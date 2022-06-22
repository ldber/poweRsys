# poweRsys

poweRsys is a collection of utilities for the analysis of power systems. In particular, the focus is on the transmission network. The scripts are written in the R programming language.

The input is a PSS/E RAW v34 file. This is essentially a text file, and is a standard across industry so ensures compatibility. The RAW file contains information about the buses, generators, loads, transmission lines, transformers, and power electronic devices.

The function ReadRaw34(filename) parses the RAW file and returns a structure that contains the network data.

The function ConstructCircuit3(ND) uses the network data to construct the full three phase electrical circuit. It returns a structure containing the indicidence matrix and a vector describing the current-voltage relationship of each branch.

The function ConstructCircuit1(ND) uses the network data to construct the a simplified single phase electrical circuit. It returns a structure containing the indicidence matrix and a vector describing the current-voltage relationship of each branch.

The function LinearSS(EC) uses the electrical circuit (as returned by ConstructCircuit3 or ConstructCircuit1) to find a linear state space representation. It returns a structure containing the state variables, the input variables, and the A, B, C, D matrices.

The function TimeDomainSimulation(SS) uses the state space representation of the circuit to perform a time domain simulation. Each input variable should be represented as a time series. The result is a structure contained the voltages across each capacitor and currents through each inductor.

The function SystemStrength(SS) uses the state space representation to calculate the system strength of each capacitor voltage waveform. It returns a vector containing the Expected Waveform Strength (EWS) of each capacitor voltage.

The results of each function are also written to text file.
