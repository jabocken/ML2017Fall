+++
title = "Overview of Models"
description = "A brief description of InceptionV3, InceptionResnetV2, and Xception"
weight = 2
draft = false
bref = ""
toc = false
+++

## InceptionV3

The “Inception” micro-architecture was first introduced by Szegedy et al. in their 2014 paper, Going Deeper with Convolutions:

{{< figure src="/img/imagenet_inception_module.png" title="The original Inception module used in GoogLeNet." >}}

The original incarnation of this architecture was called GoogLeNet, but subsequent manifestations have simply been called Inception vN where N refers to the version number put out by Google.

The Inception V3 architecture included in the Keras core comes from the later publication by Szegedy et al., Rethinking the Inception Architecture for Computer Vision (2015) which proposes updates to the inception module to further boost ImageNet classification accuracy.

In the paper Rethinking the Inception Architecture for Computer Vision, the authors proposed Inception-v2 and Inception-v3. In the Inception-v2, they introduced Factorization(factorize convolutions into smaller convolutions) and some minor change into Inception-v1. Note that we have factorized the traditional 7x7 convolution into three 3x3 convolutions. As for Inception-v3, it is a variant of Inception-v2 which adds BN-auxiliary. BN auxiliary refers to the version in which the fully connected layer of the auxiliary classifier is also-normalized, not just convolutions. We are refering to the model [Inception-v2 + BN auxiliary] as Inception-v3.

{{< figure src="/img/imagenet_inceptionv3_module.png" title="Inception V3" >}}


The weights for Inception V3 amount to 96MB.

## InceptionResnetV2

Inception-ResNet-v2 is a variation of Inception V3 model, and it is considerably deeper than the previous Inception V3. Below in the figure is an easier to read version of the same network where the repeated residual blocks have been compressed. Here, notice that the inception blocks have been simplified, containing fewer parallel towers than the previous Inception V3. The Inception-ResNet-v2 architecture is more accurate than previous state of the art models.

{{< figure src="/img/imagenet_inceptionresnetv2_schematic.png" title="Schematic of Inception-Resnet-V2" >}}

## Xception

Xception was proposed by none other than François Chollet himself, the creator and chief maintainer of the Keras library.

Xception is an extension of the Inception architecture which replaces the standard Inception modules with depthwise separable convolutions.

The original publication, Xception: Deep Learning with Depthwise Separable Convolutions can be found here.

{{< figure src="/img/imagenet_xception_flow.png" title="The Xception architecture." >}}

Xception sports the smallest weight serialization at only 91MB.


## References

- [Rethinking the Inception Architecture for Computer Vision](https://arxiv.org/pdf/1512.00567v1.pdf)
- [Inception-v4, Inception-ResNet and the Impact of Residual Connections on Learning](https://arxiv.org/abs/1602.07261)
- [Xception: Deep Learning with Depthwise Separable Convolutions](https://arxiv.org/abs/1610.02357)