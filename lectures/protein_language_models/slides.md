# Slide Deck Outline

## Slide 1. Title

`Protein Language Models for AI4Health`

- From sequence representation to structure prediction and generative design
- Suggested subtitle: `What do protein foundation models learn, and how can we use them in health?`

Suggested visual:
- Simple three-panel diagram you create locally: `sequence -> structure -> function`

## Slide 2. Why This Matters

- Proteins drive nearly every biological process.
- Sequence databases are enormous; experimentally solved structures and functional labels are limited.
- AI can learn from raw sequence scale before we have task-specific labels.

Speaker note:
- Frame this as the biological version of the foundation-model story: lots of unlabeled data, limited labeled data, strong transfer value.

## Slide 3. Proteins as a Language

- Alphabet: 20 standard amino acids plus special tokens in some models.
- Grammar: local motifs, long-range residue dependencies, domain organization, evolutionary constraints.
- Semantics: fold, stability, binding, catalysis, localization, fitness.

Suggested prompt to class:
- If English tokens compose sentences, what is the protein analogue of syntax and meaning?

## Slide 4. Why Self-Supervision Works Here

- Labels are scarce.
- Natural sequences already encode evolutionary information.
- Language-model objectives force models to predict plausible residues from context.

Key citation:
- `Rives et al., 2021` showed that scaling to `250 million` protein sequences led to representations containing structure and function signals.

Suggested visual:
- Borrow a high-level pLM architecture figure from the Galaxy ProtTrans slides if you want a quick, reusable intro visual.

## Slide 5. Historical Arc

- Early representation learning: sequence embeddings and task-specific models.
- Foundation-scale protein LMs: `ProtTrans`, `ESM`.
- Structure breakthroughs: `AlphaFold2`, `ESMFold`, `AlphaFold3`.
- Generative design: `ProtGPT2`, `ProteinMPNN`, `RFdiffusion`, `ESM3`.

Speaker note:
- This slide helps students organize the field before diving into model details.

## Slide 6. ProtTrans

- Trained multiple transformer families on large protein corpora.
- Useful to introduce scale, transfer learning, and compute requirements.
- Good classroom message: we usually do not train these from scratch in a university lab; we fine-tune or embed.

Teaching point:
- ORNL reports ProtTrans models trained on up to `393 billion amino acids`, using `5616 GPUs` and up to `1024 TPU cores`.

Suggested visual:
- Borrow 1-2 introductory slides from the Galaxy `Fine-tuning Protein Language Model` deck.

## Slide 7. What Embeddings Learn

- Remote homology
- Secondary structure
- Contact information
- Mutation effects

Key citation:
- `Rives et al., 2021` found that secondary and tertiary structure information is encoded in learned representations and can be exposed by linear projections.

Speaker note:
- This is the conceptual heart of the lecture: students should leave understanding that raw sequence pretraining can create biologically meaningful latent spaces.

## Slide 8. Variant Effect Prediction

- Why it matters for health:
  missense variants, pathogenicity triage, protein dysfunction, precision medicine.
- pLMs can estimate mutation effects without task-specific retraining in some settings.

Key citation:
- `Meier et al., NeurIPS 2021` showed zero-shot prediction of mutation effects from protein language models.

Discussion prompt:
- Why might sequence-only pretraining help predict whether a mutation is harmful?

## Slide 9. ESM Family

- `ESM-1` and `ESM-2` are core sequence representation models.
- `ESM-2` is a strong example of scale leading to better structure-aware representations.
- Hugging Face documentation summarizes the `ESM-2` and `ESMFold` transition clearly for teaching.

Teaching point:
- The strongest classroom takeaway is not the exact parameter count.
- It is that larger pLMs can recover richer structural information from single sequences.

## Slide 10. ESMFold

- Predicts structure directly from a single sequence using pLM embeddings.
- Avoids the full `MSA + template` pipeline used by AlphaFold2.
- A useful classroom contrast with AlphaFold2.

Key claim to teach:
- The ESMFold paper summary reports `similar accuracy to AlphaFold2 and RoseTTAFold for sequences with low perplexity` and `an order of magnitude faster inference than AlphaFold2`.

Speaker note:
- Emphasize that this does not mean ESMFold universally replaces AlphaFold2.
- It means pLMs made single-sequence structure prediction much more practical.

## Slide 11. AlphaFold2

- Landmark structure prediction system from DeepMind.
- Uses biological and physical inductive bias plus `multiple sequence alignments`.
- CASP14 performance was competitive with experimental structures for many targets.

Important clarification:
- `AlphaFold2` is usually taught here as a comparison model, not as a pure protein language model.

Suggested visual:
- Borrow a figure from the open-access AlphaFold 2021 Nature paper.

## Slide 12. AlphaFold2: What Students Should Remember

- Sequence alone is not the whole story in AlphaFold2.
- Evolutionary information from `MSAs` is central.
- Confidence outputs such as `pLDDT` and `PAE` are critical for interpretation.

Speaker note:
- Students often over-trust a pretty 3D structure.
- This is a good place to insist on confidence interpretation and failure modes.

## Slide 13. AlphaFold3

- Extends the task from single-protein structure to `biomolecular interactions`.
- Includes proteins, nucleic acids, ligands, and complexes.
- Useful for showing how the field is moving from fold prediction toward interaction modeling.

Teaching point:
- For an AI-for-health course, AlphaFold3 matters because many biomedical questions are about interaction, not just monomer fold.

Suggested visual:
- Use the EMBL-EBI AlphaFold slide deck, which already includes AlphaFold 3 and prediction-quality slides.

## Slide 14. AlphaFold vs ESMFold vs Protein LMs

