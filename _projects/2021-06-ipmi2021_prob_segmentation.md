---
layout: page
title: Is segmentation uncertainty useful?
description: A critical view on multiple common probabilistic models.
img: assets/img/uncertainty_thumbnail.png
category: research
date: 2021-06-01
---

<div class="profile float-right">
    {% responsive_image_block %}
        path: assets/img/uncertainty_thumbnail.png
        class: "img-fluid z-depth-1 rounded"
    {% endresponsive_image_block %}
    <div class="caption">
        Probabilistic segmentation models allow us to sample from a distribution of segmentations!
    </div>
</div>

Probabilistic image segmentation models provide a distribution of likely segmentation masks. Various characteristics of the distribution can be used to assess the prediction confidence of the model. Find the paper [here](https://arxiv.org/abs/2103.16265v1) and the code on [Github](https://github.com/SteffenCzolbe/probabilistic_segmentation).

### Models

We investigate four common models used to predict segmentation uncertainty:

- A simple U-Net with a softmax-output layer.
- An ensemble of U-Nets.
- MC-Dropout, a method that approximates Bayesian weight distributions.
- Probabilistic U-Net, a fusion between a VAE and a U-Net.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/uncertainty_models.png title: "Schematic overview of the evaluated models" class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Schematic overview of the evaluated models. Blue: residual blocks. Orange: Dropout layers essential to the networks’ functionality.
</div>

### Results

We evaluate the models on two datasets: (1) Skin leision segmentation and (2) Lung cancer segmentation. We see, that all models are relatively certain on correct predictions (TP + TN), and less certain on wrong predictions (FP + FN). Outliers are the MC-dropout model, which seems to be never completely certain in our case (possibly due to bad calibration), and TPs on the lung cancer dataset. The Lung cancer dataset has a large class imbalance, with very little cancer cells. This might explain my models are reluctant to be overly confident on detected cancer cells.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/uncertainty_results.png title: "Schematic overview of the evaluated models" class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    All models are relatively certain on correct predictions (TP + TN), and less certain on wrong predictions (FP + FN).
</div>

Separating model performance by whether different human annotators fully agree, somewhat agree, or completely disagree shows very little difference between models: All models are certain when the humans agree, and uncertain when humans disagree.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/uncertainty_results2.png title: "Schematic overview of the evaluated models" class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Model agreement with expert annotators, and generalized energy distance of the model output distribution to tthe distribution sampled from four human annotators. The models look very similar here.
</div>

### Active learning

Finally, we try to use the uncertainty estimations: In an active learning setting, we try to develop a "smart" strategy on what samples to include into the dataset next. This can inform annotation strategies and lower annotation cost. We trial an uncertainty-sampling strategy against random sampling. In most cases, the model with the random strategy performs better.

Investigating the samples selected by the uncertainty-based strategy reveals that the model frequently chose to include samples where even the group of expert annotators provided disagreeing segmentation masks, providing little information for the model to learn from.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/uncertainty_active_learning.png title: "Schematic overview of the evaluated models" class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Learning curves for the four algorithms on both datasets, using uncertainty-based sampling and random-based sampling. The random strategy performs better.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/uncertainty_active_learning_issue.png title: "Schematic overview of the evaluated models" class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    An example of the ambiguous samples frequently selected for inclusion into the training set under the uncertainty-based data gathering strategy. This unseen sample was selected when 150 annotations were revealed. The group of expert annotators provided disagreeing segmentation masks, confirming the model uncertainty but providing little additional information to learn from.
</div>

### Conclusion

Is segmentation uncertainty useful? We find that uncertainty,
even in the simplest models, reliably gives practitioners an indication of areas of an image that might be ambiguous, or wrongly segmented. Using uncertainty estimates to reduce the annotation load has proven challenging, with no significant advantage over a random strategy.
