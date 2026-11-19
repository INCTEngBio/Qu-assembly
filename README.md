# Qu-assembly: Quantum Biological Sequence Search and *In Silico* Genomic Assembly

**QuAssembly** (integrated with **QuBio**) is an open-source quantum bioinformatics pipeline that bridges pure quantum search logic with biological sequence reconstruction. Designed as a foundational quantum assembly primitive, the algorithm couples $n$-qubit Grover-driven scar site identification on the Qiskit `AerSimulator` with automated *in silico* ligation of standardized synthetic biological cassettes (**BioBloQu**), executing seamless target replacement within genomic sequences.

---

## 🧬 Key Features

- **Biological Modular Cassette Design (BioBloQu):** Constructs standardized synthetic genetic assemblies composed of:
  - **Leader / Reporter:** Kozak-optimized synthetic linker sequence (`GCCACCATGGTGAGCAAGGGCGAGGCT`)
  - **Ribosome Binding Site (RBS):** Shine-Dalgarno consensus motif (`AGGAGG`)
  - **Functional Coding Sequence (CDS):** Catalytic enzyme sequence (`enzyme_seq`, 57 bp)
  - **Transcription Terminator:** Polyadenylation signal (`AATAAA`)
- **Orthogonal Quantum Nucleotide Mapping:** Direct Hilbert-space state preparation encoding biological nitrogenous bases into discrete single-qubit registers:
  - **Adenine (A):** $|0\rangle$ (Ground computational basis state / `pass`)
  - **Thymine (T):** $|1\rangle$ via Pauli-$X$ gate
  - **Cytosine (C):** $|+\rangle$ via Hadamard ($H$) followed by Pauli-$X$ gate
  - **Guanine (G):** $|-\rangle$ via Pauli-$X$ followed by Hadamard ($H$) gate
- **Target Scar Oracle with Hermitian Uncomputation:**
  - **Pre-computation:** Rotates candidate biological target scars into the $|11\dots 1\rangle$ activation state.
  - **Phase Kickback:** Inverts the quantum phase of the marked target via an $(n-1)$-controlled NOT gate (`MCXGate`) conjugated by Hadamard gates on the target register.
  - **Hermitian Uncomputation:** Executes mirrored gate reversal ($U_{\text{oracle}}^\dagger$) across data registers to eliminate entanglement artifacts and protect quantum coherence.
- **Quantum Inversion-About-the-Mean (Grover Diffuser):** Evaluates constructive wave interference ($U_s = 2|s\rangle\langle s| - I$) across the uniform superposition state $|s\rangle$.
- **In Silico Genomic Recombination:** Validates detected target scars against measurement confidence thresholds (1,024 shots on `AerSimulator`) and executes automated sequence splicing, substituting genomic target loci with the synthetic BioBloQu payload.
- **Automated Diagnostic Plotting:** Generates publication-ready comparative bar charts illustrating quantum detection probabilities across multiple target scar loci benchmarked against the ideal unit probability ($P = 1.0$).

---

## 🔬 Computational Pipeline

*(Describe the end-to-end steps from target scar encoding and Grover search to BioBloQu assembly and genomic splicing here.)*

---

## 📦 Requirements and Dependencies

- **Python 3.8+**
- [Qiskit](https://qiskit.org/) (`qiskit >= 0.45.0` or `1.0+`)
- [Qiskit Aer](https://github.com/Qiskit/qiskit-aer) (`qiskit-aer`)
- [NumPy](https://numpy.org/)
- [Matplotlib](https://matplotlib.org/)
