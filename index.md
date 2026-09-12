# Finish My Sentence

**A Controlled Pilot Separating Activation-Derived Structure from First-Token-Conditioned Continuation in Multi-Token J-Lens**

## Research Question

When a multi-token readout recovers a phrase, how much of that information is actually recoverable from the hidden-state activation, and how much is supplied by the model's continuation prior once the first token is known?

## Setup

- Model: Qwen/Qwen3.5-4B
- 15 controlled structural minimal pairs
- 1 pilot pair
- 14 held-out pairs
- Open-source J-Lens implementation
- Lightweight activation-side alignment metric

## Main Result

Both signals were present, but continuation was much more consistent.

- L1 moved in the expected direction on 14/14 held-out pairs.
- M was positive on 9/14 pairs.
- M's matched mean alignment was +0.0420 compared with a permutation-null mean of -0.0021.
- Empirical one-sided p-value for the matched M mean was about 0.002.
- There were 5 L1-only cases and no M-only cases.

## What I Tested

### L1: First-token-conditioned continuation

L1 asks how much of the multi-token distinction the frozen language model can recover through ordinary continuation once the correct first token is supplied.

### M: Activation-side structural alignment

M does not generate a phrase. It tests whether reversing the relation in the source produces an activation-space change aligned with the difference between the two candidate concepts.

## Dataset

The 15 minimal pairs cover five relation types:

- role / argument binding
- modifier attachment
- spatial relation
- comparative relation
- quantifier binding

Pair 1 was used for pilot development. All measurement choices were then frozen before evaluating Pairs 2-15.

## Controls

For L1, I used mismatched-source and permutation controls.

For M, I used a 500-sample Monte Carlo permutation test that repeatedly broke the correct correspondence between source-difference and candidate-difference vectors.

Both controls showed that the matched results depended strongly on the correct structural correspondence.

## Category Pattern

M was consistently positive for:

- role / argument binding
- modifier attachment
- spatial relation

Comparative relations were negative on all three pairs, while quantifier binding showed a mixed pattern.

A post-hoc diagonal-whitening check softened the comparative failure but did not remove it.

## Interpretation

The experiment does not show that activation-side structure is absent.

Instead, it shows that the lightweight M metric detects pair-specific activation-side structure, while first-token-conditioned continuation tracks the tested distinctions substantially more consistently.

A correct multi-token verbalization therefore does not by itself establish that the entire phrase was directly recovered from the hidden state.

## Notebooks

1. `00_setup_check.ipynb`
2. `01_reproduce_jlens.ipynb`
3. `02_dataset_design.ipynb`
4. `03_core_experiment.ipynb`
5. `04_analysis_figures.ipynb`
6. `05_interpretation_limitations.ipynb`

## Limitations

This is a small controlled pilot on one model. M is a lightweight structural alignment metric rather than a fully calibrated multi-token J-Lens readout, and the experiment does not provide an additive decomposition of activation versus continuation.

## Repository

Full code, notebooks, outputs, and analysis are available in the GitHub repository.
