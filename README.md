# Interstitial Flow Cell Migration Digital Twin

A reproducible proof-of-concept mechanistic digital twin for phenotype-aware cancer-cell migration under interstitial flow.

## What the repository demonstrates

- stochastic switching between amoeboid and mesenchymal states;
- phenotype-dependent speed and persistence;
- synthetic microscopy measurements;
- particle-filter state estimation;
- reverse inference of latent phenotype;
- withheld-data forecasting with calibrated uncertainty; and
- comparison with hold-position and linear-extrapolation baselines.

## Scientific scope

The mechanistic model is calibrated to published aggregate measurements from Huang et al. (2015). Trajectory-level filtering and forecasting are tested on held-out synthetic trajectories. The repository does **not** contain or claim validation on the original experimental tracks.

## Run

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\\Scripts\\activate
pip install -r requirements.txt
jupyter lab
```

Open `digital_twin_reproducible.ipynb`, then select **Restart Kernel and Run All Cells**. Tables and figures are written to `outputs/`.

## Main frozen parameters

| Parameter | Value | Interpretation |
|---|---:|---|
| Fine time step | 0.05 | model-time units |
| Diffusion | 0.25 | model units |
| Amoeboid persistence | 0.50 | model-time units |
| Mesenchymal persistence | 12.0 | model-time units |
| Amoeboid speed multiplier | 2.20 | relative to mesenchymal |
| Measurement noise SD | 0.50 | position units |
| Likelihood scale | 1.25 | multiplier of measurement SD |

## Important interpretation

Six of seven calibrated population observables agree with the published targets within 4%; persistence under flow is overestimated by about 20.6%. In the original finalized analysis, state assimilation reduced synthetic position RMSE by 14.5%, latent phenotype inference achieved mean ROC AUC 0.786, and independent 60-cell forecasts reduced RMSE by 20.4-46.5% relative to linear extrapolation with mean nominal-95% coverage of 94.76%.

## References

1. Y. L. Huang et al., *Integrative Biology* **7**, 1402-1411 (2015). https://doi.org/10.1039/C5IB00115C
2. H. S. Samanta, *Physical Review Research* **2**, 013048 (2020). https://doi.org/10.1103/PhysRevResearch.2.013048

## License

MIT License. See `LICENSE`.
