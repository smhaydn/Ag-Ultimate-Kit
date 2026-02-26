---
description: Build, debug, and theorize advanced ComfyUI workflows without missing nodes or breaking pipelines.
---

# ComfyUI Build Workflow (`/comfy-build`)

**Trigger words**: `/comfy-build`, "Design a ComfyUI workflow", "ComfyUI pipeline", "Fix my ComfyUI nodes"

## 1. Requirement & Architecture Check

Before writing any JSON or node arrays, act as a **ComfyUI Architect**.

1. Ask the user for their exact goal (e.g., "Photorealistic portrait", "Animate a logo", "Face swap a character").
2. Ask about the target model (SD 1.5, SDXL, Flux.1, SD3). _This is critical as Latent sizes, text encoders (CLIP L/G, T5), and ControlNet models are completely different between them._

## 2. Conceptual Pipeline Proposal

Write out a text-based visual map of the pipeline. Example:

```text
[Load Checkpoint (SDXL)] --> [CLIP Text Encode (Prompts)]
                                     |
[Load Image] -> [IPAdapter Plus] ----+---> [KSampler] ---> [VAE Decode] ---> [Face Detailer] ---> [Save Image]
```

Present this to the user. Ask: _"Is this pipeline logic what your machine can handle, and does it align with your idea?"_

## 3. Dependency Inventory

List the custom nodes required for this pipeline to work. Warn the user to install them via ComfyUI Manager.

- _ControlNet Auxiliary Preprocessors_
- _ComfyUI-Impact-Pack_ (for Face Detailer)
- _rgthree-comfy_ (for mute/bypass nodes and fast rerouting)

## 4. JSON Generation (Only upon approval)

Once the user approves the pipeline:

1. Generate the ComfyUI API-format JSON.
2. VERIFY the connection links: Every `[node_id, port_index]` must point to a valid existing Node ID and the correct output port type (e.g., IMAGE to IMAGE, LATENT to LATENT, CONDITIONING to CONDITIONING).
3. Ensure seed parameters are set to `randomize` or a variable if requested.

## 5. Post-Generation Review

Remind the user to drag and drop the JSON into their browser and report back any "Red Node" (missing node) errors so you can debug the exact custom node repository to fix it.
