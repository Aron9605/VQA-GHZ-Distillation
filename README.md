# GHZ-state distillation via variational quantum algorithm

This project contains the Wolfram Mathematica notebook (*VQA-GHZDistillation.nb*) for the reproduction of essential results of the '*Training iterated protocols for distillation of GHZ states with variational quantum algorithms.*' article. [ref. [Physics Letters A](https://doi.org/10.1016/j.physleta.2024.129349
)]

The study has been submitted to a scientific journal; the corresponding authors are **Aron Rozgonyi**[1,2], **Gabor Szechenyi**[1,2], **Orsolya Kalman**[2] and **Tamas Kiss**[2].

*Affiliations*:

[1] Institute of Physics, [Eotvos Lorand University](https://www.elte.hu/en/), Budapest, Hungary

[2] Department for Quantum Optics and Quantum Information, [HUN-REN Wigner Research Centre for Physics](https://wigner.hu/en/news), Budapest, Hungary

## Abstract

<p align="justify">
We present optimized distillation schemes for preparing Greenberger-Horne-Zeilinger (GHZ) states. Our approach relies on training variational quantum circuits with white noise affected GHZ states as inputs. Optimizing for a single iteration of the scheme, we find that it is possible to achieve an increased fidelity to the GHZ state, although further iterations decrease the fidelity. The same scheme, acting on coherently distorted pure-state inputs, is effective only in certain special cases. We show that radically different results can be achieved, however, when one optimizes for the output after two iterations of the protocol. In this case, the obtained schemes are more effective in distilling GHZ states from inputs affected by white noise. Moreover, they can also correct several types of coherent pure-state errors.
</p>

## Protocol

<p align="justify">
The entanglement distillation protocol consists of the following steps: 
(1) The parties initially share two copies of the noisy partially entangled GHZ state. Qubits of one of the copies will be used as flags. 
(2) Each party performs identical local unitary operations (U) on their qubits. 
(3) Each party performs projective measurements in the computational basis (M) on the flag qubits. 
If all measurement outcomes are zeros, the unmeasured copy is retained. If any other measurement outcome is observed, it is discarded and the protocol is repeated.
</p>

<p align="center">
<img src="https://github.com/Aron9605/VQA-GHZ-Distillation/assets/55434231/ca5f3195-8000-4a31-9122-51c4f0ed6e1c" width="500" >
</p>

<p align="justify">
The above schematic diagram illustrates the nonlinear protocol employed for GHZ distillation, considering a scenario involving two iterations. Three parties share two noisy GHZ states on which they perform local operations (denoted by the unitary operator U) and subsequent measurements (M). Communication occurs through classical channels, with the objective of post-selecting the states through a consensus process for the next iteration.
</p>

## Variational algorithm

<p align="justify">
An analytical approach to designing a GHZ distillation protocol results in the necessity of heavy non-linear algebra. As an alternative, we utilize a VQA, a quantum-classical hybrid optimization method, in order to efficiently determine the most appropriate U matrix and to manage the related computational cost. In the VQA approach, a classical optimizer is used to train a parametric quantum circuit.
</p>

<p align="center">
<img src="https://github.com/Aron9605/VQA-GHZ-Distillation/assets/55434231/ab578335-9bba-46bd-8502-8c6cb131cfb5" width="500" >
</p>

<p align="justify">
A schematic representation of the variational algorithm is presented, which comprises a quantum circuit constructed using tuneable parametric quantum gates of RX and RY rotations, as well as CNOT gates. The circuit encircled in the yellow box (representing the unitary U) is employed by each party independently at their location. Once each protocol step has been executed by the parties (including the measurements M), the cost function (i.e., the fidelity to the GHZ state) is computed. Subsequently, a classical gradient ascent algorithm is employed to calculate the derivatives of the fidelity with respect to the parameters. The parameters are then updated according to the derivatives and the variational algorithm is run until the output fidelity converges to a final value.
</p>

## Efficiency of the protocol

<p align="justify">
We investigate training the unitary by including two iterations in the cost function.
The fidelity oscillates between two values, indicating that there is a convergence to a stable cycle of length two. For odd-numbered iterations the state is far from the desired GHZ state, however, for even-numbered iterations the GHZ state is distilled to a good approximation. This behaviour is a consequence of the training criterion, as we imposed the cost function to increase the fidelity for a double iteration of the protocol.
</p>

<p align="center">
<img width="500" alt="oscillation" src="https://github.com/Aron9605/VQA-GHZ-Distillation/assets/55434231/74105c0b-7e31-40c7-9c15-28d846136e04">
</p>

<p align="justify">
In order to analyze the tolerance of the distillation protocol utilizing , we employed different levels of white noise strength λ and calculated the output fidelities for even-numbered iterations. A continuous fidelity improvement can be achieved.
</p>

<p align="center">
<img width="500" alt="noises" src="https://github.com/Aron9605/VQA-GHZ-Distillation/assets/55434231/acdec433-9597-4b53-b2c2-1102f0cc4ce5">
</p>

## Code availability:
* VQA-GHZDistillation.nb Wolfram Mathematica notebook contains the VQA algorithm and analysis of results.
* vqa-pretrainedU.py Python notebook contains the analysis of the results.
