# Gaussian inputs and optimized structures for finite carbon nanotube fragments

Supporting inputs for **Stability and Raman Spectra of Carbon Nanotube Fragments across Chirality and Length** by Huy Nhat Le, Akio Kitao, and Duy Phuoc Tran (manuscript in preparation).

## Contents

Each `CNT_n_m/` contains the original initial PDB, historical Opt1 and Opt2 inputs, the Raman input, the follow-up inputs used in the manuscript, and the final optimized structures. `H2/` and `reference_molecules/` contain reference calculations. The stored label order is n ≤ m. These are finite molecular fragments, without periodic boundary conditions.

- `initial/`: 20 original starting PDB files.
- `historical/1_opt1/`: B3LYP/6-31G(d) for 19 motifs; HF/6-31G(d) for (5,5).
- `historical/2_opt2/`: restricted M06-2X/6-311G(d,p) optimization.
- `historical/3_raman/`: harmonic frequencies and static Raman activities.
- `followup/`: wavefunction stability, symmetry release, hydrogen capping, bond orders, triplet, functional sensitivity, and polarizability inputs where used.
- `final/`: optimized structures as XYZ files (Å), extracted from the converged Gaussian outputs.

## Optimized structures

Each XYZ file contains the geometry at which the optimization reported a stationary point, with the electronic energy and orientation frame in its comment line. `FINAL_STRUCTURES.tsv` lists the source output file, its SHA-256 hash, the number of atoms, the energy, and the route section for every structure.

- `CNT_n_m/final/opt2.xyz` (20 motifs): Opt2 geometries at M06-2X/6-311G(d,p). These are the geometries used for the Raman calculations; interatomic distances agree with the geometry read by each Raman job to within 2 × 10⁻⁶ Å.
- `CNT_5_5/final/b3lyp_path_opt2.xyz`: the same Opt2 level reached through B3LYP/6-31G(d) preoptimization (RMSD 0.0014 Å from `opt2.xyz`).
- `CNT_0_3`, `CNT_0_4`, `CNT_2_2`: `released_minimum_plus.xyz` and `released_minimum_minus.xyz` were reoptimized after displacement in either direction along the most negative Opt2 mode and have the same energy. The `plus` structure was used for the subsequent stability and bond-order calculations. `h_capped.xyz` was optimized without symmetry constraints and `h_capped_symmetry_retained.xyz` with symmetry retained.
- `CNT_3_3/final/h_capped.xyz` and `CNT_0_5/final/h_capped.xyz`: hydrogen-capped models optimized without symmetry constraints.
- `CNT_2_3/final/h_capped_selective.xyz`: (2,3) with hydrogen on the isolated two-coordinate carbons C22 and C73 only.
- `H2/final/H2.xyz` and `reference_molecules/final/` (ethylene, benzene, acetylene): reference molecules at the same level.

Original Opt1/Opt2 inputs were named `CNT.dat` and `CNT_D.dat`; only their extensions were changed to `.gjf`. Route sections and coordinates are unchanged. Historical optimizations used Gaussian 16 Revision B.01; Raman calculations and the stability, hydrogen-capping, bond-order, triplet, functional-test and polarizability checks used Revision C.02. The additional (5,5) Opt2 output records Revision B.01. Checkpoints are not distributed. Inputs using `Geom=Check/AllCheck` or `Guess=Read` depend on the appropriate preceding checkpoint. Absolute `%chk` and `%oldchk` paths were reduced to relative file names; copy the required preceding checkpoint into the calculation directory before running those steps. Relative directives were retained. Processor and memory directives were preserved as originally stored; adapt resource allocation to the local scheduler before execution.

`INPUT_PROVENANCE.tsv` maps deposited files to the preserved local source snapshot and hashes. `MANIFEST.sha256` covers all distributed files except itself. No Gaussian outputs, checkpoints, scheduler scripts, or molecular dynamics data are included; optimized geometries are provided as the XYZ files above. Failed test calculations and unrelated Raman backup attempts are excluded. The original hydrogen-capping input and its default-convergence restart are both retained when the former generated the checkpoint used by the latter.

The (2,3) UKS polarizability input is included; the job terminated normally. The Opt2 input of the successful (5,5) B3LYP path was recovered from the Gaussian submission archive `CNT_D.dat.ap` and stored as `CNT_5_5/followup/5_b3lyp_path/4_opt2/CNT_D.gjf`. Its route, charge/multiplicity (0/1), and all 100 carbon coordinates agree with the input section of the completed Opt2 output. The deposited file is byte-identical to that `.ap` archive (including its recorded resource directives); its checkpoint directive already uses a relative basename. The native `.dat` file is no longer available, so byte identity to that missing original has not been established. No file with an `.ap` extension or scheduler script is distributed. The historical Opt2 input is supplied separately.

## Access and reuse

The input files, coordinates, and optimized structures in this repository are licensed under the Creative Commons Attribution 4.0 International License (CC BY 4.0); see `LICENSE`. Gaussian software is not included and requires a separate license.

To verify the files after download, run `shasum -a 256 -c MANIFEST.sha256` from the repository root.
