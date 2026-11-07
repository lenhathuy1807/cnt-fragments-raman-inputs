# Gaussian inputs for finite carbon nanotube fragments

Supporting inputs for **Stability and Raman Spectra of Carbon Nanotube Fragments across Chirality and Length** by Huy Nhat Le, Akio Kitao, and Duy Phuoc Tran (manuscript H1, November 2026).

## Contents

Each `CNT_n_m/` contains the original initial PDB, historical Opt1 and Opt2 inputs, the Raman input, and the follow-up inputs used in the manuscript. `H2/` and `reference_molecules/` contain reference calculations. The stored label order is n ≤ m. These are finite molecular fragments, without periodic boundary conditions.

- `initial/`: 20 original starting PDB files.
- `historical/1_opt1/`: B3LYP/6-31G(d) for 19 motifs; HF/6-31G(d) for (5,5).
- `historical/2_opt2/`: restricted M06-2X/6-311G(d,p) optimization.
- `historical/3_raman/`: harmonic frequencies and static Raman activities.
- `followup/`: wavefunction stability, symmetry release, hydrogen capping, bond orders, triplet, functional sensitivity, and polarizability inputs where used.

Original Opt1/Opt2 inputs were named `CNT.dat` and `CNT_D.dat`; only their extensions were changed to `.gjf`. Route sections and coordinates are unchanged. Historical optimizations used Gaussian 16 Revision B.01; Raman calculations and the stability, hydrogen-capping, bond-order, triplet, functional-test and polarizability checks used Revision C.02. The additional (5,5) Opt2 output records Revision B.01. Checkpoints are not distributed. Inputs using `Geom=Check/AllCheck` or `Guess=Read` depend on the appropriate preceding checkpoint. Absolute `%chk` and `%oldchk` paths were reduced to relative file names; copy the required preceding checkpoint into the calculation directory before running those steps. Relative directives were retained. Processor and memory directives were preserved as originally stored; adapt resource allocation to the local scheduler before execution.

`INPUT_PROVENANCE.tsv` maps deposited files to the preserved local source snapshot and hashes. `MANIFEST.sha256` covers all distributed files except itself. No Gaussian outputs, checkpoints, scheduler scripts, or molecular dynamics data are included. Failed checks in `_checks` and unrelated Raman backup attempts are excluded. The original hydrogen-capping input and its default-convergence restart are both retained when the former generated the checkpoint used by the latter.

The (2,3) UKS polarizability input is included; the job terminated normally. The Opt2 input of the successful (5,5) B3LYP path was recovered from the Gaussian submission archive `CNT_D.dat.ap` and stored as `CNT_5_5/followup/5_b3lyp_path/4_opt2/CNT_D.gjf`. Its route, charge/multiplicity (0/1), and all 100 carbon coordinates agree with the input section of the completed Opt2 output. The deposited file is byte-identical to that `.ap` archive (including its recorded resource directives); its checkpoint directive already uses a relative basename. The native `.dat` file is no longer available, so byte identity to that missing original has not been established. No file with an `.ap` extension or scheduler script is distributed. The historical Opt2 input is supplied separately.

## Access and reuse

This is a local preparation directory. No remote repository has been configured and nothing has been uploaded. A license has not yet been selected by the authors; this deposit does not grant an open-source license. Gaussian software is not included and requires a separate license.
