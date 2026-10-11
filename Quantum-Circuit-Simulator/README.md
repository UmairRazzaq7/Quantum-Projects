# Quantum Circuit Simulator: Investigating the Effects of Noise on Quantum Circuits
## 1. Project Overview

This project explores quantum circuit simulation using Python, Qiskit, and Qiskit Aer. It investigates how quantum circuits operate under ideal conditions and how their performance changes when noise is introduced into quantum gate operations.

The project focuses on two important examples in quantum computing:

### Bell-state preparation:
              A fundamental example of quantum entanglement.
### Grover's search algorithm:
              A quantum algorithm designed to search an unstructured search space using fewer oracle queries than classical exhaustive search.

Both circuits are first implemented under ideal conditions and then simulated using a depolarizing noise model. The project also investigates how additional gate operations affect the fidelity of a Bell state, even when those operations do not change the ideal quantum state.

The simulations run locally on a classical computer. No physical quantum processor or paid quantum computing service is required.

The main goal is to connect the mathematical principles of quantum computing with practical circuit implementation, numerical simulation, data analysis, and visualization.

## 2. Project Objectives

The main objectives of this project are:

To understand how quantum circuits are constructed and simulated using Qiskit.
To implement a Hadamard gate and investigate the resulting measurement probabilities.
To prepare and simulate a two-qubit Bell state.
To construct a depolarizing noise model and investigate its effects on quantum circuits.
To calculate Bell-state fidelity as a quantitative measure of similarity to an ideal target state.
To implement Grover's search algorithm for a two-qubit search problem.
To evaluate how noise affects Grover's search success probability.
To investigate how additional gate operations affect Bell-state fidelity.
To analyze simulation data and visualize the relationships between noise, circuit operations, and performance.
## 3. Technologies Used
Python: Implementation of quantum circuits and simulation workflows.
Qiskit: Construction of quantum circuits and definition of quantum operations.
Qiskit Aer: Simulation of ideal and noisy quantum circuits.
NumPy: Generation of numerical parameter ranges.
Pandas: Organization and analysis of simulation results.
Matplotlib: Visualization of measurement distributions and numerical results.
Jupyter Notebook: Interactive development and documentation of the experiments.
## 4. Experiment 1: Single-Qubit Superposition

The first experiment introduces the basic principles of quantum circuit simulation.

A circuit containing one qubit is constructed, and a Hadamard gate is applied before measurement.

The Hadamard gate transforms the computational basis state |0⟩ into an equal superposition:

|ψ⟩ = (|0⟩ + |1⟩) / √2

The ideal measurement probabilities are:

P(0) = 0.5
P(1) = 0.5

The circuit is executed for 1,000 shots to generate simulated measurement data. A histogram visualizes the frequency of each outcome.

Because the measurements are sampled, the observed frequencies may differ slightly from the theoretical probabilities.

Purpose: To understand quantum gates, superposition, measurement, shot-based simulation, and probability visualization.

## 5. Experiment 2: Bell-State Preparation and Simulation

The second experiment investigates quantum entanglement by constructing a two-qubit Bell-state circuit.

The circuit consists of three operations:

Apply a Hadamard gate to the first qubit.
Apply a controlled-NOT (CNOT) gate, using the first qubit as the control and the second as the target.
Measure both qubits.

Starting from |00⟩, these operations prepare the Bell state:

|Φ⁺⟩ = (|00⟩ + |11⟩) / √2

For an ideal circuit, the measurement probabilities are:

P(00) = 0.5
P(01) = 0
P(10) = 0
P(11) = 0.5

The circuit is simulated for 10,000 shots, and the measurement counts are displayed as a histogram.

The expected result is that 00 and 11 occur with approximately equal frequencies, while 01 and 10 do not occur in an ideal simulation.

This experiment establishes a baseline for comparison with noisy circuit behavior.

Purpose: To understand how quantum gates generate entanglement and how ideal quantum circuits produce correlated measurement outcomes.

## 6. Experiment 3: Modeling Depolarizing Noise

