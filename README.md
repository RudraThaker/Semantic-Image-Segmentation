# Semantic-Image-Segmentation
Semantic image segmentation, which becomes one of the key applications in image processing and computer vision domain, has been used in multiple domains such as medical area and intelligent transportation. Semantic image segmentation plays a central role in image understanding. With the development of deep learning techniques, great progress has been made in recent years.

## Dataset

In this paper we survey the architecture on the Pascal VOC 2012 semantic segmentation challenge, which is the most representative image dataset for this purpose.
The twenty object classes that have been selected are as follows:
Person: person
Animal: bird, cat, dog, cow, horse, sheep
Vehicle: aeroplane, bicycle, boat, bus, car, motorbike, train
Indoor: bottle, chair, dinning table, potted plant, sofa, TV/monitor

## Network architecture:


The network architecture consists of a contractive path (left side) and an expansive path (right side). The contracting path follows the typical architecture of a convolutional network. It consists of the repeated application of two 3x3 convolutions (padded convolutions) with batch normalization, each followed by a rectified linear unit (ReLU) and a 2x2 max pooling operation with stride 2 for down-sampling. At each down-sampling step we double the number of feature channels. Every step in the expansive path consists of an up-sampling of the feature map followed by a 2x2 convolution (“Transposed-convolution”) that halves the number of feature channels, a concatenation with the correspondingly feature map from the contracting path, and two 3x3 convolutions, each followed by a ReLU. At the final layer a 1x1 convolution is used to map each 64- component feature vector to the desired number of classes. In total the network has 23 convolutional layers. The network architecture is shown in the figure.

<img width="668" alt="image" src="https://user-images.githubusercontent.com/75456477/166508993-ec884a20-51bb-4874-b6fe-895021b6ad41.png">

## Code

1. Run DataGenerator.py includes image preprocessing 
2. Models.py as of now includes U-Net using tensorflow, without keras. This implementation runs faster on my local machine as keras models have a lot of background condition checks for every epoch. Which I am skipping here.
3. Finally run Train.py, this will stich the input image, ground truth mask and predicted mask respectively, save it on your local file path.

## Evaluation Metrics

● Combined Loss function to tackle Class imbalance

● Loss = 𝜆 x Tversky loss + (1 - 𝜆) x categorical cross entropy loss

● Lambda relative weighting parameter set to 0.75

● Dice Similarity Coefficient

● Intersection Over Union


## Results

<img width="668" alt="image" src="https://user-images.githubusercontent.com/75456477/166509904-123725aa-896c-4961-80f4-518d8eec70a3.png">



