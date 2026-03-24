# Protein Language Models for AI4Health

This module is designed as a course unit for `AI for Health`. It treats protein language models as a bridge between modern AI, structural biology, and translational applications such as variant interpretation, therapeutic design, and biomolecular engineering.

## Recommended Topic Sequence

1. Proteins as a language
   Why amino-acid sequences can be modeled with token-based self-supervision, and why unlabeled sequence scale matters.

2. Foundational protein language models
   `ProtBERT`, `ProtT5`, `ESM-1/2`, and the idea of pretrained embeddings for downstream tasks.

3. What protein language models learn
   Emergent signals for secondary structure, tertiary contacts, remote homology, and mutation effects.

4. Structure prediction and where AlphaFold fits
   `AlphaFold2` as the landmark structure model, `ESMFold` as the single-sequence pLM-based alternative, and `AlphaFold3` for biomolecular interactions.

5. Generative protein models
   `ProtGPT2` for sequence generation, `ProteinMPNN` for inverse folding and structure-conditioned sequence design, `RFdiffusion` for structure generation, and `ESM3` for multimodal generation over sequence, structure, and function.

6. AI-for-health applications
   Missense variant interpretation, antibody and binder design, enzyme engineering, pathogen proteins, and design workflows that combine pLMs with structure prediction.

7. Limitations, evaluation, and safety
   Benchmark leakage, confidence calibration, wet-lab validation, dual-use concerns, and the difference between plausible structure and useful function.

## Recommended Teaching Format

- `1 x 90 min lecture`
  Cover sections 1-5, with AI-for-health applications woven throughout.

- `2 x 75 min lectures`
  Lecture 1: representations, structure, AlphaFold vs ESMFold.
  Lecture 2: generative models, design workflows, healthcare use cases, limits.

- `+ optional 45-60 min lab`
  Use an AlphaFold Database case study or a simple embedding/fine-tuning demo.

## Learning Objectives

By the end of the module, students should be able to:

- explain why protein sequences are suitable for self-supervised language modeling
- distinguish representation models, structure predictors, and generative design models
- compare `AlphaFold2`, `ESMFold`, and `AlphaFold3` at a high level
- describe how protein language models support mutation-effect prediction and protein engineering
- identify major evaluation pitfalls and why wet-lab validation is still necessary

## Suggested Emphasis for AI4Health

If you want a health-centered version rather than a pure protein-design lecture, I recommend this emphasis:

1. Start from disease variants and protein dysfunction.
2. Introduce pLMs as a scalable way to learn from sequence alone.
3. Compare embeddings, structure prediction, and generation as three different uses of foundation models.
4. End with translational examples:
   missense effect prediction, therapeutic binders, antibodies, enzymes, and model safety.

## Canonical Models To Cover

- `ProtTrans`
  Good for introducing scale, transfer learning, and the hardware cost of training protein LMs.

- `ESM-1/2`
  Good for showing how structure and function emerge from unsupervised sequence modeling.

- `AlphaFold2`
  Essential comparison point. It is not usually framed as a protein language model, but students need it for context.

- `ESMFold`
  Best bridge between pLMs and structure prediction from a single sequence.

- `AlphaFold3`
  Important extension from single-protein structure to biomolecular interactions.

- `ProtGPT2`
  Clean example of sequence generation.

- `ProteinMPNN`
  Strong example of structure-conditioned sequence design.

- `RFdiffusion`
  Core example of generative structure design.

- `ESM3`
  Current flagship example of multimodal protein generation.

## Files In This Module

- [slides.md](/Users/hqin/github/AI4Health/lectures/protein_language_models/slides.md)
  Slide-ready lecture outline with speaker notes and visual suggestions.

- [resources.md](/Users/hqin/github/AI4Health/lectures/protein_language_models/resources.md)
  Primary papers, borrowable open teaching materials, reusable figure sources, and assignment ideas.

## Short Recommendation

For this course, I would teach the module under this title:

`Protein Language Models: From Sequence Representation to Structure Prediction and Generative Design`

That title is broad enough to naturally include `AlphaFold`, `protein generative models`, and AI-for-health applications without confusing students about what counts as a language model versus a structure model.