Real quantum computers are affected by imperfect gate operations and interactions with their environments. These effects can reduce the accuracy of quantum computations.

To investigate this behavior, the project introduces a depolarizing noise model using Qiskit Aer.

The model applies noise after selected quantum gates:

Single-qubit depolarizing errors after Hadamard gates.
Two-qubit depolarizing errors after CNOT gates.

A noise parameter, p, controls the strength of the modeled errors.

The experiments investigate the following values:

p = 0.00, 0.01, 0.05, 0.10, 0.20

These values are selected for numerical investigation and do not represent measured error rates from a specific quantum processor.

The Bell-state circuit is simulated under each noise setting. Its measurement distribution is compared with the ideal distribution.

Under the selected noise model, outcomes such as 01 and 10 can appear because errors can disrupt the correlations established by the circuit.

Purpose: To investigate the relationship between modeled gate noise and quantum circuit output.

## 7. Experiment 4: Bell-State Fidelity Analysis

Measurement histograms help explain circuit outputs, but they do not completely characterize the underlying quantum state.

To obtain a more informative measure of state quality, the project calculates Bell-state fidelity.

For a pure target state |ψ⟩ and a simulated density matrix ρ, the fidelity is:

F = ⟨ψ|ρ|ψ⟩

Here:

|ψ⟩ represents the ideal Bell state.
ρ represents the quantum state produced by the noisy simulation.
F quantifies the similarity between the simulated state and the ideal target state.

The ideal Bell state is constructed separately, and the noisy circuit is simulated using the density-matrix method.

Density matrices are useful for representing quantum states affected by noise because the resulting state can be mixed rather than described by a single pure-state vector.

Fidelity is calculated for multiple noise strengths, from zero to 0.20.

The results are recorded and plotted to investigate how increasing depolarizing noise affects the quality of the prepared Bell state.

In the absence of added noise, fidelity should be approximately 1. As the modeled noise increases, fidelity is expected to decrease for this circuit and noise model.

Purpose: To quantify the effect of noise on quantum-state preparation rather than relying only on measurement histograms.

## 8. Experiment 5: Grover's Search Algorithm

The project next implements Grover's search algorithm, introducing a quantum algorithm beyond basic state preparation.

The search space contains four possible two-bit states:

00, 01, 10, 11

The target state is 11.

The circuit begins by applying Hadamard gates to both qubits, creating a uniform superposition over the four possible states.

An oracle then marks the target state using a controlled-Z (CZ) gate. The Grover diffusion operator amplifies the amplitude of the marked state.

The circuit performs one Grover iteration before measuring both qubits.

For this two-qubit problem, one ideal Grover iteration identifies the target state with probability 1.

The resulting measurement distribution provides a baseline for evaluating the algorithm under noisy conditions.

Purpose: To implement a basic quantum search algorithm and understand how an oracle and diffusion operator amplify the probability of a target result.

## 9. Experiment 6: Grover's Algorithm Under Noise

After implementing the ideal search circuit, the same depolarizing noise model is applied to its quantum gate operations.

The circuit is simulated at multiple noise strengths, and the number of times the target state 11 is measured is recorded.

The success probability is calculated as:

Success Probability = Number of Target Outcomes / Total Number of Measurement Shots

For example, if the target appears in 8,000 out of 10,000 shots, the observed success probability is 0.8.

The simulations are repeated across the selected range of noise parameters, and the results are plotted.

This experiment investigates how errors affect the algorithm's ability to return the correct answer.

The results are specific to the circuit implementation and noise model used in this project. They should not be interpreted as universal estimates of Grover's performance on real quantum hardware.

Purpose: To evaluate how modeled quantum gate errors affect the success probability of a quantum search algorithm.

## 10. Experiment 7: Comparing Quantum Circuit Performance

The next experiment combines the Bell-state fidelity and Grover success-probability results into a single dataset.

For each noise parameter, the project records:

Depolarizing noise strength.
Bell-state fidelity.
Grover success probability.

The results are organized using Pandas and exported to a CSV file.

A comparison graph shows how both performance metrics change with noise strength.

