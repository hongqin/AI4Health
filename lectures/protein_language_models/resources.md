# Resources, Sources, and Borrowable Materials

This file separates `what to teach` from `what you can safely borrow or adapt`.

## Primary Papers and Official Sources

### Protein LM foundations

- `Rives et al., 2021`
  `Biological structure and function emerge from scaling unsupervised learning to 250 million protein sequences`
  Link: https://pmc.ncbi.nlm.nih.gov/articles/PMC8053943/
  Why it matters: canonical evidence that unsupervised protein LMs learn structure- and function-related signals.

- `ProtTrans, 2021`
  ORNL summary page: https://www.ornl.gov/publication/prottrans-towards-cracking-language-lifes-code-through-self-supervised-deep-learning
  Why it matters: strong citation for scale, transfer learning, and compute requirements.

- `Meier et al., 2021`
  `Language models enable zero-shot prediction of the effects of mutations on protein function`
  Link: https://proceedings.neurips.cc/paper/2021/hash/f51338d736f95dd42427296047067694-Abstract.html
  Why it matters: best short citation for health-relevant variant-effect prediction.

### Structure prediction

- `Jumper et al., 2021`
  `Highly accurate protein structure prediction with AlphaFold`
  Link: https://www.nature.com/articles/s41586-021-03819-2
  Why it matters: landmark AlphaFold2 paper. Open access and reusable figures under CC BY 4.0 unless otherwise noted.

- `ESM / ESMFold summary`
  Link: https://huggingface.co/docs/transformers/model_doc/esm
  Why it matters: compact teaching summary of `ESM-2` and `ESMFold`, including the single-sequence framing and speed comparison.

- `Abramson et al., 2024`
  `Accurate structure prediction of biomolecular interactions with AlphaFold 3`
  Link: https://www.nature.com/articles/s41586-024-07487-w
  Why it matters: best primary source for AlphaFold3 in a current lecture. Open access and reusable figures under CC BY 4.0 unless otherwise noted.

### Generative protein models

- `ProtGPT2, 2022`
  Link: https://www.nature.com/articles/s41467-022-32007-7
  Why it matters: clean sequence-generation paper. Open access and reusable figures under CC BY 4.0 unless otherwise noted.

- `ProteinMPNN, 2022`
  Link: https://pubmed.ncbi.nlm.nih.gov/36108050/
  Why it matters: canonical inverse-folding design paper and strong bridge from structure to sequence.

- `RFdiffusion, 2023`
  Link: https://www.nature.com/articles/s41586-023-06415-8
  Why it matters: core diffusion-based protein design paper. Open access and reusable figures under CC BY 4.0 unless otherwise noted.

- `EvolutionaryScale ESM repository`
  Link: https://github.com/evolutionaryscale/esm
  Why it matters: official current entry point for `ESM3`, `ESM C`, model family descriptions, and access patterns.

- `Hayes et al., 2025`
  `Simulating 500 million years of evolution with a language model`
  Link: https://pubmed.ncbi.nlm.nih.gov/39818825/
  Why it matters: primary citation for `ESM3` as a multimodal generative model.

## Borrowable Open Teaching Materials

### EMBL-EBI AlphaFold course slides

- Link: https://www.ebi.ac.uk/training/online/courses/alphafold/course-slides/
- Why use it:
  polished teaching slides with AlphaFold2, confidence scores, AlphaFold3, and practical interpretation.
- License:
  `CC BY 4.0`
- Safe use:
  download, adapt, and merge selected AlphaFold slides into your lecture with attribution.

### Galaxy Training Network protein language model slides

- Link: https://training.galaxyproject.org/training-material/topics/statistics/tutorials/fine_tuning_protTrans/slides-plain.html
- Why use it:
  good introductory slides for `ProtTrans`, pLM basics, fine-tuning, and teaching-level visuals.
- License:
  `CC BY 4.0`
- Safe use:
  borrow the introductory pLM slides and the fine-tuning framing for an optional lab or methods section.

## Reusable Figure Sources

These are the safest sources for direct figure reuse in your own slides.

- `AlphaFold Nature 2021`
  Link: https://www.nature.com/articles/s41586-021-03819-2
  Note: open access under `CC BY 4.0`.

- `AlphaFold 3 Nature 2024`
  Link: https://www.nature.com/articles/s41586-024-07487-w
  Note: open access under `CC BY 4.0`.

- `ProtGPT2 Nature Communications 2022`
  Link: https://www.nature.com/articles/s41467-022-32007-7
  Note: open access under `CC BY 4.0`.

- `RFdiffusion Nature 2023`
  Link: https://www.nature.com/articles/s41586-023-06415-8
  Note: open access under `CC BY 4.0`.

## License Caution

- `ProteinMPNN` is a `Science` paper.
  Use it freely as a source for facts and discussion, but do not assume figures are reusable without checking rights.

- `ESM3` is also a `Science` paper.
  Safer options are:
  cite the paper,
  recreate a simple diagram yourself,
  or use visuals from officially licensed repositories after checking license terms.

- Even in open-access papers, third-party figures may carry separate credit lines.
  Check the figure caption before reuse.

## Good Figures To Borrow

- AlphaFold 2021:
  model overview and CASP14 performance figure.

- AlphaFold 3:
  model/task figure for biomolecular interactions.

- ProtGPT2:
  protein-space exploration or generated-sequence characterization figure.

- RFdiffusion:
  design workflow or conditional generation figure.

## Suggested Live Demos

### Demo 1. AlphaFold Database walkthrough

- Show how to inspect a predicted structure.
- Explain `pLDDT` and `PAE`.
- Connect confidence to responsible use.

### Demo 2. Hugging Face ESM page

- Show what pretrained protein models look like in practice.
- Explain embeddings vs full prediction vs generation.

### Demo 3. Simple case-study discussion

- Pick a disease gene or therapeutic target.
- Ask which tool family you would use first:
  pLM embeddings, AlphaFold, ProteinMPNN, or RFdiffusion.

## Suggested Assignments

### Assignment 1. Model comparison memo

- Compare `AlphaFold2`, `ESMFold`, and `ProteinMPNN`.
- Focus on input, output, supervision, and biomedical use case.

### Assignment 2. Critique a generative paper

- Read `ProtGPT2`, `RFdiffusion`, or `ESM3`.
- Ask whether evaluation demonstrates novelty, function, and practical utility.

### Assignment 3. Health-focused design proposal

- Choose a protein relevant to disease.
- Propose a workflow using a protein LM plus a structure or generation model.
- State what experimental validation would still be required.

## Practical Teaching Recommendation

If you want the cleanest lecture flow with minimal slide-building effort:

1. Use your own title, motivation, and summary slides.
2. Borrow 3-4 AlphaFold slides from EMBL-EBI.
3. Borrow 2-3 introductory pLM slides from Galaxy.
4. Add your own comparison slides on `ProtGPT2`, `ProteinMPNN`, `RFdiffusion`, and `ESM3`.
5. Finish with health applications and limitations.
