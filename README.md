
Quantum Support Vector Machine (QSVM)


![image](https://user-images.githubusercontent.com/68777214/223538076-eb33388f-5683-4587-9a7d-03084baded16.png)


Support Vector Machine (SVM) is a famous method in Machine Learning used to classify data into labels. Developed in the ’60s, SVM’s idea is to find the hyperplane that maximizes the ‘street’ width that divides the labels into the data. The above figure shows the case when there are two features in the data. For three features, SVM will try to find the best plane, and for four or more features, it would try to find the best hyperplane.

To perform the optimization, the ML model minimizes |w| subject to the following constraint:
![image](https://user-images.githubusercontent.com/68777214/223538259-de8d987e-5faa-437b-a4c4-eb47d1bbd1f2.png)

in which yᵢ is the label (i.e -1 or 1), w is the normal vector to the hyperplane, xᵢ is the feature vector, and b is the bias.

One of the main benefits of SVM is that, unlike many ML methods that use the Gradient Descent Algorithm to find the optimal model to predict test data, the vector machine method does not get blocked by local optimal points, as it is a convex optimization problem. This, by itself, makes SVM one of the strongest classification ML models that are available to us.

However, due to its nature, the Support Vector Machine depends on how the data is distributed to be able to find the optimal hyperplane. When there is no optimal hyperplane, SVM needs another feature that makes the classification possible: the Kernel.
![image](https://user-images.githubusercontent.com/68777214/223538402-d2f7c585-4ff5-4362-ab81-0e17fd7beb89.png)


A kernel is a mapping feature that takes data points and maps them into a new domain which, in this case, makes the dataset easier to classify. It works, for instance, by adding new dimensions to the data (i.e. the image above) or redistributing the dataset in the given domain.

Although it may be very computationally expensive to compute the mapping, SVM does not need the map itself, but only the dot products between the feature vector and the weight vector in the kernel function, as given by the optimization equation. This makes kernels extremely useful in better classifying complex datasets.
![image](https://user-images.githubusercontent.com/68777214/223538542-96709285-5120-4a57-9dec-12726acfe05f.png)


Currently, there are several kernel functions. However, Sklearn, a famous data science library, has already implemented 3 useful ones:

* Polynomial → k(xᵢ, xⱼ) = (xᵢ ⋅ xⱼ)ᵈ , linear if d = 1
* Radial Basis Function (RBF) → k(xᵢ, xⱼ) = exp(-γ|xᵢ –xⱼ|²), for γ >0
* Sigmoid → k(xᵢ,xⱼ) = tanh(κ xᵢ ⋅ xⱼ + c), for κ > 0 and c < 0

Even with kernel mapping, however, we might find it computationally expensive and inefficient to find such map features to the point of being ineffective to use SVM. For such cases, we can apply what is known as Quantum Kernel.


Quantum Kernel
The idea behind quantum kernels is to take advantage of quantum mechanics to achieve better results while mapping the feature vector. The general guidelines for such mapping are encoding classical data into qubits, performing operations (such as superposition and rotations in the Bloch sphere), then computing the dot product of the resulting states.

Some of the proposals for the kernel have been made. For instance, Aram Harrow et al. proposed the following kernel circuit:

![image](https://user-images.githubusercontent.com/68777214/223540464-794a0554-f064-42ae-b564-f1026339fa9a.png)

Here, U is a unitary gate that takes the feature vector as a parameter that represents the following, where S is the test dataset:

![image](https://user-images.githubusercontent.com/68777214/223540600-23fade7f-0565-4a2c-b2d9-a6e9b4547247.png)

Although it may be complex, quantum kernels have to perform operations that are not available to a classical machine to outperform them. In the case above, the circuit uses Hadamard gates and Z Pauli matrices to get some advantage over them.

Currently, Qiskit has 2 types of kernels available and another one that allows the user to create circuits that will encode the classical data.

ZFeatureMap
The idea for ZFeatureMap is that, for each dimension in our feature set, there is going to be a qubit that will go through a Hadamard gate and a unitary gate Uϕ.


![image](https://user-images.githubusercontent.com/68777214/223540790-80b7e132-50e1-4b37-a3a6-94c332304a19.png)

As shown, the circuit is linear in the sense that does not ‘crossover’ (i.e. no CNOT gates) information through the qubits, which makes it absent of entanglement besides de H gates.

ZZFeatureMap
The ZZFeatureMap adds entanglement to the quantum system in the following way.

![image](https://user-images.githubusercontent.com/68777214/223540865-60d7ce73-7a73-4c67-9b92-071c56e7a702.png)


Applying Quantum Kernels in ML
Now the next step is applying these ideas into datasets. Qiskit already provides datasets suitable to benchmark QSVM against regular SVM.

First, we are going to import Qiskit and set up our data set:


![image](https://user-images.githubusercontent.com/68777214/223541187-88b17425-d17a-44ec-bd1f-d6106ac08f6d.png)

Then, we are going to get the backend running for our experiment in Qiskit and define our feature map to set up our kernel:

![image](https://user-images.githubusercontent.com/68777214/223541885-429476aa-8516-48fd-a9c9-e6496f1b3fe5.png)

![image](https://user-images.githubusercontent.com/68777214/223542067-affbdfcd-44e8-4808-aa87-d9b50c4e338a.png)

Now we run the experiments:

![image](https://user-images.githubusercontent.com/68777214/223542203-226022b1-9edc-4435-85b3-375627acfd15.png)

Conclusion:

Quantum Machine Learning will improve current predictions models. In particular, Support Vector Machine has been proved to be a very effective method in order to get better results than classical algorithms.

References:

[https://arxiv.org/pdf/1804.11326.pdf]
[https://qiskit.org/documentation/stable/0.32/aqua_tutorials/Qiskit%20Algorithms%20Migration%20Guide.html]
[https://qiskit.org/documentation/machine-learning/tutorials/02a_training_a_quantum_model_on_a_real_dataset.html]
[https://github.com/qiskit-community/qiskit-community-tutorials/blob/master/machine_learning/qsvm_multiclass.ipynb]











