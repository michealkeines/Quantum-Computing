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


# QPU instruction: CNOT

![[Pasted image 20211112092131.png]]

CNOT operates on two qubits and can be though of as an if programming construct

that is 

Apply the NOT operation to a target qubit, but only if a condition qubit has the value 1.

the circuit symbol used for CNOT shows this logic for connecting two qubits with a line.

A filled dot represents that control qubit, while a not symbol shows the target qubit to be conditionally operated on.


![[Pasted image 20211112092629.png]]

We can see that the essential operation of CNOT is same as that of NOT, only more selective, applying the not operation only to values who binary representaion have a 1 in second bit.

Reversibility: Like that not operation, CNOT is its own inverse, applying the CNOT operation twice will return a multi-qubit register to its initial state.


on its own its doesnt have any import feature, but if we pass superposition in control qubit, the result if 1 would make the operated bit will able be one thus will be 00 or 11, thus 0 or 3, this is means that two qubits are entangled, thus if a reads out 0, b will also be 0 and if a reads out 1, b will also be one.

although the readout must be random, they always agree on 00 or 11


# Instruction CPHASE

![[Pasted image 20211112110350.png]]


Like the CNOT operation, CPHASE employs a kind of entanglement generating conditional logic.

As CNOT did for NOT, CPHASE restricts this action on some target qubit to occur only when another control qubit assumed value |1>.

CPHASE acts only when its control qubit is |1> and when it does act, it only affects target qubit startes have value |1>

THis means that CPHASE applied to say qubit 1 and 4 results in rotation of all circles for which both two qubits have a value of |1>. because of this property CHASE has a symmetry between its inputs not shared by CNOT

![[Pasted image 20211112113544.png]]

Adding a condition further cuts the number of rotated circle in half.

in general the more we conditon qpu operations, the more selective we can be with which values in a qpu register we manipulate.

# QPU instruction CZ

![[Pasted image 20211112114000.png]]

qpu programs frequently employs the CPHASE(180), thus it got its own name and simplized symbol

# Phase kickback

![[Pasted image 20211112124306.png]]

![[Pasted image 20211112124316.png]]

![[Pasted image 20211112140641.png]]

phase kickback is very usefull idea, as we can use it to apply phase rotations to specific values in a register.

we can do this by performing a phase rotation on some other register conditionsed on qubits from the register we really care about. we can choose these qubits to specifically pick out the values we want to rotate.

it will be of great use to understand the inner workings of the quantum phase estimation QPU permitive.


# QPU Instruction: CCNOT (Toffoli)

![[Pasted image 20211113042510.png]]

A CNOT with two condition qubits is commonly referred to as a CCNOT operation.

CCNOT is also sometimes called a Toffoli gate, after the identically titled equivalent gate from conventional computing.

with each condition added, the NOT operation stays the same, but the number of operator pairs affected in the register's circle notation reduced by half.

![[Pasted image 20211113042926.png]]

In a sense CCNOT can be interpreted as an operation implementing "if A and B then flip C".

# QPU instructions: SWAP and CSWAP

![[Pasted image 20211113043629.png]]

Swap or exchange, which simple exchanges two qubits.

if the architecture of a QPU allows it, SWAP may be a truly fundamental operation in which the physical objects representing qubits are actually moved to swap their positions.

it can also done by three CNOT operations

![[Pasted image 20211113043948.png]]

Swap comes into its own when we cosider generalizing it to a conditional operation called CSWAP or conditional exchange.

![[Pasted image 20211113044204.png]]

if the condition qubit for a CSWAP operation is in superposition. we will endup with a superpoistion of our two qubits being exchanged and also being not exchanged.

if the two swap variable are |1>, then output will always be 1

as the two swap variables are more different, the probability of reading a 1 outcome in the output register decresases

The more runs for which we obsrve a 1 outcome, the more convinced we can be that the two input states were identical.

precisely how many times we would need to repeat the swap test depends on how confident we want to be that the two points are identical and how close we would allow them to in order to be called identical.

![[Pasted image 20211113060708.png]]

Rather than looking at the swap test as a yes/no way of ascertaining two states are equal, another usefull interpreation is to note th probability that we get a 1 outcome is a measure of a just how identical the two inputs are.


Constructing any conditional operation.

By breaking our single qubit operation into smaller steps
