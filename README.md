# Grover-Algorithm-Factoring
Using Grover's algorithm for the factorization of bi primes
## Prerequisites
* Python
* Qiskit library
## Setup Guide
### 1.Import the necessary libraries:
```python
import qiskit
from qiskit import * 
from qiskit.visualization import plot_histogram
```
### 2.Create a quantum circuit for factorising 35:
Create a quantum circuit(qc) then append it with the oracle(cq) and diffuser(c) depending on number of iteration to reach the solution.

2.1 quantum circuit(qc):
```python
qc = QuantumCircuit(10,6)
for i in range(6):
    qc.h(i)
qc.x(6)
qc.x(8)
qc.x(9)
qc.h(9)
```
2.2 oracle(cq):
```python
cq = QuantumCircuit(10)
for i in range(6):
    cq.x(i)
cq.x(7)
cq.mcx([0,1,2,3,4,5,6,7,8],9)
for i in range(6):
    cq.x(i)
cq.x(7)
```
2.3 diffuser(c):
```python
c = QuantumCircuit(10)
for i in range(6):
    c.h(i)
    c.x(i)
c.mcx([0,1,2,3,4,5],9)
for i in range(6):
    c.x(i)
    c.h(i)
```
### 3.Implementation:
The number of iteration run is equal to 6 of appending oracle and diffuser in original circuit as taking superposed state to solution state.

 N = integer which is to be factored
 
For convenience we define M = (N − S)/6 − 1 and S = (3-(N mod 6))/2

Two bitstrings x = a, y = b satisfying N = (6a + 6 + s)(6b + 6 + sS) with s = ±1

Find value of a,b from the plot and then find its factors using highest probability bit set

### 4 . Result
#### histogram plot for factoring N = 35:

specifying x = 3 bit number and y = 3 bit number .

convention : starting bit is the least significant bit.

![image](https://github.com/Alokphy/Grover-Algorithm-Factoring/assets/171216145/1e79db53-f9bd-48db-8e14-f8ceb5978049)



the plot gives  a six bit binary with first 3 specifying x and last 3 specifying y

in this case a = 0, b =0, S = -1, taking s =1 gives first number 5 and second 7 as factors 

#### histogram plot for factoring N = 115:

specifying x = 3 bit number and y = 2 bit number

convention : starting bit is the least significant bit.

![image](https://github.com/Alokphy/Quantum-Factoring-Grovers-Algorithm/assets/171216145/2ea1253b-dc93-4c01-85df-2f3b35678ae2)

the plot gives  a five bit binary with first 3 specifying x and last 2 specifying y

in this case a = 3, b =0, S = 1, taking s = -1 gives first number 23 and second 5 as factors

#### histogram plot for factoring 893:

specifying x = 3 bit number and y = 2 bit number

convention : starting bit is the least significant bit.

![image](https://github.com/Alokphy/Quantum-Factoring-Grovers-Algorithm/assets/171216145/c64200d4-feda-431c-91ab-96bdaadc4d66)

the plot gives  a five bit binary with first 3 specifying x and last 2 specifying y

in this case a = 7, b =2, S = -1, taking s = -1 gives first number 47 and second 19 as factors

### Conclusion:
Circuit for how to implement  N = 115 and 893 are given in the code.

### References:
* https://arxiv.org/abs/2312.10054
* Quantum Computation and Quantum Information(Issac Chuang and Michael Nielsen)
























  




