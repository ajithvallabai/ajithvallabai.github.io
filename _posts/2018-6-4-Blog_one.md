---
layout: post
title: Feature map
---

Mapping of input image where a certain kind of feature is found .It's done by activation of outputs with a kernel/filter applied on input image with a certain receptive field. 
Feature map is also called as activation map.

You know what happened in the flim when Neo understands the enigneering/structure/entity of the matrix he was able to control them.

![Image1](https://i.gifer.com/3HeS.gif)

Basic feature mapping: Edge detection of image/vedio and Sharpenning of images/vedio:


![edges.PNG](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogone/edges.png) ![sharp.PNG](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogone/sharp.png)




**Math View**

Receptive field + kernel  ---> Activation --> Feature map

Kernel can be altered to produce the desired feature map after activation.Activation is nothing but considreing/theresholding the filtered input within 0 to 1 value.

![Feature mapping](https://cdn-images-1.medium.com/max/800/1*_34EtrgYk6cQxlJ2br51HQ.gif)

**Feature view**:

Naive view:

**Original Image with One feature**

![drawisland (4).png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogone/drawisland(4).png)![imagenine.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogone/imagenine.png)![drawisland (5).png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogone/drawisland(5).png)

*Feature maps of digit 1,2,3 are matrix Ek,matrix Tho,matrix Theen*

$$
\left[
\begin{array}{cc}
  0&0&0\\
  0&0&a\\
  0&0&a\\
  0&0&a\\
  0&0&0
\end{array}
\right]
-
\left[
\begin{array}{cc}
  a&a&a\\
  0&0&a\\
  a&a&a\\
  a&0&0\\
  a&a&a
\end{array}
\right]
-
\left[
\begin{array}{cc}
  a&a&a\\
  0&0&a\\
  a&a&a\\
  0&0&a\\
  a&a&a
\end{array}
\right]
$$

You can see that a matrix Ek can be identified as 1 with the presence of a in [1,2],[2,2],[3,2] similarly for matrix tuo, and for matrix theen.



**Original image with Two feature**

![drawisland (8).png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogone/drawisland(8).png) ![imagethree.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogone/imagethree.png) ![imagefour.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogone/imagefour.png) ![imagetwo.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogone/imagetwo.png)

Now transformming the digit 2 features in to matrixes 

![imageseven.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogone/imageseven.png)
![imagefive.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogone/imagefive.png)

$$
\left[
\begin{array}{cc}
  a&a&a\\
  0&0&0\\
  a&a&a\\
  0&0&0\\
  a&a&a
\end{array}
\right]+
\left[
\begin{array}{cc}
  0&0&0\\
  0&0&b\\
  0&0&0\\
  b&0&0\\
  0&0&0
\end{array}
\right]->
\left[
\begin{array}{cc}
  a&a&a\\
  0&0&b\\
  a&a&a\\
  b&0&0\\
  a&a&a
\end{array}
\right]
$$
*Feature map 1 of digit 2 + Feature map 2 of digit 2 --> Output 1*
$$
\left[
\begin{array}{cc}
  a&a&a\\
  0&0&0\\
  a&a&a\\
  0&0&0\\
  a&a&a
\end{array}
\right]+
\left[
\begin{array}{cc}
  0&0&0\\
  0&0&b\\
  0&0&0\\
  0&0&b\\
  0&0&0
\end{array}
\right]->
\left[
\begin{array}{cc}
  a&a&a\\
  0&0&b\\
  a&a&a\\
  0&0&b\\
  a&a&a
\end{array}
\right]
$$
*Feature map 1 of digit 3 + Feature map 2 of digit 3 --> Output 2*

Now with 1x1 convolution we can make the network to train such that by seeing two pixels/cells [2,0] and [2,2] the network could identify whther it is 1, 2 or 3 . and still if original image contains more features we can extract many feature maps for better network.

Think of one feature , two feature and four feature maps for calculator digits
More the features there are in original image --> more the deeper the network could go -->more the connectivity --> firing of neurons can be worth for it.
![imagenine.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogone/imagenine.png)  ![imagethree.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogone/imagethree.png) ![imageten.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogone/imageten.png)


Using the power of feature maps is provided by convolution

When you see an image its the features that make the image.Those features are the vision that you have sub consiously in neuron activation both in humans.

*Same way when the neural network and neurons that you design for a robot/machine  are able to map and differentiate features with the power of architecture they have, they can have the power to recongnise the inputs given to them .*

![Image6](https://i.pinimg.com/originals/18/ba/9f/18ba9fa5659f85c4462607397ad8c99a.gif)

So how he was able to do that 

![Image2](https://media0.giphy.com/media/V8iAE46YlM2FW/giphy.gif)

its the features that makes us to percieve

Though the brain of neo already was capable/capacity of controlling or viewing that environment ;only after the intellegince provieded by the child he was able to bend it. 

Intelligence is provided by activations of neurons that produces feature maps .

**Advanced view:**

Below is an image for salient object detection technique in deep learning you can see how the object to be detected is getting more prioratised in further layers by neglecting background. This is how the needed feature of image is processed/filtered in subsequent layers with corresponding regions beiing activated/mapped.

![Image](http://ars.els-cdn.com/content/image/1-s2.0-S0925231216314710-gr1.jpg)



**Mnist feature maps of early layer and final layers:**

This is a view of early layers where network is seeing the edges of the digit.This is similar to how rods and cones in our eyes to works

![layer1](http://everettsprojects.com/figs/2018-01-17-mnist-visualization/output_8_0.png)

You can see that at final layer network is able to identify common features in the given set of input images

![layer2](http://everettsprojects.com/figs/2018-01-17-mnist-visualization/output_18_0.png)


References & further readings:
1. [Image Kernels explained visually](http://setosa.io/ev/image-kernels/)
2.  [What Does my MNIST ConvNet Actually See?](http://everettsprojects.com/2018/01/17/mnist-visualization.html)
3.  https://www.sciencedirect.com/science/article/pii/S0925231216314710



