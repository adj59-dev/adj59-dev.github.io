---
title: "Learning Qiskit"
description: "Notes and examples from completing Coursera’s Practical Quantum Computing with IBM Qiskit for Beginners, with emphasis on circuit simulation, visualization, and execution on IBM quantum hardware."
categories:
  - Qiskit
permalink: /qiskit/learning-qiskit
toc: true
tags:
  - quantum computing
  - Qiskit
  - Coursera
last_modified_at: 2025-12-26 12:00:00 -08:00
---

I recently completed *Practical Quantum Computing with IBM Qiskit for Beginners* on Coursera. I originally started this course about a year ago and worked through roughly the first half (up through Module 20) before putting it on hold while prioritizing other projects. I picked it back up today and was able to finish the remaining material relatively quickly.

When I first took the course, I found it approachable and well structured, particularly given that my prior exposure to quantum computing was mostly limited to experimental quantum optics work from graduate school. Since then, however, I’ve completed the first six chapters of *Quantum Computation and Quantum Information* by Nielsen and Chuang, which significantly deepened my theoretical understanding.

Viewed through that lens, this Coursera course largely overlaps with material from Chapter 4 of QCQI, focusing on basic quantum circuits and their implementation using IBM Qiskit, including execution on IBM’s real quantum hardware. In hindsight, this would have paired extremely well with Chapter 4 if taken in parallel. Doing so would have provided a concrete computational sandbox for validating circuit identities, checking intermediate results, and building intuition, especially since Qiskit allows both statevector simulation and explicit matrix representations.

Completing the course after working through the theory made much of it feel almost trivially easy, but that is not a criticism of the course itself. Rather, it highlights the complementary relationship between theory-first study and hands-on tooling. I’m glad I now have a solid introductory knowledge of Qiskit and a practical path from abstract circuits on paper to executable code on real quantum devices.

Below are my notes from the course. They primarily consist of commonly used Qiskit functions and brief reminders on how to run quantum circuits on IBM’s quantum computers.

<!-- toc -->

## Qiskit Basics and Circuit Construction


### Installation

https://quantum.cloud.ibm.com/docs/en/guides/install-qiskit

### Imports and Dependencies

```
# Core circuit construction and compilation
from qiskit import QuantumCircuit, transpile

# Aer simulators
from qiskit_aer import Aer

# Quantum information objects
from qiskit.quantum_info import Statevector

# Visualization tools
from qiskit.visualization import (
    plot_bloch_multivector,
    plot_histogram
)

# Numerical constants
from numpy import pi
```

### Defining Qubits and Classical Registers

```
qc = QuantumCircuit(1,1)
```
The first argument specifies the number of qubits, and the second specifies the number of classical bits used to store measurement results. In most cases, you will want at least one classical bit per measured qubit.

### State Initialization (Optional)

```
initial_state = [0,1]
qc.initialize(initial_state,0)
```
initialize prepares an arbitrary statevector, bypassing gate-level preparation. This is useful for simulations but is generally not physically realizable on real hardware without decomposition into gates.

Note: Explicit initialization is not required in most circuits. Qubits are initialized to $\ket{0}$ by default, and many states can be prepared using gates alone (e.g., applying a Hadamard to create superposition).

### Gates

#### Pauli Gates

```
qc.x(0)
qc.y(0)
qc.z(0)
```

The input value defines which qubit the gate will be applied to.


#### Hadamard Gate

```
qc.h(0)
```

The input value defines which qubit the gate will be applied to.

#### Single-Qubit Rotation Gates

```
qc.rx(pi/4,0)
qc.ry(pi/4,0)
qc.rz(pi/4,0)
```
The first value is the angle of rotation and the second defines which qubit the gate will be applied to.

#### Phase Gates ($S$ and $S^\dagger$)

```
qc.s(0)
qc.sdg(0)
```

The sdg gate is the $S^\dagger$ gate. The input value defines which qubit the gate will be applied to.

#### $T$ and $T^\dagger$ Gates

```
qc.t(0)
qc.tdg(0)
```

The tdg gate is the $T^\dagger$ gate. The input value defines which qubit the gate will be applied to.


#### General Single-Qubit Unitary (U Gate)

```
qc.u(pi/2,pi/4,pi/8,0)
```

Generic single-qubit rotation in terms of ZYZ Euler angles. The implemented unitary is $U_3(\theta,\phi,\lambda)= R_z(\phi)R_y(\theta)R_z(\lambda)$.

#### Identity Gate

```
qc.i(0)
```

#### Controlled-NOT (CNOT)

```
qc.cx(0,1)
```

The first value defines which qubit is the control and the second is the target.

