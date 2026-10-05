# Prompt framework for a figure series

Use this framework only after extracting architecture facts from the available sources. Replace bracketed fields; remove lines that do not apply. It is a structure for a user-facing prompt, not an ESOL-specific template.

```text
@创建图像

Create [N] original scientific architecture illustrations for [project or paper]. Generate Figure [first] through Figure [last] from scratch. [If the user supplied a reference image: use the attached image only for specified style properties; do not copy its architecture.] No reference image is required when none is attached.

Deliver [N] separate images, one complete architecture per image, in figure-number order. Each uses a [aspect ratio] canvas. Do not combine architectures into a collage or contact sheet. Begin image generation; do not answer with only a plan.

[For a complex project series, make Figure 1 an end-to-end overview unless the user requests otherwise. Show data inputs, conditioning, shared model core, training-only supervision, inference/sampling, and final output. Separate training and inference visually. Follow with focused figures that reveal mechanisms too detailed for the overview. Choose the actual number and scope from the verified implementation; do not automatically use three figures.]

Shared visual contract:
- Purpose and audience: [e.g., journal article for machine-learning researchers].
- Background, camera angle, line treatment and whitespace: [specific, consistent choices].
- Palette: [color → meaning; keep the same meaning in every image].
- Typography: [font family or style, minimum readable size, horizontal labels].
- Data flow and arrows: [direction and restrained connector style].
- Reveal internal mechanisms rather than drawing generic boxes. Use only a few exact labels. No invented layers, outputs or results.

Figure [i] — “[exact title]”
Input and verified example: [representation; parsed tokens or shape if shown].
Ordered computation: [branches, stages, counts, dimensions, merge points, pooling and output].
Visual focus: [specific mechanism to depict internally].
Critical distinctions: [what separates this model from nearby figures].
Exact labels: [short list; specify spelling and capitalization].
Exclude: [only plausible but incorrect mechanisms or unsupported claims].

[Repeat the figure specification for every requested image.]

Before completing each image, check its input parsing, ordered layers, masks, pooling and output against its specification. For a complex series, also verify that the overview connects the complete project path and that focused figures explain distinct internal mechanisms without contradicting it. Preserve the shared visual contract across the series. After generation, list only the figures actually completed. If the session cannot produce all [N] independent images in one response, do not substitute a collage or claim completion; state the remaining figure numbers.
```

## Architecture inventory hints

Use only the checks relevant to the model family:

| Family | Detail that commonly changes the drawing |
| --- | --- |
| RNN, LSTM, GRU | Cell type, directionality, number of stages, returned sequence versus terminal state, gate or memory mechanism |
| Attention pooling | Source of per-position states, scoring and weighting, padding mask, weighted aggregation |
| Transformer | Encoder versus decoder, layer count, head count, position information, masks, residual paths, pooling |
| Multimodal or descriptor fusion | Independent inputs, preprocessing, learned projections, exact merge point |
| Pretrained model | Tokenizer, checkpoint identity if verified, encoder/readout, fine-tuned versus frozen state if known |
| Tuned model | Candidate configurations, validation criterion, selection boundary, test evaluation after selection |

If the image must contain many precise labels, recommend a final visual inspection of the generated result: image generators may misspell text or misdraw repeated structures. The verified source remains the authority if the image differs from it.

