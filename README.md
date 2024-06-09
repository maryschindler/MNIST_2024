# MNIST Dataset - Classifying Handwritten Digits

Last Updated: 06/09/24


**Outstanding Tasks**
1. None


**Index**
1. Analysis Goal
2. Modeling
    1. Simple feed-forward neural network
    2. Feed-forward neural network with data augmentation
    3. Convolutional neural network with data augmentation


## 1. Analysis Goal
Classify handwritten digits from the MNIST database


### 2. Modeling
#### A. Simple feed-forward neural network
***98.44% Accuracy***

A fully connected neural network, taking a 28x28 greyscale image input, flattening, passing it through three hidden dense layers with ReLU activation, outputing a probability distribution over 10 classes using softmax activation:

**Model Architecture**
1. Input: (28, 28, 1)
2. Flatten: (784)
3. Dense: (784) to (512), ReLU
4. Dense: (512) to (256), ReLU
5. Dense: (256) to (128), ReLU
6. Output Dense: (128) to (10), softmax

The model was compiled with Adam optimizer, categorical cross-entropy loss, and accuracy as the evaluation metric. The model was trained for 20 epochs.


#### B. Feed-forward neural network with data augmentation
***98.71% Accuracy***

Using the same neural network described above, data augmentation is applied to improve the model's generalizability:

**Data Augmentation**
- Rotation: Randomly rotate up to 10 degrees
- Zoom: Randomly zoom in up to 10%
- Width shift: Randomly shift horizontally up to 10% of width
- Height shift: Randomly shift vertically up to 10% of height

The model was compiled with Adam optimizer, categorical cross-entropy loss, and accuracy as the evaluation metric. The model was trained for 20 epochs. 


#### C. Covolutional neural network with data augmentation
***99.43% Accuracy***

A convolutional neural network (CNN), taking a 28x28 grayscale image input, processing it through several convolutional and pooling layers, followed by dense layers, and outputing a probability distribution over 10 classes using softmax activation. Data augmentation is applied to the training data to improve the model's generalization. The same data augmentation applied to the feed-forward neural network was used to improve the model's generalizability:

**Model Architecture**
1. Input: (28, 28, 1), Conv2D with 32 filters, kernel size (3, 3), ReLU
2. MaxPooling2D: Pool size (2, 2)
3. Conv2D: 64 filters, kernel size (3, 3), ReLU
4. MaxPooling2D: Pool size (2, 2)
5. Conv2D: 64 filters, kernel size (3, 3), ReLU
6. Flatten: (None, 64)
7. Dense: (64) to (128), ReLU
8. Droupout Layer: Regularization rate 0.50
9. Output Dense: (128) to (10), softmax

The model was compiled with Adam optimizer, categorical cross-entropy loss, and accuracy as the evaluation metric. The model was trained for 20 epochs.