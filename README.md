# Gaussian inputs for finite carbon nanotube fragments

Supporting inputs for **Stability and Raman Spectra of Carbon Nanotube Fragments across Chirality and Length** by Huy Nhat Le, Akio Kitao, and Duy Phuoc Tran (manuscript H1, November 2026).

## Contents

Each `CNT_n_m/` contains the original initial PDB, historical Opt1 and Opt2 inputs, the Raman input, and the follow-up inputs used in the manuscript. `H2/` and `reference_molecules/` contain reference calculations. The stored label order is n ≤ m. These are finite molecular fragments, without periodic boundary conditions.

- `initial/`: 20 original starting PDB files.
- `historical/1_opt1/`: B3LYP/6-31G(d) for 19 motifs; HF/6-31G(d) for (5,5).
- `historical/2_opt2/`: restricted M06-2X/6-311G(d,p) optimization.
- `historical/3_raman/`: harmonic frequencies and static Raman activities.
- `followup/`: wavefunction stability, symmetry release, hydrogen capping, bond orders, triplet, functional sensitivity, and polarizability inputs where used.

Original Opt1/Opt2 inputs were named `CNT.dat` and `CNT_D.dat`; only their extensions were changed to `.gjf`. Route sections and coordinates are unchanged. Historical optimizations used Gaussian 16 Revision B.01; Raman and follow-up calculations used Revision C.02. Checkpoints are not distributed. Inputs using `Geom=Check/AllCheck` or `Guess=Read` depend on the appropriate preceding checkpoint. Absolute `%chk` and `%oldchk` paths were reduced to relative file names; copy the required preceding checkpoint into the calculation directory before running those steps. Relative directives were retained. Processor and memory directives were preserved as originally stored; adapt resource allocation to the local scheduler before execution.

`INPUT_PROVENANCE.tsv` maps deposited files to the preserved local source snapshot and hashes. `MANIFEST.sha256` covers all distributed files except itself. No Gaussian outputs, checkpoints, scheduler scripts, or molecular dynamics data are included. Failed checks in `_checks` and unrelated Raman backup attempts are excluded. The original hydrogen-capping input and its default-convergence restart are both retained when the former generated the checkpoint used by the latter.

The (2,3) UKS polarizability input is included; its output was incomplete in the H1 snapshot. The successful (5,5) B3LYP path is represented by the available input files; the native Opt2 `.dat` file of that additional branch was not in the requested `.gjf` snapshot. The historical Opt2 input at the same level is supplied separately.

## Access and reuse

This is a local preparation directory. No remote repository has been configured and nothing has been uploaded. A license has not yet been selected by the authors; this deposit does not grant an open-source license. Gaussian software is not included and requires a separate license.
