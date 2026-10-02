# THESEUS

## Theseus in the Graph: Towards Traceable Multi-Hop Graph Navigation

**THESEUS** is a framework for studying multi-hop Knowledge Graph Question Answering (KGQA) as **question-conditioned graph navigation**.

Rather than evaluating only whether a model reaches the correct answer, THESEUS makes the reasoning process explicit: given a **natural-language question**, a **starting entity**, and a **knowledge graph**, an agent must navigate the graph hop by hop to reach a valid answer.

This formulation enables evaluation of both:

- **Answer correctness** — did the agent reach the correct answer?
- **Path fidelity** — did it follow the reasoning trajectory supported by the question?

![Theseus in the Graph: Multi-Hop KG Navigation](agent_navigation.gif)

The resulting trajectories expose the sequence of **entities and relations** used during reasoning, making it possible to distinguish successful navigation from cases where a model arrives at the correct answer through an incorrect or unintended path.

> **Anonymous artifact repository for the manuscript under review.**

---

## Resources

This repository serves as the central anonymous index for the datasets, adapted model implementations, pretrained checkpoints, and evaluation resources associated with the submission.

### Datasets

| Dataset | Description | Resource |
| --- | --- | --- |
| **KINSHIP** | Small controlled navigation-ready KGQA benchmark with 1–3 hop questions, annotated reference reasoning paths, and controlled paraphrases | [Anonymous dataset](https://www.kaggle.com/datasets/anonymousexpert/kinship) |
| **MQuAKE-ST** | Large static navigation-ready variant of MQuAKE with 1–4 hop questions, a fixed Wikidata-derived graph, verified relation-chain templates, paraphrases, and single- and multi-answer settings | [Anonymous dataset](https://www.kaggle.com/datasets/anonymousexpert/mquake-st) |

The released datasets use explicit topic entities and materialized knowledge graphs so that both terminal-answer quality and executed graph trajectories can be evaluated under a reproducible navigation setting.

---

### Adapted Navigation Models

| Model | Navigation paradigm | Anonymous implementation |
| --- | --- | --- |
| **MINERVA** | Reinforcement-learning graph navigation | [Repository](https://anonymous.4open.science/r/MINERVA-EF54/) |
| **MultiHopKG** | Reinforcement-learning graph navigation adapted from MultiHopKG | [Repository](https://anonymous.4open.science/r/MultiHopKG-352D/) |
| **SQUIRE** | Sequence-to-sequence path generation | [Repository](https://anonymous.4open.science/r/Anonymous-Repo-3222/) |

These repositories contain the anonymized implementations used for the experiments reported in the submission.

---

### Pretrained Checkpoints and Evaluation Artifacts

Pretrained checkpoints corresponding to the reported experiments are available through the anonymous artifact archives below.

Each archive contains the released model artifacts and associated experimental resources.

| Model | Resource |
| --- | --- |
| **MINERVA** | [Pretrained checkpoints](https://www.kaggle.com/models/anonymousexpert/minerva-kgqa) |
| **MultiHopKG** | [Pretrained checkpoints](https://www.kaggle.com/models/anonymousexpert/multihop-kgqa) |
| **SQUIRE** | [Model artifacts](https://www.kaggle.com/datasets/anonymousrepo1729/kgqa-models) · [Dataset artifacts](https://www.kaggle.com/datasets/anonymousrepo1729/kgqa-datasets) |

---

## What is THESEUS?

Traditional multi-hop KGQA evaluation primarily asks whether a system predicts the correct answer. THESEUS instead treats reasoning as an explicit navigation problem:

```text
Natural-language question
          +
     Topic entity
          +
    Knowledge graph
          |
          v
 Question-conditioned
   navigation policy
          |
          v
e0 --r1--> e1 --r2--> ... --rn--> answer
          |
          v
Answer correctness + Path traceability
```

THESEUS evaluates both:

- **Answer ranking:** MRR and Hits@1
- **Path traceability:** PED, RED, F1_SG, and F1_Rel

The adapted models replace their original symbolic query interfaces with natural-language question conditioning while preserving their underlying navigation architectures.

The reasoning horizon is separated from the underlying question hop length, allowing questions of different depths to be evaluated under a common traversal budget.

---

## Dataset Summary

| Dataset | Entities | Relations | Triples | QA setting | Hop lengths | Reference paths |
| --- | ---: | ---: | ---: | --- | :---: | :---: |
| **KINSHIP** | 24 | 12 | 112 | Single-answer | 1–3 | Yes |
| **MQuAKE-ST** | 38,516 | 665 | 724,141 | Single- and multi-answer | 1–4 | Yes |
| **MetaQA** | 43,234 | 9 | 134,741 | Multi-answer | 1–3 | No |

For **KINSHIP** and **MQuAKE-ST**, 1-hop questions are reserved for training in the mixed-hop setting.

These releases include explicit reference reasoning paths, enabling evaluation of both terminal-answer correctness and executed trajectory fidelity.

**MetaQA** provides question-answer supervision but does not include reference reasoning paths.

---

## Artifact Organization

The anonymous resources are organized as follows:

```text
THESEUS
├── Datasets
│   ├── KINSHIP
│   └── MQuAKE-ST
├── Implementations
│   ├── MINERVA
│   ├── MultiHopKG
│   └── SQUIRE
└── Pretrained checkpoints and evaluation artifacts
    ├── MINERVA
    ├── MultiHopKG
    └── SQUIRE
```

The individual repositories and artifact archives contain the implementation-specific instructions and resources required to reproduce the corresponding experiments.

