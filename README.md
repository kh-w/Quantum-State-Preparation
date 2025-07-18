# Quantum-State-Preparation

- [Introduction](#introduction)
- [From-Rz-to-Ry-gate](#from-rz-to-ry-gate)
- [Quantum-State-Preparation-n-3](#quantum-state-preparation-n-3)
  - [Methodology-n-3](#methodology-n-3)
  - [Result-n-3](#result-n-3)
- [Quantum-State-Preparation-n-4](#quantum-state-preparation-n-4)
  - [Methodology-n-4](#methodology-n-4)
  - [Result-n-4](#result-n-4)

## Introduction

The goal of quantum state preparation is to prepare the superposition $\Psi_0\left|0\right\rangle_n+\Psi_1\left|1\right\rangle_n+...+\Psi_{2^n-1}\left|2^n-1\right\rangle_n$ from $\left|0\right\rangle_n$, where $\Psi_n>0$ for all $n$ and $\lVert\Psi\rVert_2=1$.\
\
When $n=1$, it is easy to prepare $\Psi_0\left|0\right\rangle_1+\Psi_1\left|1\right\rangle_1$. If we let $\Psi_0=\cos(\frac{\theta}{2})$, then $\Psi_1=\sin(\frac{\theta}{2})$ by the property of $\lVert\Psi\rVert_2=1$. Then we will have $\Psi_0\left|0\right\rangle_1+\Psi_1\left|1\right\rangle_1=\cos(\frac{\theta}{2})(1\hspace{0.15cm}0)'+\sin(\frac{\theta}{2})(0\hspace{0.15cm}1)'=(\cos(\frac{\theta}{2})\hspace{0.15cm}\sin(\frac{\theta}{2}))'=R_Y(\theta)\left|0\right\rangle$.\
\
When $n=2$, it is also not hard to prepare $\Psi_0\left|0\right\rangle_2+\Psi_1\left|1\right\rangle_2+\Psi_2\left|2\right\rangle_2+\Psi_3\left|3\right\rangle_2$.\
\
$\Psi_0\left|0\right\rangle_2+\Psi_1\left|1\right\rangle_2+\Psi_2\left|2\right\rangle_2+\Psi_3\left|3\right\rangle_2$\
$=\Psi_0\left|00\right\rangle+\Psi_1\left|01\right\rangle+\Psi_2\left|10\right\rangle+\Psi_3\left|11\right\rangle$\
$=(\Psi_0\left|0\right\rangle+\Psi_2\left|1\right\rangle)\otimes\left|0\right\rangle+(\Psi_1\left|0\right\rangle+\Psi_3\left|1\right\rangle)\otimes\left|1\right\rangle$\
$=(\cos(\frac{\theta_{10}}{2})\left|0\right\rangle+\sin(\frac{\theta_{10}}{2})\left|1\right\rangle)\otimes\cos(\frac{\theta_{0}}{2})\left|0\right\rangle+(\cos(\frac{\theta_{11}}{2})\left|0\right\rangle+\sin(\frac{\theta_{11}}{2})\left|1\right\rangle)\otimes\sin(\frac{\theta_{0}}{2})\left|1\right\rangle$\
\
where the definitions for $(\theta_{0},\theta_{10},\theta_{11})$ are:\
\
$\cos(\frac{\theta_{0}}{2})=\sqrt{\Psi_0^2+\Psi_1^2}$ therefore $\sin(\frac{\theta_{0}}{2})=\sqrt{\Psi_2^2+\Psi_3^2}$, and\
$\cos(\frac{\theta_{10}}{2})=\frac{\Psi_0}{\sqrt{\Psi_0^2+\Psi_1^2}}$ therefore $\sin(\frac{\theta_{10}}{2})=\frac{\Psi_1}{\sqrt{\Psi_0^2+\Psi_1^2}}$, and\
$\cos(\frac{\theta_{11}}{2})=\frac{\Psi_2}{\sqrt{\Psi_2^2+\Psi_3^2}}$ therefore $\sin(\frac{\theta_{11}}{2})=\frac{\Psi_3}{\sqrt{\Psi_2^2+\Psi_3^2}}$.\
\
This leads to a circuit designed: apply $R_Y(\theta_0)$ to the second bit, apply $R_Y(\theta_{10})$ to the first bit if the second bit is $0$, and apply $R_Y(\theta_{11})$ to the first bit if the second bit is $1$.\
\
![image](https://github.com/user-attachments/assets/e7603e16-9344-4815-9bdd-14a42a87760f)
\
The gate can be written mathematically in terms of operator compositions:\
$(R_Y(\theta_11)\otimes I)(I\otimes X)(R_Y(\theta_10)\otimes I)(I\otimes X)(I\otimes R_Y(\theta_0))$\
\
For example, $\left|00\right\rangle=\left|0\right\rangle\otimes\left|0\right\rangle$ becomes:\
\
$(I\otimes X)(R_Y(\theta_{10})\otimes I)(I\otimes X)(I\otimes R_Y(\theta_0))(\left|0\right\rangle\otimes\left|0\right\rangle)$\
$=(I\otimes X)(R_Y(\theta_{10})\otimes I)(I\otimes X)(\left|0\right\rangle\otimes R_Y(\theta_0)\left|0\right\rangle)$\
$=(I\otimes X)(R_Y(\theta_{10})\otimes I)(\left|0\right\rangle\otimes XR_Y(\theta_0)\left|0\right\rangle)$\
$=(I\otimes X)(R_Y(\theta_{10})\left|0\right\rangle\otimes XR_Y(\theta_0)\left|0\right\rangle)$\
$=R_Y(\theta_{10})\left|0\right\rangle\otimes R_Y(\theta_0)\left|0\right\rangle$\
$=(R_Y(\theta_{10})\otimes R_Y(\theta_0))(\left|0\right\rangle\otimes\left|0\right\rangle)$\
$=\cos(\frac{\theta_{10}}{2})\cos(\frac{\theta_{0}}{2})\left|00\right\rangle$\
$=\Psi_0\left|00\right\rangle$\
\
Using the same algebraic steps, we can create the quantum state $\Psi_0\left|0\right\rangle_2+\Psi_1\left|1\right\rangle_2+\Psi_2\left|2\right\rangle_2+\Psi_3\left|3\right\rangle_2$.\
\
In the following sections, we will go through the case $n=3$ and $n=4$, while higher values of $n$ can be designed similarly.

## From-Rz-to-Ry-gate

We can build $R_Y(\theta)$ from $R_Z(\theta)$ using the identity $R_Y(\theta)=S^\dagger HR_Z(\theta)HS$:

![image](https://github.com/user-attachments/assets/8b1d9c8e-5f29-43d1-a706-aef4477c3e6e)


## Quantum-State-Preparation-n-3

### Methodology-n-3

For $n=3$, we have:\
\
$\left| \psi \right\rangle=a\left|000\right\rangle+b\left|001\right\rangle+c\left|010\right\rangle+d\left|011\right\rangle+e\left|100\right\rangle+f\left|101\right\rangle+g\left|110\right\rangle+h\left|111\right\rangle$\
\
where $a$ to $h$ are all positive, and $\lVert\psi\rVert^2=a^2+b^2+...+h^2=1$.\
\
Factorize in tensor product sense, note that after factorized, rotations are done by each bit:\
($\color{black}{\text{black = firstbit}}$, $\color{blue}{\text{blue = secondbit}}$, $\color{red}{\text{red = thirdbit}}$)

![image](https://github.com/user-attachments/assets/3795cfbd-e14d-4d03-b240-774a421ed29d)

Looking at the basis states, we can see that $R_y(\theta_{100})$ is applied to the first bit (top wire) when the second and third bits are $00$, $R_y(\theta_{110})$ is applied when the second and third bits are $10$, $R_y(\theta_{101})$ is applied when the second and third bits are $01$, $R_y(\theta_{111})$ is applied when the second and third bits are $11$; then, $R_y(\theta_{10})$ is applied to the second bit (middle wire) when the third bit is $0$, $R_y(\theta_{11})$ is applied when the third bit is $1$; finally, $R_y(\theta_0)$ is applied to the last bit. Therefore a quantum gate can be constructed by using quantum multiplexers, with the $\theta$'s defined below satisfying $\sin^2\theta+\cos^2\theta=1$ and $\lVert\psi\rVert^2=a^2+b^2+...+h^2=1$:\
\
Table A:\
![image](https://github.com/user-attachments/assets/8011164c-f409-4c11-a8e0-e10d8ce4a594)

### Result-n-3

![image](https://github.com/user-attachments/assets/ccfcbccd-67a0-447e-a043-1d96a19da2fb)

Define the $\theta$'s accordingly:

![image](https://github.com/user-attachments/assets/ba828762-4142-4f8e-96b0-b7379e18868b)

A circuit has been built, which can be found in the notebook:

![image](https://github.com/user-attachments/assets/61f1166a-8e65-4750-a768-c34751ef44fb)

Check the prepared state against the original state:

![image](https://github.com/user-attachments/assets/a440ccff-e3e0-4955-9a37-e407480e5739)

We successfully prepared the desired state for $n=3$ using a self-defined qiskit function.

## Quantum-State-Preparation-n-4

### Methodology-n-4

For $n=4$, we have a table similar to table A:\
\
Table B:
![n_equals_4](https://drive.google.com/uc?id=1oToStd8b5iZq6RhwlEky_G91JA2POcFI)
\
Similarly we can build a circuit accordingly.

### Result-n-4

![image](https://github.com/user-attachments/assets/9a740885-da33-4ae9-8c65-cbb650b3fda5)

Define the $\theta$'s accordingly:

![image](https://github.com/user-attachments/assets/3c438bb9-2a35-428a-9d58-8579e4284fe0)

A circuit has been built, which can be found in the notebook:

![image](https://github.com/user-attachments/assets/ed4635ce-b2e0-444a-ba66-2bf64ecbd1b7)

Check the prepared state against the original state:

![image](https://github.com/user-attachments/assets/0f018c27-3047-4fdf-b4fe-6a72b1b4e121)

We successfully prepared the desired state for $n=4$ using a self-defined qiskit function.