#### Control-Z gate

```
qc.cz(0,1)
```

The first value defines which qubit is the control and the second is the target.

#### Control-Y gate

```
qc.cy(0,1)
```

The first value defines which qubit is the control and the second is the target.

#### SWAP Gate

```
qc.swap(0,1)
```

Swap the states of the qubits defined by the input values.

#### Toffoli (CCNOT) Gate

```
qc.ccx(0,1,2)
```

The first two values are control qubits and the last defines which qubit is the target. 

### Draw Circuit

```
qc.draw('mpl')
```

<img width="269" height="158" alt="image" src="https://github.com/user-attachments/assets/9d5c340f-3d59-448e-8aa7-c28720e72528" />


### Plot Bloch Vector

```
state = Statevector.from_instruction(qc)
plot_bloch_multivector(state)
```

<img width="787" height="367" alt="image" src="https://github.com/user-attachments/assets/b0ad50d1-7338-40b6-977b-fb430eaa6e62" />


### Histogram

```
# Get the exact final statevector
state = Statevector.from_instruction(qc)

# Compute probabilities for all computational basis states
probs = state.probabilities_dict()

# Plot exact probabilities as a histogram
plot_histogram(probs)
```

<img width="599" height="425" alt="image" src="https://github.com/user-attachments/assets/add2fbe7-6354-4e6b-bf51-ff047c0faa67" />


### Measurement

```
qc.measure(0,0)
qc.measure_all()
```

For measure(a,b), the measurement from qubit a is put in classical bit b. For measure_all(), all the qubits are measured. 

### Barrier

```
qc.barrier()
```

Barriers prevent the transpiler from reordering or combining gates across the barrier, which is useful for visual clarity or enforcing circuit structure.

### Statevector

```
statevector = Statevector(qc)
statevector.draw(output='latex')
```

<img width="219" height="85" alt="image" src="https://github.com/user-attachments/assets/f4b2ba64-059e-4990-af9a-67831ffbe78d" />


### Get Unitary

```
# Create a circuit
qc = QuantumCircuit(2)
qc.h(0)
qc.cx(0, 1)

# Get the unitary simulator backend
backend = Aer.get_backend("unitary_simulator")

# Transpile for the backend
tqc = transpile(qc, backend)

# Run the simulation
result = backend.run(tqc).result()

# Extract the unitary matrix
U = result.get_unitary(tqc)

U.draw(output='latex')
```

<img width="327" height="170" alt="image" src="https://github.com/user-attachments/assets/0edb2c2f-f3c9-4a99-9087-23e44725744f" />

The unitary simulator is useful for validating circuit identities and comparing against analytical matrix representations, but it does not scale beyond a small number of qubits.

### QASM Simulator

```
# Add measurements to all qubits in the circuit.
qc.measure_all()

# Select the QASM (sampling-based) simulator backend.
# This simulator mimics running the circuit on real hardware
backend = Aer.get_backend('qasm_simulator')

# Number of times the circuit is executed.
shots = 1024

# Transpile for the backend
tqc = transpile(qc, backend)

# Run the simulation
job = backend.run(tqc, shots=shots)

# Retrieve the results once execution is complete.
result = job.result()
counts = result.get_counts()

plot_histogram(counts)
```

<img width="605" height="427" alt="image" src="https://github.com/user-attachments/assets/86592051-909b-4062-887d-46096fb979f3" />

The shots parameter controls statistical sampling noise and mimics repeated experimental runs on real hardware.

## Running Circuits on IBM Quantum Hardware

### IBM Quantum Account Setup

You can make a free account at https://quantum.cloud.ibm.com/

### Creating an IBM Quantum Instance

You can signup for a free instance that gives you ten minutes a month of runtime on a quantum computer. 

### IBM Quantum Composer (Web Interface)

You can construct circuits using [IBMs online composer](https://quantum.cloud.ibm.com/composer) and then setup and run jobs on a real quantum computer. It is a drag and drop interface which is easy to use. 


### First Execution on Real Quantum Hardware

#### Submitted Circuit

<img width="204" height="244" alt="image" src="https://github.com/user-attachments/assets/efc17864-05eb-48c8-a772-274481de62fb" />

#### Runtime

This took 2s on the ibm_torino quantum computer.

#### Measured Results

<img width="825" height="588" alt="image" src="https://github.com/user-attachments/assets/40c4d58a-2ebe-4739-a5fd-f635717f1fd3" />

| Measurement outcome | Frequency |
|:-------------------:|:---------:|
| 0000                |	552       |
| 0001                |	472       |

Results from real quantum hardware include noise, readout errors, and gate imperfections, which often cause deviations from ideal simulator results.