- `Protein language models` learn sequence representations by self-supervision.
- `AlphaFold2` is a structure predictor with heavy MSA use.
- `ESMFold` is the clearest bridge from pLMs to direct structure prediction.
- `AlphaFold3` extends interaction prediction and broader biomolecular reasoning.

Board-ready summary:
- `representation`
- `prediction`
- `generation`

## Slide 15. Transition to Generative Models

- Once a model can read protein space, can it also write new proteins?
- This motivates sequence generation, inverse folding, and structure diffusion.

Speaker note:
- This is the pivot from understanding proteins to designing proteins.

## Slide 16. ProtGPT2

- Autoregressive sequence generator for de novo protein design.
- Good first example of sequence generation without explicit structure conditioning.

Key facts to teach:
- `ProtGPT2` generated proteins with natural amino-acid propensities.
- The paper reports `88%` of generated sequences predicted as globular.
- The authors argue that generated sequences explore previously under-sampled regions of protein space.

Suggested visual:
- Borrow a figure from the open-access ProtGPT2 Nature Communications paper.

## Slide 17. Inverse Folding and ProteinMPNN

- Input: backbone structure.
- Output: sequence likely to fold into that structure.
- This is different from pure language modeling but extremely important in protein design workflows.

Key fact to teach:
- `ProteinMPNN` reported `52.4%` sequence recovery on native backbones versus `32.9%` for Rosetta in the Science paper abstract.

Speaker note:
- This is often the easiest way to explain structure-conditioned design to students.

## Slide 18. RFdiffusion

- Diffusion model for generating protein structures.
- Strong for motif scaffolding, binder design, and de novo backbone generation.
- Often paired with `ProteinMPNN` for sequence design after generating structure.

Teaching point:
- This is the modern design pipeline students are likely to hear about in current papers and biotech talks.

Suggested visual:
- Borrow from the open-access RFdiffusion Nature paper.

## Slide 19. ESM3

- Multimodal generative model over `sequence`, `structure`, and `function`.
- Represents a shift from single-track sequence modeling to joint biological generation.
- Good final model to present because it unifies many earlier ideas.

Key facts to teach:
- EvolutionaryScale describes `ESM3` as a multimodal generative model for proteins.
- The 2025 Science paper reports prompting ESM3 to generate fluorescent proteins far from known natural sequences.

Speaker note:
- If time is limited, use ESM3 as the capstone rather than going deep into implementation details.

## Slide 20. Design Workflow View

- Step 1: represent or pre-screen sequences with a pLM
- Step 2: predict structure with `ESMFold` or `AlphaFold`
- Step 3: generate candidates with `ProtGPT2`, `ProteinMPNN`, or `RFdiffusion`
- Step 4: score confidence, novelty, and constraints
- Step 5: experimental validation

Suggested visual:
- Draw this as a pipeline rather than borrowing a figure.

## Slide 21. AI-for-Health Use Cases

- Missense variant interpretation
- Antibody and binder design
- Enzyme engineering for diagnostics or therapeutics
- Viral and pathogen protein analysis
- Structure-guided target prioritization

Speaker note:
- Keep the message balanced: these models accelerate hypothesis generation, not clinical decision-making by themselves.

## Slide 22. Evaluation and Failure Modes

- Structure confidence is not the same as biological function.
- Generated proteins may be plausible but not expressible, stable, or useful.
- Benchmark leakage and similarity to training data remain concerns.
- Wet-lab validation is still the decision point.

Suggested discussion:
- Which metric would you trust for a therapeutic design claim: structure confidence, novelty, activity assay, or all of them together?

## Slide 23. Safety and Responsible Use

- Design models can be dual-use.
- Open models vary in license and access restrictions.
- Responsible development now appears explicitly in model repositories such as `EvolutionaryScale/esm`.

Speaker note:
- This fits naturally in an AI-for-health course and keeps the lecture current without becoming alarmist.

## Slide 24. Key Comparisons

- `ProtTrans`: large-scale transfer learning
- `ESM-2`: strong sequence representations
- `ESMFold`: single-sequence structure prediction
- `AlphaFold2`: MSA-based structure breakthrough
- `AlphaFold3`: biomolecular interaction prediction
- `ProtGPT2`: sequence generation
- `ProteinMPNN`: inverse folding
- `RFdiffusion`: structure generation
- `ESM3`: multimodal generation

## Slide 25. Take-Home Messages

- Protein language models learn biologically meaningful representations from sequence alone.
- Structure prediction and generative design are now tightly connected.
- `AlphaFold` belongs in this module as a comparison point and workflow partner.
- The frontier is moving toward multimodal and generative protein foundation models.
- Biology still needs experiments.

## Slide 26. Optional In-Class Exercise

- Give students one protein and ask:
  what would each model family contribute?
- Representation model?
- Structure model?
- Generative model?
- What evidence would still be missing before making a health claim?

## Slide 27. Suggested Homework

Option A:
- Write a `2-page` comparison of `AlphaFold2`, `ESMFold`, and `ProteinMPNN`.

Option B:
- Pick one disease-associated protein and propose a pLM-enabled analysis pipeline.

Option C:
- Read one generative paper and critique its evaluation strategy.

## Slide 28. Reading List

- `Rives et al., 2021`
- `ProtTrans, 2021`
- `Jumper et al., 2021`
- `Lin et al. / ESMFold summary`
- `ProtGPT2, 2022`
- `ProteinMPNN, 2022`
- `RFdiffusion, 2023`
- `Abramson et al., 2024`
- `Hayes et al., 2025`

## Slide 29. If You Only Have 60 Minutes

- Keep slides `1-5`
- Keep slides `7-14`
- Keep slides `16-19`
- Keep slides `21-25`
- Skip detailed implementation and focus on conceptual differences

## Slide 30. End Slide

`Protein language models changed how we read proteins.`

`Generative models are starting to change how we write them.`
