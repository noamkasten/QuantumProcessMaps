
# Quantum Process Maps

## Overview

This project provides a detailed exploration of quantum process maps, focusing on the theoretical and practical aspects of modeling noisy quantum circuits. The accompanying Jupyter Notebook demonstrates the application of these concepts using Python.

## Theory

### Quantum States and Operations

In theory, the state of a quantum system is represented by a density matrix $$\rho$$, which is a positive semi-definite matrix with trace one. This matrix provides a complete description of the quantum state, including mixed states that can arise from statistical mixtures of different pure states.

Quantum operations describe how quantum states evolve. These operations can include:
- **Unitary transformations**: Ideal, noiseless operations.
- **Non-unitary processes**: Such as noise and decoherence.

These operations, including noisy gates, can be described using quantum channels through Kraus Representation:

$$E_j (\rho) = \sum_i K_i \rho K_i^\dagger$$
$$\sum_i K_i^\dagger K_i = I$$

### Noisy Quantum Circuits

Our approach involves dividing the quantum circuit into different parts, each represented by a channel $$ E_j (\rho) $$ defined with its Kraus operators. This allows us to model the noisy channels as follows:

$$\rho_j = E_j (\rho_{j-1})$$

#### Types of Noise

1. **Regular Noises on States**:
   - Example: Bit-flip on the second qubit:
   
   $$\rho_j = E_j (\rho_{j-1}) = (1 - f_j(\{p_i\})) \rho_{j-1} + f_j(\{p_i\}) \cdot X_2 \rho_{j-1} X_2^\dagger$$
   - Here, $$ \{p_i\} $$ represents the fault degree of freedom for the i-th regular noise, and $$f_j(\{p_i\}): [0,1] \rightarrow [0,1]$$ is a function of these parameters.

2. **Noisy Syndrome/Fixing Gates**:
   - For two-qubit gates with an operator $$O_{\text{original}}$$, we replace it with an "unwanted operation" $$O_{\text{noise}}$$ with probability $$g_j(\{q_i\}): [0,1] \rightarrow [0,1]$$:
   
   $$\rho_j = E_j (\rho_{j-1}) = (1 - g_j(\{q_i\})) O_{\text{original}} \rho_{j-1} O_{\text{original}}^\dagger + g_j(\{q_i\}) \cdot O_{\text{noise}} \rho_{j-1} O_{\text{noise}}^\dagger$$

### Assumptions of Our Model

To simplify our model, we made the following assumptions:
1. **Linear Noises**: $$f_j(\{p_i\}) = p_i$$ and $$g_j(\{q_i\}) = q_i$$.
2. **Uniform Fault Probability**: $$p_i = p$$ and $$q_j = q$$ for all $$i, j$$.
3. **Simplified Identity Noise Model**: For faulty two-qubit gates, $$O_{\text{noise}} = I$$, meaning the gate essentially does not work.

## Getting Started

### Prerequisites

- Python 3.x
- Jupyter Notebook


### Running the Notebook

1. Open Jupyter Notebook:
   ```sh
   jupyter notebook
   ```
2. Open the `5_qubit_error_correction_code.ipynb` notebook and run the cells to see the theory in action.


## Acknowledgements

- Quantum Computation and Quantum Information by Michael A. Nielsen and Isaac L. Chuang
