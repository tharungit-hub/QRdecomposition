# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Householder reflection method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	The householder reflection is given by 

    ![eqn1](./eq1.jpg)
2.	The vector u is given by

    ![eqn2](./eq2.jpg)
3.	Q matrix can be found by taking the dot product of each successively formed Householder matrix. 
![eqn3](./eq3.jpg)
4.	Find appropriate H matrices and multiplying them from the left by the original matrix A to construct the upper triangular matrix R.

## Program:
i)	# Householder reflection method
```
''' 
Program to QR decomposition using the Householder reflection method
Developed by: M VIGNESH
RegisterNumber: 21004061
'''
import numpy as np
def qr(A):
	m, n = A.shape
	Q = np.eye(m)
	for i in range(n - (m == n)):
	    H = np.eye(m)
	    H[i:, i:] = make_householder(A[i:, i])
	    Q = np.dot(Q, H)
	    A = np.dot(H, A)
	return Q, A
def make_householder(a):
	v = a / (a[0] + np.copysign(np.linalg.norm(a), a[0]))
	v[0] = 1
	H = np.eye(a.shape[0])
	H -= (2 / np.dot(v, v)) * np.dot(v[:, None], v[None, :])
	return H
a = np.array([[2, -2, 18], [2, 1, 0], [1, 2, 0]])
q, r = qr(a)
print('q:\n', q.round(6))
print('r:\n', r.round(6))
```
ii)	# using np.linalg.qr
```
import numpy as np
m1=np.array([[2, -2, 18], [2, 1, 0], [1, 2, 0]])
print(m1)
 q,r =np.linalg.qr(m1)
print('\n Q:\n',q)
print('\n R:\n',r)
```
## Sample Input and Output
![inp](./input.jpg)

## Result
Thus the QR decomposition algorithm using the Householder reflection method is written and verified the result.