
# SVM - Support Vector Machine

Main Characteristics
--------------------
    - Capable of performing linear or nonlinear classification, regression, and even outlier detection. 
    - Well suited for classification
    - Small / Medium datasets


SVM vs Logistics Regression
---------------------------
    - Logistic Regression doesn't care whether the instances are close to the decision boundary.

    - To be more confident with our predictions, the optimal decision boundary should be able to maximize the distance between 
        the decision boundary and all instances. i.e., maximize the margins. 

    - THAT'S WHY SVM IS IMPORTANT ******


What are SVMs?
-------------
    - Given a set of training examples, each marked as belonging to one or the other of two categories, an SVM training algorithm builds a model that 
    assigns new examples to one category or the other, making it a non-probabilistic binary linear classifier.

    - Objective: applying SVMs is to find the best line in two dimensions or the best hyperplane in more than two dimensions in order to help us separate our space into classes.

<!-- Support Vector/Hyperplanes picture -->
![SVM Pic](/pics/SVM_pic1.png)
    
    - Hyperplane (line) = found through the maximum margin, i.e., the maximum distance between data points of both classes.

    - Support Vectors   = the closest points to the hyperplanes. They are the ONLY points that affect the hyperplan (aka the SVM algorithm)
    
    - Margin            = the distance of the vectors from the hyperplane is called the margin

### Good/Bad Margin Example
![Margin Pic](/pics/margin_pic.png)

More about MARGINS
------------------
    - Hard Margin: If the training data is linearly separable, we can select two parallel hyperplanes that separate the two classes of data, so that the distance between them is as large as possible.

        (Problem: it is sensible to outliers. So having a hard margin AND having outliers on the data will affect the SVM model)

  
    - Soft Margin: As most of the real-world data are not fully linearly separable, we will allow some margin violation to occur, which is called soft margin classification

    - Margin violation: choosing a hyperplane, which can allow some data points to stay in either the incorrect side of the hyperplane and between the margin and the correct side of the hyperplane.
  
    - In general, it's better to have a large margin, but some constraints are violated.

### Hard/Soft Margin Example
![Hard/Soft Margin Pic](/pics/hard_soft_pic.png)

How to make SVM better
----------------------
    - Feature Scaling: SVMs are sensitive to scaling. The decision boundary gets way better after scaling. 

    - Balance C: "C" is the hyperparameter that balances between hard/soft margins. A smaller C values leads to a wider "street", but more margin violations.
        (Regularize by reduzing C. Do this if the SVM model is overfitting)

<br><br>

WHAT IF MY DATA IS NOT LINEAR SEPERABLE?????
--------------------------------------------
    - Increse number of dimensions of the data through (mostly) Polynomial Kernel

    - KERNEL TRICK: adds many polynomial features without actually having to add them (which means faster model)




Gaussian RBF (Radial Basis Function)
------------
![GRBF Equation](/pics/gaussian_rbf_eq.png)

    - Another technique to tackle nonlinear problems is to add features computed using a similarity function that measures how much each instance resembles a particular landmark

    - Create a landmark at the location of each instance in the dataset

    - This makes the dataset have now 'm' instances and 'm' features (making it a huge m x m dataset at the end)

    Hyperparameters of RBF Kernel:
        C values:
            - A smaller C values leads to a wider "street", but more margin violations. (same as normal kernel)

        Gamma values:
            - Increasing gamma makes the bell-shape curve narrower

![RBF Kernel](/pics/RBF_kernel.png)


Which Kernel to use?
--------------------
    - Rule of Thumb: Use LinearSVC instead of SVC(kernel='linear')
    
    - GRBF if the dataset is not too large


SVM's Cost Function
-------------------
![RBF Kernel](/pics/svm_cost_function.png)