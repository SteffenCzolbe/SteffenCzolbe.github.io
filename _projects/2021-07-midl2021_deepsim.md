---
layout: page
title: Semantic Similarity
description: Runner up for the best paper award at MIDL 2021
img: assets/img/deepsimreg_thumbnail.png
category: research
date: 2021-07-01
---

What do we want to align? Image registration tries to align components of images. This is typically frames as an optimization problem, where we find the optimal transformation $$\Phi^*$$ for an image pair $$\mathbf{I}, \mathbf{J}$$ as

$$
\Phi^* = min_{\Phi} D(\mathbf{I} \circ \Phi, \mathbf{J}) + R(\Phi) ,
$$

where $$R$$ is a regularizer on the transformation, and $$D$$ a similarity measure between the images.

Existing similarity metrics can be grouped into three categories:

- Keypoint-Based metrics, such as the target registration error. These metrics try to aligign prior-placed landmark correspondences, but are impractical in many applications as the manual annotation and matching of landmarks in time-consuming.
- Intensity-Based metrics, such as the mean squared error (MSE). These metrics aim to align the color-vlues of the pixels.
- Correlation based metrics, such as normalized cros correlation (NCC). These try to maximize local correlations in the images, buy in practice also merely align pixel intensities.

> The underlying assumption of intensity- and correlation-based metrics is that as long as the pixel intensities of both images are close to each other, the images are well aligned. We challenge this assumption. Image registration should align areas of similar semantic content. Pixel intensities are not always a good description of the semantic meaning of areas of the images.

We design a method based on deep feature representation of a dataset, and achieve higher registration accuracy and smoother transformation fields compared to intensity- and correlation -based metrics. See the whole method in the [video](https://www.youtube.com/watch?v=Hs9X3wSO774&ab_channel=Steffen), and take a look at the code on [Github](https://github.com/SteffenCzolbe/DeepSimRegistration).

<iframe width="560" height="315" src="https://www.youtube.com/embed/Hs9X3wSO774" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
