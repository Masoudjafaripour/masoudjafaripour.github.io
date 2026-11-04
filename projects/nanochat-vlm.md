---
layout: project
title: nanochat-VLM
project: nanochat-VLM
permalink: /projects/nanochat-vlm/
description: nanochat-VLM, a minimal vision-language model trained end-to-end in the spirit of Karpathy's nanochat.
---

**nanochat-VLM** extends Andrej Karpathy's [nanochat](https://github.com/karpathy/nanochat) toward multimodality: a small but complete **vision-language model (VLM)**, trained end-to-end with the same philosophy of minimal code, full ownership, and clear learning value. The main goal is to train the whole pipeline with nanochat-style scripts (tokenizer, then language model, then multimodal training), not just to demo inference. It is built for learning, research, and hackability rather than scale.

### How it works

<div class="method-demo">
<iframe id="vlm-demo" src="{{ '/assets/demos/nanochat-vlm/index.html?embed' | relative_url }}" title="nanochat-VLM method animation" loading="lazy" style="width:100%;height:820px;border:0;border-radius:16px;display:block"></iframe>
</div>
<script>
  // The demo posts its content height so the frame fits it without a scrollbar.
  addEventListener("message", function (e) {
    var frame = document.getElementById("vlm-demo");
    if (frame && e.source === frame.contentWindow && e.data && e.data.type === "method-demo:height") {
      frame.style.height = e.data.height + "px";
    }
  });
</script>

### Goals

- Rebuild the core nanochat LLM pipeline: tokenization, transformer, and training.
- Extend it to a VLM with a vision encoder and multimodal fusion.
- Train script-first, nanochat-style, rather than notebook-first.
- Keep the system transparent, minimal, and easy to modify.
- Make experiments possible on limited compute, from a single GPU to a small server.

### Pipeline

1. **Tokenizer.** A byte-level BPE tokenizer trained with `rustbpe`, a small Rust routine, and exported to `tiktoken` for fast inference. Special tokens such as `<|image|>` are reserved up front so the same vocabulary can later carry image placeholders.
2. **Base language model.** A GPT-style decoder-only transformer with rotary embeddings, QK-norm, untied embeddings, ReLU² MLPs, RMSNorm, and multi-query attention. It is optimized with Muon for hidden matrices and AdamW for embeddings, on data streamed from FineWeb-Edu, and scales with a single `depth` knob from a tiny CPU model to multi-GPU runs with PyTorch DDP.
3. **Vision-to-language bridge.** A pretrained vision encoder (CLIP, ViT, or DINO) produces patch embeddings, and a projector maps them into the language model's embedding space. Image tokens are prepended to the text sequence with a matching attention mask, so the model attends over both modalities jointly.
4. **Training stages.** Tokenizer training, then base pretraining, then vision-projector alignment, multimodal fusion training, and chat SFT with evaluation.

### Learning notebooks

Six notebooks walk through each VLM component in isolation before it is promoted into the training scripts:

1. Vision tokenization and patch embeddings
2. Projecting vision embeddings into the LM embedding space
3. Fusing image and text tokens, with attention masks
4. A full multimodal forward pass
5. A first training step that trains only the projector
6. Multimodal generation and qualitative evaluation

### Status

The text pipeline (tokenizer training, base pretraining, and CORE benchmark evaluation) runs from the repository's scripts. The vision stages, from encoder integration through multimodal training and chat, are being prototyped in the notebooks and have not yet been promoted to the main training scripts. Setup and run commands are in the [repository README](https://github.com/Masoudjafaripour/nanochat-VLM#readme).
