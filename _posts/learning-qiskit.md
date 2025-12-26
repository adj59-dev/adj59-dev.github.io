---
title: "Learning Qiskit"
description: "Learning Qiskit through Coursera's Practical Quantum Computing with IBM Qiskit for Beginners."
categories:
  - Qiskit
permalink: /qiskit
toc: true
tags:
  - quantum computing
  - Qiskit
  - Coursera
last_modified_at: 2025-12-07 12:00:00 -08:00
---

## Programming in Qiskit

### Import packages 

```
from qiskit import *
from qiskit_aer import Aer
from qiskit.visualization import plot_bloch_multivector, plot_histogram, visualize_transition
```

### Define bits

```
qc = QuantumCircuit(1,0)
```
The first number is the number of qubits in the circuit and the second number is the number of classical bits

### Initilize bits

```
initial_state = [0,1]
qc.initialize(initial_state,0)
```

### Construct circuit

#### Pauli gates

```
qc.x(0)
qc.y(0)
qc.z(0)
```

The input value defines which qubit the gate will be applied to.


#### Hadamard gate

```
qc.h(0)
```

The input value defines which qubit the gate will be applied to.

#### Rotation gates

```
from numpy import pi
qc.rx(pi/4,0)
qc.ry(pi/4,0)
qc.rz(pi/4,0)
```
The first value is the angle of rotation and the second defines which qubit the gate will be applied to.

#### S gate

```
qc.s(0)
qc.sdg(0)
```

The sdg gate is the $S^\dagger$ gate. The input value defines which qubit the gate will be applied to.

#### T gate

```
qc.t(0)
qc.tdg(0)
```

The tdg gate is the $T^\dagger$ gate. The input value defines which qubit the gate will be applied to.


#### General U gates

```
from numpy import pi
qc.u(pi/2,pi/4,pi/8,0)
```

Generic single-qubit rotation in terms of ZYZ Euler angles. The parameters are $R_z(\phi),R_y(\theta),R_z(\lambda)$.

$$\begin{aligned}
U_3(\theta, \phi, \lambda) &= \begin{bmatrix} \cos(\theta/2) & -e^{i\lambda}\sin(\theta/2) \\\ e^{i\phi}\sin(\theta/2) & e^{i\lambda+i\phi}\cos(\theta/2) \end{bmatrix} \\
U_2 &= U_3(\frac{\pi}{2},\phi,\lambda)\\
U_1 &= U_3(0,0,\lambda)\\
\end{aligned}$$

#### Identity gate

```
qc.i(0)
```

### Draw circuit

```
qc.draw('mpl')
```

### Plot Bloch vector

```
backend = Aer.get_backend("statevector_simulator")
out = transpile(qc, backend)
plot_bloch_multivector(out)
```

### View results histogram

```
results = backend.run(out).result()
counts = results.get_counts()
plot_histogram(counts)
```

### Measurement

```
qc.measure(0,0)
```

## Running Qiskit code on quantum computer

### Create an account and signin

https://quantum.cloud.ibm.com/

### Create an instance

You can signup for a free instance that gives you ten minutes a month runtime on a quantum computer. 

### Online composer

You can construct circuits using [IBMs online composer](https://quantum.cloud.ibm.com/composer) and then setup and run jobs on a real quantum computer. It is a drag and drop interface which is easy to use. 


### My first time using a quantum computer

#### Code

<img width="204" height="244" alt="image" src="https://github.com/user-attachments/assets/efc17864-05eb-48c8-a772-274481de62fb" />

#### Runtime

This took 2s on the ibm_torino quantum computer.

#### Results

<img width="825" height="588" alt="image" src="https://github.com/user-attachments/assets/40c4d58a-2ebe-4739-a5fd-f635717f1fd3" />

| Measurement outcome | Frequency |
|:-------------------:|:---------:|
| 0000                |	552       |
| 0001                |	472       |
