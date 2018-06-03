---
layout: post
title: Receptive field
---



Field(group of cells) to be processed from the input image for having better connectivity within neurons(cells) to activate the desired neuron for the desired purpose of the neural network. 

Each pixel/cell in the input image is connected to a local region/cells of specific volume and that is called receptive field. As seen in the below image (*convolution layer*) -receptive field (3x3x3)is the area fromwhich the neuron is formed. In Image(*Fully connected Layer*) entire 29x29x3 is a receptive field for the neuron.

![Image1](https://mblogthumb-phinf.pstatic.net/MjAxNzAzMTNfMzEg/MDAxNDg5NDAzMDU5Nzg2.ylr41aKgMXahg5jA-2uwubgpMuVIoabszMkZRFrkivwg.byXi7m54e2A5_Ssy3KD4AECmuK6pisWqBT4qSed1qQIg.PNG.rix962/Fig4.png?type=w2)

Usage of receptive field:
While applying convolution operation kernel strides through the input field/receptive field and forms a resultant feature map/output.In below image a 3x3 kernel is applied on 5x5 input with stride 1 operation to produce a feature map of 3x3 output.
![Image2](https://mlnotebook.github.io/img/CNN/convSobel.gif)

**Math view**
The pixel at the center forms the gravitational point of the image were entire perception of the recptive field lies.
![Image4](https://i.stack.imgur.com/GvsBA.jpg)

**Architecture Explanation**

Lets keep each cell/pixel from original image corresponds to each neuron .Specific group of neurons(recpetive field) are connected together to form a neuron of next layer.Only a subset of neurons/pixel of first layer is connected to form next layer neuron instead of connecting all the neurons.its like assuming a sevreal leader for a set of persons among a group and the leader tells how well their group members are performing.

Imagine a 600 pixel image if we are connecting all the neurons(600) of first layer to only a single neuron(1) it like 600 people having a single leader.Where as in 600 pixels successively each of 60 pixels is connected to 1 neuron, then there would be 10 neurons in the second layer and then these 10 neuron would be connected to a single neuron at third layer .Thus in the latter the leader/neuron at third layer could have a good control and overview over the 600 neuron/people.

Thus in deeper the network the neurons at final layer will have larger portion of image than the neurons at lower network.More the deeper, neurons could identify pattern from receptive field


![Original](https://distill.pub/2018/building-blocks/examples/input_images/chain.jpeg)  

Desired area can be focused with proper activation functions on feature maps.Final layers of the bird image is shown below.

![Final layer](https://distill.pub/2018/building-blocks/examples/activations/chain/mixed4d.jpeg)


You can see the neurons in final layers has abstract data of image litterally its like which part of image is our mind focusing when we are seeing an image.

Computing area of recptive field (bounding box) is also an important technique in computer vision which enables the network to detect the desired object faster .
![Traffic](https://cdn-images-1.medium.com/max/800/1*ntDmAV-hak6IqfxY2DtWiQ.png)

References:
1. [The Building Blocks of Interpretability](https://distill.pub/2018/building-blocks/)
2.  [Feature Visualization](https://distill.pub/2017/feature-visualization/)
