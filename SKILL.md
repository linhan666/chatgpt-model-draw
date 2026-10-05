---
name: model-architecture-image-prompts
description: Turn verified machine-learning model implementations or specifications into scientifically accurate, visually coherent prompts for ChatGPT web image generation. Use for one architecture figure or a consistent series; do not use for generic image requests unrelated to model architecture.
---

# Model architecture image prompts

Create a paste-ready request for ChatGPT web image generation. The outcome is an architecture illustration that reveals how the model works while remaining faithful to the available evidence. The user may request one image or a series, and may supply code, a paper, an existing figure, or a verbal description.

## Establish the architecture

1. Read the source the user provides. For a codebase, inspect the model builder, tokenizer or preprocessing, forward pass, configuration, and checkpoint loading where relevant. A prior diagram or report may help locate facts but does not override implementation. If sources disagree, surface the conflict before specifying the disputed detail.
2. Make a compact internal inventory for each figure: input representation and example, branches and merge points, ordered layers and counts, dimensions that matter, outputs, masks and pooling, pretrained versus scratch components, and the single mechanism that should be visually prominent. Distinguish operations used only during training or model selection from the inference path.
3. Use a concrete example only after checking its parsing or shape. For instance, character and chemistry-token views of the same string can differ. Do not infer missing widths, checkpoint identities, gate types, winners, or scores. Omit nonessential unknowns; ask a focused question only when an unknown blocks an accurate figure.

## Plan figure coverage

- Decide the number and scope of figures from the verified architecture and the user's request; no fixed three-part split is prescribed. For a complex project with distinct data preparation, learned model, training, and inference paths, include an end-to-end overview figure before focused mechanism figures unless the user explicitly requests a narrower set. The overview should connect the real inputs, conditioning, model core, training-only supervision, sampling, and final output while visibly distinguishing training from inference.
- Make focused figures complementary to the overview. Give each one enough space to expose a mechanism that would be too small in the overview, such as a Transformer layer, a transport or alignment objective, or iterative sampling. Do not repeat the same generic boxes across figures.
- Check coverage across the series: a reader should understand the complete project from the overview and use the focused figures to inspect its important internal computations. Do not force unrelated models into one overview merely because the user requested a series.

## Translate computation into a visual

- Choose a form that makes the distinctive operation recognizable: recurrent memory and gates; aligned token states and masked weights; separate feature branches and fusion; attention heads, residual paths and feed-forward sublayers; or pretrained encoder and readout. These are examples, not modules to add to every model.
- Preserve data direction and exact layer order. Depict repeated blocks as the actual number of stages. Make masks, aggregation, and selection paths explicit when they change the meaning of the architecture.
- Keep short, exact labels for scientific terms, layer sizes, and outputs. Reduce image text instead of adding explanatory paragraphs. Do not ask the generator to invent omitted details.
- For a series, define one style contract before the figure specifications: canvas/aspect ratio, perspective, palette with stable semantic roles, typography, margins, arrow treatment, and label size. Describe a different visual focus for each figure while preserving that contract. An approved image can be an optional style reference; never make one mandatory unless the user supplied it.
- In an end-to-end overview, use visually bounded training and inference routes that share the same model core. Show the real order and role of major components, but reserve fine internal gates, heads, losses, or loop details for focused figures. A project overview must still reveal meaningful computation; it is not a generic pipeline of labeled boxes.
- Prefer an illustration of internal structure over a generic row of labeled boxes. Avoid decoration that suggests a different model family or mechanism.

## Build the web prompt

Use [references/prompt-framework.md](references/prompt-framework.md) when assembling a multi-figure, single-message request or when a reusable prompt skeleton would help. Adapt its fields to the verified architecture; remove irrelevant fields and examples. For a single figure, a shorter direct prompt is usually better.

If the user wants one paste into ChatGPT web, provide one self-contained prompt covering all figures. Explicitly request separate images, one model per canvas, and prohibit a collage when independent figures are required. Do not require an uploaded first figure merely to establish a common style. State exact titles and labels where typography matters. In the prompt, ask the image generator to begin rather than reply with a plan, and to report which figures were actually produced if the session cannot finish the batch.

Do not promise that one ChatGPT web message will yield every requested independent image. The prompt can request a batch, but product and usage limits govern delivery. If the user asks for a reliable automated batch, explain the limitation and offer an API or other programmatic workflow as an option without replacing the requested web prompt.

## Check the deliverable

Before handing over the prompt, compare each figure specification with the inventory: tokenization, layer count and order, hidden-state versus pooled outputs, mask placement, feature fusion, pretrained status, output head, and whether any training or selection step is mistaken for inference. For a complex series, check that the overview covers the complete project path and the focused figures explain its distinctive mechanisms. Check that figure numbering is complete, style rules do not conflict with model-specific instructions, and the request does not accidentally depend on an absent attachment.

Return the paste-ready prompt prominently. Add only a brief practical note for a material limitation or unresolved architecture fact.

