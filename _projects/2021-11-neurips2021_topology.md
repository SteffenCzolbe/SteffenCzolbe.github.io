---
layout: page
title: Spot the difference
description: Can we detect when geometric alignment algorithms go crazy?
img: assets/img/topology_thumbnail.png
category: research
date: 2021-11-09
---

At NeurIPS 2021, we introduce the first unsupervised, learning based method for detecting changes in image topology. In additioan, we introduce the first dataset of manually annotated changes in topology, which allows us to significantly extend on the evaluation strategies employed in of previous work.

### The Problem

Alignment of distributions or images often assumes a common topology across the images, with undefined behaviour if this assumption is violated. Yet in practice, we are often especially interested in these cases where image topology is different or abnormal. For example in medical imaging, the patient we are inspecting is likely in treatment because their anatomy does not follow a 'standard', but is abnormal in some way - e.g. by a brain tumor.

Alignment and registration methods that can handle differing topologies exist, but require the prior annotation of the changes in topology - we aim to provide an unsupervised method to detect the changes in topology.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/topology_detection.png title: "Two neighboring image slices show a change in the topology of the cell. Our unsupervised method can detect the change." class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left+Center: Topological change between two neighboring image slices show a change in the topology of the cell. Right: Our unsupervised method can detect the change.
</div>

### Solution

We base our method on probabilistic registration models, using a VAE to give pixel-wise bounds on the likelihood of a diffeomorphic match. We extend prior work by re-defining the output distribution and eliminating hyperparameters in the prior. For validation, we introduce the first dataset with annotated topological changes to aid evaluation in this field, which has been relying on qualitative assessment of small sample sizes and proxy-tasks before.

### Results

The new method outperforms baselines from topological change detection and anomaly detection by a large margin, and competes with supervised models on one of the datasets.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/topology-cells.png title: "img" class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Topological differences detected by our method, cell dataset. Neighboring slices $$\mathbf{I}, \mathbf{J}$$ in rows 1 and 2. Heatmaps of the likelihood of topological differences detected with $$L_\text{sym}$$ in row 3. Heatmaps are overlayed on image $$\mathbf{J}$$ to ease comparison. Annotated topological differences used for evaluation outlined in red. Note that only a subset of topological anomalies present is annotated in our dataset.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/topology-brains.png title: "img" class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Topological differences detected by our method, brain dataset. Structurally normal brain $$\mathbf{I}$$ in column 1, brain with tumor $$\mathbf{J}$$ in column 2. Heatmaps of the likelihood of topological differences detected with $$L_\text{sym}$$ in columns 3, 4 . Likelihood of topological differences caused by the structural anomaly in columns 5, 6. Contour of the ground truth brain tumor in red. Heatmaps are overlayed on image J to ease comparison.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/topology-auc.png title: "img" class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
   Receiver operating characteristic curves (ROC) and area under the curve (AUC) for detecting topological changes on the cell and brain datasets. We test models of our method for unsupervised topological change detection, trained with a semantic loss function and the MSE in the reconstruction term, and compare against unsupervised baselines from image registration (Li and Wyatt, Jacobian Determinant) and unsupervised anomaly detection (An and Cho). For reference, we also include a supervised segmentation model, which has been trained on the ground truth annotations.
</div>
Code available on [Github](https://github.com/SteffenCzolbe/TopologicalChangeDetection).

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/MQ4GvM0up5c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
