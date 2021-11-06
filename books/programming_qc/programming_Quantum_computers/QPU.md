conventional bits have one binary parameter to play with, 
we initialize it wiith either 0 or 1

on qubits, wherever you read the value of a qubit you will get either 0 or 1 that is after the readout.

but before readout, a qubit isnt 0 or 1, it exist in superpostion of states.

![[Pasted image 20211029050141.png]]

Numbers encloded in bra-ket notation i.e |0} denotes values that a qubit might be found to have when readout.

Physical Qubit:

One Object that readily demonstrates quantum supersposition is a single photon.

let's take a step back and suppose we tried to use the location of a photon to represent a conventional digital bit. like a switchable mirror (that can be set as either refective or transparent) allows us to control whether a photon ends up in one of two paths corresponding to an encoding of either 0 or 1

![[Pasted image 20211029051158.png]]

Now let's try simulating the qubit in this setup, suppose we replace the switch we use to set the photon as 0 or 1 with a half-silvered minrror.

A half silvered mirror also known as beam splitterr is semireflective surface that would with a 50% chance, either deflect light into the path we associate with 1 or allow it to pass straight through to the path we associate with 0. there are no other options.

![[Pasted image 20211029051512.png]]

When a single indivisible photon hits this surface, it suffers a sort of identity crisis. in an effect that has no conventional equalvalent, it ends up existing in a state where it can be influenced by effects in both the 0 path and the 1 path. we say that the photon is in a superposition of traveling in each possiblit path. in other wors, we no longer have a conventional bit, but a qubit that can be in a superpostion of value o and 1.

It's very easy to misunderstand the nature of superposition. it's not correct to say that the photon is in both the 0 and 1 paths at the same time. there is only one photon, os if we put a detectors in each path, only one will go off. when this happens, it reduces the photon's superposition into a digital bit and give a definitive 0 or 1, yet there are computiationally usefull ways a QPU can interact with a quit in superposition before we need to read it out through such a dection.

Amplitude - the maximum extent of a vibration or oscillation

Magnitude - size and speed of an object while it is in motion

when our photon is in a superposition of paths, we say it has an amplitude associated with each path.

The magnitude associated with each path of the photon's superposition is an analog value that measures how much the photon has spread into each path. 

A path's magnitude is related to the probability that the photon will be detected in that path.

Specifically, the square of the magnitude determines the chance we observe a photon in a given path.

we could twiddle the magnitudes of the amplitudes associated with each path by altering how reflective the half-silvered mirror is.

The relative phase between the different paths in the photon's supoerpostion captures the amout by whihc the photon is delayed on one path relative to the other.

this is analog value that can be controlled by the difference between how far the photon tarvels in the paths coressponding to 0 or1, thus we coul change the relative phase without affecting the chance of the photon being detected in each path.

The term amplitude is a way of referring to both the magnitude and the relative phase associated with some value from a qubits superposition.

The Magnitude and relative phase are values available for us to exploit when computing and we can thing of them as being encoded in our qubit. but if were ever to read out any information from it, the photon must eventually strike some kind of detector. at this point both these analog values vanish the quantumness of the qubit is gone.

here lies the crux of quantum computing: finding a way to exploit these ethereal quantities such that useful remnant persists after the destructive act of readout.


From exprementing with photons weve seen that there are two aspects of a qubit general state that we need to keep track of in QPU: the magnitude of it superposition ampitudes and the relative phase between them

The circular notation displays:

The magnitude of the amplitude associated with each value of a qubit can assume is related to the radius of the filled-in area

![[Pasted image 20211029055512.png]]


The magnitude associated with that value really corresponds to the circle radius.

The realtive phase between the amplitudes of these values is indicated by rotation in the circle |1} relative to the |0} circle.

The relative phase of a qubit's state can take any value from 0 to 360, 

![[Pasted image 20211029060352.png]]

As it is relative phase, we nly have to care about one circle's rotation respect to the other.

![[Pasted image 20211029060549.png]]

Note that the relative phase can be varied indepently of the magnitude of a superposition. this independence also works the other way. we can see that the relative phase between outcomes for a single qubit has no direct effect on the chances of what we will read out.

The fact that the relative phase of a single qubit has no effect on the magnitudes in super poisiton means it has no direct influence on the abservable readout results.

but in actuall computation we can cleverly and indirectly affect the chances that we will eventually read out different values.
