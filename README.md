# Supersonic Nozzle Design via the Method of Characteristics (MOC)

Designs a 2D **Mach 2.6 minimum-length supersonic nozzle** contour using the **Method of Characteristics**, with a Prandtl-Meyer expansion-fan formulation solved from scratch (including a numerical inverse-Prandtl-Meyer root solver).

Developed as part of coursework/research at the University of Florida; originally validated against ANSYS Fluent CFD across ideally-expanded, over-expanded, and under-expanded operating conditions.

## What it does

- Computes the **Prandtl-Meyer function** ν(M) and its numerical inverse (bisection solver) for calorically perfect air (γ = 1.4).
- Designs a **minimum-length nozzle (MLN)** wall contour for a target exit Mach number via centered expansion-wave theory.
- Reports the **expansion-shock Mach deviation** between the MOC-predicted and design exit Mach number (target: < 2%).
- Applies a **real-gas correction** factor to the ideal-gas MOC solution, in the spirit of the compressibility correction validated against CFD in the original study (~15% accuracy improvement over the ideal-gas-only MOC solution).
- Exports the wall contour to CSV for plotting or import into CAD/CFD meshing tools.

## Usage

```bash
pip install -r requirements.txt   # stdlib only
python moc_nozzle.py
```

Example output:

```
Design Mach number: 2.6
Max expansion angle (theta_max): 20.707 deg
MOC-predicted exit Mach number: 2.6000
Expansion-shock Mach deviation: 0.000% (target: < 2%)
Real-gas-corrected exit Mach number: 2.5376
Wall contour points generated: 41
Wrote wall contour to nozzle_contour.csv
```

## Files

- `moc_nozzle.py` — Prandtl-Meyer solver, MLN contour design, real-gas correction
- `nozzle_contour.csv` — example generated wall-contour point cloud
- `requirements.txt` — dependencies (stdlib only)

## Notes

This is a simplified single-family-of-waves MOC implementation (a coarse wall contour via characteristic reflection), intended to demonstrate the underlying compressible-flow theory rather than reproduce a full multi-wave-reflection MOC mesh. The original coursework project validated the resulting contour against ANSYS Fluent CFD under ideally-expanded, over-expanded, and under-expanded back-pressure conditions.

## Author

Arvind Kanagasabapathi Chandirakala — M.S. Aerospace & Mechanical Engineering, University of Florida
[LinkedIn](https://www.linkedin.com/in/arvind-kc-/)
