# Model Architecture Image Prompts

A Codex skill that turns verified model code or specifications into paste-ready prompts for ChatGPT web image generation. It helps produce scientifically faithful architecture illustrations, either as a single figure or as a coherent series.

## What it does

- Inspects the implementation before specifying inputs, layers, dimensions, branches, masks, outputs, and training-only operations.
- Chooses the number and scope of figures from the actual model. Complex projects can start with an end-to-end overview, followed by focused mechanism figures.
- Defines a shared visual style for a series while giving each figure a distinct computational focus.
- Produces one self-contained prompt for a single web message when a multi-image request is needed.
- Checks the prompt for invented modules, incorrect layer order, and confusion between training and inference.

## Install

Place this repository folder under your Codex skills directory, for example `~/.codex/skills/model-architecture-image-prompts/`. Keep `SKILL.md` and `references/prompt-framework.md` together.

## Use

Ask Codex to apply `model-architecture-image-prompts` to a model repository, paper, or specification. Provide a version or commit when reproducibility matters. Codex should read the relevant source before writing the image prompt.

Example request:

> Apply the model-architecture-image-prompts skill to this repository and give me one prompt I can paste into ChatGPT web to generate a consistent series of architecture figures.

The skill generates prompts; it does not itself guarantee that a single ChatGPT web response will produce every requested image. Verify all image labels and repeated structures against the source implementation before publication.

## Files

- `SKILL.md` — the Codex skill instructions.
- `references/prompt-framework.md` — an adaptable prompt framework for figure series.

