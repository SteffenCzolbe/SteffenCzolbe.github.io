---
layout: page
title: Image Registration
description: Play around with image alignment algorithms! The correct alignment of images is at the core of many applications in photography, video, and medical imaging.
img: assets/img/registration_thumbnail.png
category: research
date: 2019-10-01
---

Image registration aligns two or more images of the same scene. A source image is placed into the coordinate system of a target image via geometric transformations. Image registration as a wide range of applications. For example, it is used in computer vision to stitch together multiple photographs to a panorama shot, or in medical imaging to align scans deformable body parts, such brain tissue in MRI scans.

This tool lets you experiment with different image registration algorithms. Just draw a source and a target image, and hit the align button!

> This tool lives on <a href="https://steffen-io.com/registration.html"> my old website</a> , as github pages does not allow me to do computationally heavy tasks (thanks crypto miners). Might break at any time.

<div class="row">
    <a href="https://steffen-io.com/registration.html">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/image_registration_tool.png title: "screenshot of the image registration tool" class: "img-fluid rounded z-depth-1" %}
    </div>
     </a>
</div>
<div class="caption">
    Check out the tool <a href="https://steffen-io.com/registration.html"> here </a> or by clicking the image.
</div>