The two metrics describe different aspects of quantum circuit performance:

Bell-state fidelity measures the similarity between the simulated state and an ideal target state.
Grover success probability measures how frequently the algorithm returns its desired answer.

Comparing these quantities helps investigate whether the two circuits respond similarly to the same modeled noise conditions.

Purpose: To organize the numerical results and compare the behavior of a quantum state-preparation circuit with a quantum search algorithm.

## 11. Experiment 8: Circuit Operations and Bell-State Fidelity

The final experiment investigates how additional gate operations affect Bell-state fidelity.

A Bell state is first prepared using a Hadamard gate and a CNOT gate.

Pairs of additional CNOT operations are then inserted into the circuit.

Two consecutive CNOT operations cancel each other in an ideal circuit:

CNOT × CNOT = Identity

Consequently, adding pairs of CNOT gates does not change the final ideal Bell state.

However, the added gates are subject to the specified noise model. Their presence can therefore affect the final simulated state.

The experiment evaluates fidelity for circuits containing different numbers of additional CNOT pairs.

The resulting graph shows how fidelity changes as more gate operations are introduced.

This provides a controlled way to investigate the relationship between the number of noisy gate operations and the quality of the final quantum state.

It also highlights an important distinction: two circuits can implement the same ideal quantum operation but exhibit different performance when noise is included.

Purpose: To investigate the effect of additional noisy gate operations while keeping the ideal final quantum state unchanged.

## 12. Data Analysis and Visualization

The project uses numerical analysis to summarize the results of the experiments.

The main quantities investigated are:

### Quantity	Interpretation
Measurement counts	Number of occurrences of each measured bit string
Bell-state fidelity	Similarity between the simulated state and the ideal Bell state
Grover success probability	Fraction of measurement shots that return the target state
Depolarizing noise strength	Parameter controlling the modeled noise channel
Number of additional CNOT pairs	Parameter controlling the added gate operations

### Matplotlib is used to generate four main figures:

Bell-state fidelity versus depolarizing noise strength.
Grover success probability versus depolarizing noise strength.
Comparison of Bell-state fidelity and Grover success probability.
Bell-state fidelity versus the number of additional CNOT pairs.

The simulation results are also exported to CSV format for further inspection in Python, Excel, or other data-analysis tools.

## 13. Key Research Questions

The project investigates the following questions:

How does depolarizing noise affect Bell-state fidelity?
How does noise influence the probability of obtaining the correct result from Grover's algorithm?
Do Bell-state fidelity and Grover success probability respond similarly to increasing noise?
How does adding noisy gate operations affect the fidelity of an ideally unchanged Bell state?
What are the limitations of using a simplified depolarizing noise model to represent quantum hardware?

The answers should be derived from the numerical results produced by the simulations rather than assumed in advance.

## 14. Limitations

This project uses classical simulation rather than experiments on physical quantum hardware.

The depolarizing noise model is a simplified representation of quantum errors. It does not include every source of error found in real quantum processors, such as device-specific calibration errors, crosstalk, leakage, and time-dependent environmental effects.

The Bell-state and Grover experiments use small circuits that can be simulated easily on a classical computer. Their results do not establish how larger quantum circuits will behave.

The study also does not, by itself, demonstrate a new quantum algorithm or a new error-correction technique.

The findings should therefore be interpreted as a numerical investigation of selected quantum circuits under a defined noise model.

## 15. Conclusion

This project provides a practical introduction to quantum circuit simulation and numerical analysis using Python and Qiskit.

It progresses from a single-qubit superposition to Bell-state preparation, noisy quantum-state simulation, fidelity calculations, and Grover's search algorithm.

By varying noise strength and introducing additional gate operations, the project investigates how quantum circuit performance depends on the operations performed and the noise model used.

The work combines quantum computing concepts, programming, simulation, and data visualization in a reproducible workflow. It also establishes a foundation for further study of quantum noise, circuit optimization, and quantum algorithm reliability.

Note: Numerical conclusions should be added after the simulations have been executed and their results verified.
