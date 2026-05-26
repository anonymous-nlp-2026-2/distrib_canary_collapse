# Characterizing the Detectability Landscape of Iterative Model Collapse

Code and data for anonymous EMNLP 2026 ARR submission.

## Abstract

As machine-generated text proliferates online, language models increasingly risk training on their own output, creating a feedback loop driving iterative model collapse that erodes diversity and calibration across generations. While collapse dynamics are increasingly understood, *detecting* onset remains open: iterative training yields short, noisy time series (T<15) resisting early-warning diagnostics, collapse is a first-order transition precluding critical-slowing-down signals, and no prior work systematically compares detection methods on this problem. We map the *detectability landscape* (how detection varies across contamination levels, observation windows, and statistical methods) on five model families (345M--6.9B). A steep onset emerges: permutation Granger testing finds zero significant canary-to-downstream pairs through 45% contamination, then jumps to reliable detection (6/8 pairs; 95% CI [0.25, 0.92]) within two percentage points, defining blind, onset, and detection regimes. Across five methods, null-control false-positive rates span 7%--94%, revealing that method choice alone determines whether collapse appears detectable. Token entropy precedes diversity decline by at least 1 generation, enabling proof-of-concept intervention reducing peak perplexity by 64%.

## Structure

- `docs/paper/` — Paper source (LaTeX), figures, and compiled PDF
- `scripts/` — Analysis and figure generation scripts
- `configs/` — Experiment configuration files
- `consensus_framework.py` — Multi-Method Consensus Test (MMCT) implementation
- `specification_curve_analysis.py` — Specification curve analysis
- `cross_alpha_analysis.py` — Cross-contamination-level analysis
- `bootstrap_ty_validation.py` — Toda-Yamamoto bootstrap validation

## Requirements

```
pip install torch transformers datasets numpy scipy matplotlib seaborn
```

## Reproducing Results

See individual scripts in `scripts/` for analysis pipelines. Key entry points:

- **Permutation Granger causality**: `consensus_framework.py`
- **Dose-response analysis**: `compile_dose_response.py`
- **Figure generation**: `docs/paper/figures/gen_fig_*.py`
