---
layout: post
title: 1x1 Convolution
---


**Reason for a filter like 1x1 convolution rather than 5x5 or 3x3**:
Cross channel/dimensional information provides deeper insight of input with a better receptive field for unique features.1x1 convolution also provides dimentionality reduction across multiple feature maps with less computation cost.

**Origin:**  [Network in network](https://arxiv.org/pdf/1312.4400v3.pdf) , [Inception Module](https://arxiv.org/pdf/1409.4842v1.pdf)

In 1x1 convolution input of all feature maps should be exactly in same dimension (Width and height) to provide exact same dimiension(height and width) transformed output.Thus enabling the transformation to take place among each of the feature maps.This provides cross channel information learnning to provide better receptive field  

### Architecture view

**Naive view**

Below you can see how two features maps can be transformed to one with 1x1 convolution 

![imagethree.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogtwo/imagethree.png)  ![imagefour.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogtwo/imagefour.png)

**Features of Digit 2 :**
Feature map 1 & Feature map 2
![imageseven.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogtwo/imageseven.png) ![imagefive.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogtwo/imagefive.png)

**Features of Digit 3:**
Feature map 1 & Feature map 2
![imageseven.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogtwo/imageseven.png) ![imagesix.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogtwo/imagesix.png)

Image representation :

![imagetwo.png](https://raw.githubusercontent.com/ajithvallabai/ajithvallabai.github.io/master/images/blogtwo/imagetwo.png)

Now transformming the features in to matrixes

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
*Feature map 1 of digit 2 + Feature map 2 of digit 2 --> Output 2*

**Thus 1x1 convolution makes the network(gives intelligence) to see that a single pixel at location (3,2) contains b or not .if b is present network will detect it as digit 2 if b is not present after transformation network will detect as 3**


From the simple view above you can see that while doing 1x1 convolution the kernel/filter doesnt care about the correlation of information in same feature map.Here each pixel of feature map 1 is compared with each pixel of feature map 2 and output is provided.


Similarly think of 4 feature maps

1x1 convolution enables us to focus on unique part in the input like difference between 2 and 3 

**Advanced view**

In below picture 10 feature maps of 32x32 image is transformed to 4 feature maps of 32x32 image

![image3](https://mlblr.com/images/1x1.jpg)


### Process of dimensionality reduction

50x 600x600 --> 50 x1x1 x20 --> 600x600 x20

50x 600x600 --> 1 channel of 600x600 image
50x 1x1x20  --> each of (50x 1x1 ) provides one output(600x600x1) --> so we get twenty outputs(600x600x20) 

### Math view
**Naive view:**

I have shown how 3 feature maps that are mapped to 1 feature maps
*I have shown how 3 feature maps of size 6x6(WXH) that were mapped to 1 feature maps of size 5x5(WxH)*
**Three feature maps**

$$ \left[
\begin{array}{cc}
  1&2&3&2&2&3\\
  4&5&6&2&2&3\\
  2&1&7&2&1&3\\
  3&2&4&2&2&3\\
  3&2&4&2&2&3\\
  3&2&4&2&2&3
\end{array}
\right]
\left[
\begin{array}{cc}
  3&2&4&3&2&2\\
  3&2&4&3&2&2\\
  1&2&3&3&2&2\\
  4&5&6&3&2&2\\
  3&2&4&3&2&2\\
  2&1&7&2&1&3
\end{array}
\right]$$
$$
\left[
\begin{array}{cc}
  1&2&3&3&2&2\\ 
  3&2&4&3&2&2\\
  3&2&4&3&2&2\\
   4&5&6&3&2&2\\
  3&2&4&3&2&2\\
  2&1&7&2&1&3
\end{array}
\right]$$


**1x1 kernel** of Depth 1

$$\left[
\begin{array}{cc}
  0.1\\  
\end{array}
\right]
\left[
\begin{array}{cc}
  0.2\\ 
\end{array}
\right]
\left[
\begin{array}{cc}
  0.4\\  
\end{array}
\right]$$


**Transformation**

$$3 *6*6    --> 3 *1*1   *1 --> 6*6* 1$$
$$C*W*H  --> C*W*H *K  --> W*H* K$$
C-- Channels
W--Width
H--Height
K--Number of desired output channel/number of filters/Number of depth size


**Output**
1 * 0.1 +3 * 0.2 + 1 * 0.4 = 1.1  for output T[0,0]
4 * 0.1 + 3 * 0.2 +3 * 0.4 = 2.2 for ouput T[1,0]

Matrix **output T** after 1x1 convolution:

 $$
\left[
\begin{array}{cc}
  1.1&1.4&2.3&2.0&1.4&1.5\\ 
  2.2&1.7&3.0&2.0&1.4&1.5\\
  1.6&1.3&2.9&2.0&1.3&1.5\\
   2.7&3.2&4.0&2.0&1.4&1.5\\
  2.1&1.4&2.8&2.0&1.4&1.5\\
  1.5&0.8&0.6&1.4&0.8&2.1
\end{array}
\right]$$


### Depth criteria:

By increasing number of 1x1 filters in parallel with channel we can increase the depth of convolution  so deeper the network deeper the network could percieve.
**Depth 1** 

![Image 0](https://qph.ec.quoracdn.net/main-qimg-013c5e1bac766f3e1bbe655c9a460a5e)

**Depth 2**

![Image1 ](https://qph.ec.quoracdn.net/main-qimg-0b3c4bbc86cc5c73efb8dbf2c699265a)

**Depth 3**

![Image 2](https://qph.ec.quoracdn.net/main-qimg-80ebcfc916a3016013b14e258c82daaa)

Fully connected layers provided overfitting so to reduce them dropout were used but it lead to information loss moreover adantages of unique feature extraction in 1x1 was lacking in early FC layers .

### References and further readings: 


1. [ML & AI](https://mlblr.com/includes/mlai/index.html#1x1-convolutions)
2. [One by One [ 1 x 1 ] Convolution - counter-intuitively usefu
l – Aaditya Prakash (Adi) – Random musings of a deep learning grad student](http://iamaaditya.github.io/2016/03/one-by-one-convolution/)
3. [1x1 Convolutions - Why use them? : MachineLearning](https://www.reddit.com/r/MachineLearning/comments/3oln72/1x1_convolutions_why_use_them/)
