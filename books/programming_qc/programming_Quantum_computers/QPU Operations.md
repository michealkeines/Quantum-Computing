Many QPU instructions have an associate inverse, which can be usefull to know about.

in this case QPU operation is said to be reversible, whihc utilmetly means that no information is lost or discadted when it is applied.

Some QPU opertations are irreversible and have no inverse

# Quantum NOT:

![[Pasted image 20211105050932.png]]

NOT is similar to conventional opertaion, zero becomes one and vice versa. 

it can also operate on qubit superposition.

![[Pasted image 20211105051144.png]]

Reversibility: just as in digital logic, the NOT operation is its own inverse, applying it twice returns a qubit to its original value.

# Quantum HAD:

![[Pasted image 20211105051307.png]]

HAD operation short for Hadamard essentially creates an equal superposition when preseneted with either a |0> or |1> state.

this introduces bizarre and delicate parallelism of quatum superposition.

This allows HAD to produce uniform superpositions in a qubit, ie a superposition where each outcome is equally likely.

Reversibility: Has operation is its own inverse, applying it twice returns a qubit to its original value.


# Quantum READ

![[Pasted image 20211105052959.png]]

The read operation is the formal expression of readout process.

read is unique in being the only part of a QPU instruction set that potentially returns a random result.

appyling read to a single quantum bit will return either 0 or 1 with probabilities determited by the square of the associated magnitued in the qubit's state.

in circle notation an outcome occurs with a probability determinited by the filled area in each associated circle. we then shift the filled in area between circle to reflect the result.

the circle associated with the occuring outcome becomes entirely filled in. while the remaining becomes empty.

![[Pasted image 20211105053902.png]]

thus any superpoisitin is irreverisbly destroyed after a read

as read operation removes all meaningful relative phase information, we reorient so that the cicle points upwards.


# Quantum WRITE

![[Pasted image 20211105053355.png]]

The write operation allows us to initialize a QPU register we operate on it, it is a deterministic process.

using a READ and NOT we can construct a simple WRITE operation, that allows us to prepare a qubit in desired state of either |0> or |1>

first we read a qubit, if the value is not what we wnat, we perform a not operation.

this only gives either 0 or 1 no qubit with arbirtary superpostion.

Write operation is not reversible. it destroys the superpositon.


QCengine, write and had operations default to act on all initialized qubits, unless we explicitly pass specific qubits for them to act on.


# PHASE(degree)

the phase operation has no conventional equivalent.

it allows us to directly manipulate the relaive phase of a qubit

![[Pasted image 20211105063636.png]]

Note that the PHASE operation only rotates the circle associated with the |1> state, so it would have no effect on a qubit in the |0> state.

reversibility: PHASE operations are reversible, althought they are not generally their own inverse, the phase operation may be revresed by applying a phase with the negative of the original angle. this corresponds to the undoing the rotation.

# ROTX(degree) and ROTY(degree)

these two are similar to phase rotation, rotx rotates in x axis and roty rotats in y axsis, we use circular notation, which doent have zaxis, thus we lose that information

![[Pasted image 20211105075751.png]]

# the missing operation COPY

although we can make many copies of a known state by repeatedly preparing it, there is no way of copygin some state partway through a quantum compuation without determinnig what it is.

# Combining operations

![[Pasted image 20211105080245.png]]

We can combine operations to get actuall operations.

# Quantum ROOT-of-NOT

its is literally the square root of the NOT operation, when applied twice, it performs a single NOT. there are more than one way to construct this operation.

![[Pasted image 20211105081222.png]]

![[Pasted image 20211105081233.png]]

![[Pasted image 20211105081330.png]]


Quantum spy hunter

```// Quantum Key Distribution
qc.reset(3);
qc.discard();

var fiber = qint.new(1, 'fiber');
var a = qint.new(1, 'alice');
var b = qint.new(1, 'bob');

function get_random_bit(q) {
    q.write(0);
    q.had();
    return q.read();
}

var send_had = get_random_bit(a);
var send_val = get_random_bit(a);

a.write(0);

if (send_val) {
    a.not();
}
if (send_had) {
    a.had();
}

fiber.exchange(a);

var  recv_had = get_random_bit(b);

fiber.exchange(b);

if (recv_had) {
    b.had();
}

var recv_val = b.read();

qc.print(recv_val)




```

