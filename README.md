# Quantum Embedding Kernels with Pennylane and Double-Cake Dataset

![grafik](https://github.com/user-attachments/assets/5b9b11c8-2b63-4c5a-a00c-95616cfffa59)



This repository implements a scalable quantum embedding structure inspired by the approach detailed in the paper Training Quantum Embedding Kernels on Near-Term Quantum Computers by Thomas Hubregtsen, David Wierichs, Elies Gil-Fuster, Peter-Jan H. S. Derks, Paul K. Faehrmann, and Johannes Jakob Meyer (2021) - https://arxiv.org/abs/2105.02276. Specifically, it utilizes the quantum embedding structure described on page 10 of the paper.


### Features

- Scalability: Users can configure the number of qubits and layers in the quantum model, enabling flexibility in adapting to different hardware constraints and problem complexities.

- Loss Function: The model optimizes the Kernel-Target Alignment (KTA), a metric that evaluates how well the kernel with its variational parameters captures the dataset’s characteristics. This helps to ensure the embedding is suited for the learning task.

- Quantum Embedding: Built to enable experimentation with quantum embedding kernels, especially in the context of near-term quantum devices.

- q_library.py

    Core utilities for quantum circuits:
    
    Gate Definitions: Differentiable RY, RZ, CRZ gates.
    Layer Functions: Apply gates in parallel (ry_layer, rz_layer, crz_ring).
    Initial State: Start state ∣0...0⟩∣0...0⟩.
    Ring Closure: Handles periodic boundaries for gates.

- q_circuit.py

    Defines the full quantum circuit:
    
    Blocks: Combines Hadamard, parameterized RZ, RY, and CRZ gates.
    Adjoint Blocks: Implements Hermitian reversals for blocks.
    Circuit: Stacks blocks and adjoint blocks for feature embedding.

### Cake Dataset

This repository also features the creation of a synthetic dataset known as Double-Cake Data, designed to test the quantum embedding kernel. The data consists of datapoints arranged in two circular sectors, with their classification based on which sector they fall into.

### Pennylane Tester

This repository also includes the Pennylane Tester, a helper for evaluating the quantum embedding models resulting parameters.


## Setup

The project is executed using main.py. It trains a quantum neural network and evaluates its kernel-target alignment (KTA). The script requires several command-line arguments.
Usage

python main.py <EPOCHS> <PRINT_AT> <QUBITS> <BLOCKS> <LEARNING_RATE> <SECTORS>

Parameters:

    <EPOCHS>: Number of training epochs (e.g., 1000).
    <PRINT_AT>: Frequency of loss printouts during training (e.g., 100).
    <QUBITS>: Number of qubits (e.g., 5).
    <BLOCKS>: Number of quantum circuit blocks (e.g., 5). Odd numbers work better currently.
    <LEARNING_RATE>: Learning rate for training (e.g., 0.05).
    <SECTORS>: Number of sectors in the dataset (e.g., 3).

