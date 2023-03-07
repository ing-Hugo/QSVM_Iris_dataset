
#Quantum Support Vector Machine (QSVM)
##Classical Support Vector Machine

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



