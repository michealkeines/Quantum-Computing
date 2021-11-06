Can we extend our circle notation to mutiple qubits, if our qubits didnt intract with one another, we could simple employ mulpile version of representations we used for a single qubit.

we could use a pair of circle for the |0> and |1> state of each qubit.

Although this navie representation allows us to describe a superposition of any one individual qubit, there are superpositions of groups of qubits that it cannot represent.

A register of N qubits can be used to represent one of 2^N different values

For example:

A register of 3 qubits in states |0> |1> |1> can represent a decimal value 3.

![[Pasted image 20211106081523.png]]

This is not "one paire of circles per qubit", instead, it is one circle for each possible two-bit number you may get by reading these qubits.

for three qubits, upon readout we can get any three-bit value.

this means that we can now associate a magintude and relative phase with each of these 2^N values.

qc.reset() to set up register with some qubits,

qinit.new() to assign them to qbits

Entanglement allows qubits to communicate in way, that only one value is returned


we can collectivle refer to a register of eight qubits as a qubyte in analogy with a conventional eight bit byte.

what happens when we apply single quit operations such as NOT, HAD, PHASE to a multiqubit register?

The only difference from the single qubit case is that the circles are opeated on in certain operator pairs specific to the qubit that the opertion acts on.

To identify a qubit's operator pairs, match each circle with the one whose value differs by the qubit's bit value

For example, if we are operating on qubit 0x4, then each pair will include circles whoe values differ by excatly 4.

![[Pasted image 20211106090430.png]]

Once these operator pairs have been identifies, the operation is performed on each pair, just as if the members of a pair were the |0> and |1> values of single qubit register.

for a NOT operation, the cirlces in each pair are simply swapped.

for a single qubit phase operation, the righthand circle of each pair is rotated by the phase angle.

![[Pasted image 20211106090706.png]]

reading a qubit in multi qubit register

we can determine the probabilty of obtaining a outcome 0 for one single bit by adding the squared magnitudes of all the circles on the |0> left side of the qubits operator pairs, and probability of 1 by adding the squared magnitudes of all of the circles on the right hand side of the qubit operator pairs.


