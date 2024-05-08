---
aliases:
  - CNN
---
Convolutional Neural Networks, commonly referred to as CNNs are a specialized type of neural network designed to process and classify **images**.

![[Pasted image 20240425085503.png]]
## Convolutional layers
- **Convolutional Layers**
	- These layers are fundamental in CNNs.
	- They perform the critical operation of convolution.
- **Kernels**
	- Specialized filters that traverse the input image.
	- Extract features such as edges, textures, and shapes.
	- Represented as small matrices of numbers.
![[convolutional-kernel.gif|center]]
- **Kernel Operation**
	- Involves element-wise multiplication with the image pixels.
	- Various methods for deciding kernel values based on desired effects.
![[Pasted image 20240425090010.png|center]]
- **Convolution Operation**
	- Multiplying kernel values by original pixel values and summing results.
- **Feature Map**
	- Output matrix generated by the convolution process.
- **Utility and Importance**
	- Convolution allows automatic extraction of image features.
	- Enables CNNs to learn hierarchical representations of visual patterns.
### Channels
1. **Representation of Features**: Channels in convolutional layers represent distinct aspects or features of the input image.
2. **Output of Kernels**: Each channel is produced by applying multiple kernels to the input image, where each kernel detects specific patterns or features.
3. **Feature Maps**: The output of each kernel is a feature map, and collectively, these maps form the channels in the convolutional layer.
4. **Distinct Features**: Different channels may correspond to different characteristics such as edges, textures, or colors, depending on the learned patterns by the kernels.
5. **Hierarchical Representation**: Channels enable the extraction of various features from the input image, contributing to the network's ability to learn hierarchical representations.
![[rgb-channels.gif|center]]
## Pooling layers
1. **Objective of Convolutional Layers**: Convolutional layers primarily focus on feature extraction rather than dimensionality reduction. They create new channels to capture various features in the input data.
2. **Pooling Layer's Objective**: Pooling layers, on the other hand, aim at dimensionality reduction by resizing the input data while preserving important features.
3. **Pooling Operation**: Pooling layers operate independently on each depth slice of the input data, resizing it spatially using operations like Max or Average pooling.
4. **Difference from Convolution**: Unlike convolution, pooling does not involve applying kernels to the input data but simplifies information through mathematical operations.
5. **Treatment of Channels**: Pooling operations are applied independently to each channel of the input data, thus not reducing the number of channels.
	![[Pasted image 20240425091627.png]]
1. **Visualization of Channels**: Channels remain unchanged in number through convolutional and pooling layers, as shown in the architectural representation.
2. **Combining Channels**: After convolutional and pooling layers extract relevant features, the high-dimensional feature map is prepared for fully connected layers, where the channels are combined for further processing.
![[pooling.gif|center]]
## Flattening layers
- Flattening takes the entire feature map and reorganizes it into a single, long vector.
- Fully connected layers (dense layers) are designed to operate on 1-dimensional data, hence, flattening is a necessary step to transition from the multidimensional tensors produced by convolutional layers to the format required for dense layers.
![[Pasted image 20240425091727.png|center]]

> [!note] Note
> Although flattening changes the shape of the data, it does not make any changes to the actual information.

## Dense layer (fully connected layer)
While convolutional layers are good at **detecting features** in input data, dense layers are essential for **integrating these features into predictions**.
## Activation functions

![[Pasted image 20240425092327.png|center]]
- Activations — Convolutional and dense layers
	- ReLU: is the most common activation function. It outputs the input directly if it is positive, otherwise, it outputs zero. It has the benefit of reducing training time and mitigating the vanishing gradient problem.
	- Leaky ReLU: A variation of ReLU that allows a small, non-zero gradient when the unit is inactive, which can help prevent dead neurons during training.
- Activations — Output layer
	- Sigmoid: Produces an output in the range (0, 1). It’s not commonly used in hidden layers anymore due to the vanishing gradient problem, but it’s still used for binary classification in the output layer.
	- Tanh (Hyperbolic Tangent): Output values in the range (-1, 1). It is similar to the sigmoid but can provide better training performance for some problems due to its output range.
## Backpropagations
![[Pasted image 20240425092448.png|center]]
- Useful links:
	- [Convolutional Neural Networks: A Comprehensive Guide - Medium](https://medium.com/thedeephub/convolutional-neural-networks-a-comprehensive-guide-5cc0b5eae175)
	- [Convolutions and Backpropagations - Medium](https://pavisj.medium.com/convolutions-and-backpropagations-46026a8f5d2c)