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

L1, the first-token-conditioned continuation baseline, succeeded on 14/14 held-out pairs. M, the activation-side alignment metric, was positive on 9/14 pairs.

For M, the matched mean alignment was +0.0420 compared with a 500-sample Monte Carlo permutation null mean of -0.0021, with empirical p ≈ 0.002.

The main takeaway is not that activations do not matter, or that multi-token J-Lens fails. The result suggests a real activation-side structural signal alongside a substantially more consistent continuation signal.

## Project Files

The notebooks, executive summary, figures, and supporting results will be added here.
