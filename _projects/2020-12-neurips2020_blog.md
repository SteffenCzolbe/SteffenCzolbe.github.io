---
layout: page
title: "Virtual conferences can be good ?!"
description: As the pandemic rages on, conferences turn virtual
img: assets/img/gathertown_thumbnail.png
category: research
date: 2020-12-12
---

2020 has been a strange year. With infectious zombies roaming the streets, we all have been forced to reduce our social contacts, stay indoors and work remotely. Large gatherings of people are cancelled around the world, from musical concerts, to sporting events like the olympics. The same applies for scientific conferences, usually used to share and disseminate the latest research, network with colleagues from around the world and indulge in good food and nice hotels.

But as there continues a need for overworked grad students to publish their annual round of papers in the name of progress (and to comply with their study program), these scientific conferences have been forced to move online. The prospect of _virtually_ presenting my research at one of the largest conferences in my field did not exactly fill me with joy. Social media is full of rants about how terrible the virtual conference experience is (Just as i'm writing this blog post, the top post over on /r/PhD is titled <a href='https://www.reddit.com/r/PhD/comments/kexx5z/virtual_conferences_are_bs_and_a_waste_of_time/'>“Virtual conferences are bs and a waste of time” </a>). I was prepared for the worst. But after looking back at NeurIPS 2020, I must say they really nailed the experience.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/gathertown.png title: "A Gathering in gather.town." class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A Gathering in gather.town.
</div>

## The virtual experience

The star of the show has been <a href='www.gather.town'>gather.town</a>, the game/software used to run the conference. Think minecraft or animal crossing, but with a 2d top-down 80s style pixel graphics. You move your character through the virtual conference halls, interact with the various posters, watch videos of presentations, and draw on virtual whiteboards arranged throughout the venue. As you approach other people, their web-cam view pops up at the top of the screen and you can have a conversation. As you see the other attendees busily walking around and talking to presenters, it's easy to get a sense of the scale of the conference. The crowds forming in front of some posters make it easy to identify interesting discussions.

The software allowed many of the human interactions you would have at a physical conference. The virtual garden offered space for many popular activities, like the Yoga session for beginners, or a hallway full of cute videos of kittens and pandas. Having to walk from one presentation to another among the virtual hallways allowed for plenty of smalltalk and networking opportunities. On one occasion I bumped into Adrian Dalca. After having worked intensely with some of his recent papers, I had plenty to discuss with Adrian. After some conversation, we both left with a chuckle as to how we just had a normal talk in the hallway of a conference - just virtually.

## Paper highlights

Throughout the conference I had in-depth discussions with various authors. While the big-shot names and keypoint addresses get quite some attention, I want to use this opportunity to highlight two works I found very interesting.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/neurips_papers.png title: "Left: multi-modal image registration via a joint representation. Right: Network for ambiguous predictions." class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: multi-modal image registration via a joint representation. Right: Network for ambiguous predictions.
</div>

<a href='https://arxiv.org/abs/2006.06325'>CoMIR: Contrastive Multimodal Image Representation for Registration</a>, presented by Nicolas Pielawski et al. is an elegant way to solve the multimodal image registration problem. In image registration, we want to align two images, so that their contents overlap. Think taking multiple aerial images from an airplane, which you now want to combine to create a map. The images overlap at the edges, allowing you to find good alignment. Many algorithms have been proposed to align images of the same modality, e.g. align an RGB image to another RGB image. Bur aligning images of different modalities, for example an RGB image to an infrared image, or a T1-weighted MRI scan to a T2-weighted one, requires some trickery. Over the last two years I've read multiple papers proposing quite complicated methods to solve this problem. None of them has been as elegant as what this paper proposes. They train a pair of U-net like networks to convert images of either modality into a common abstract representation. As training data, they require only a pair of manually aligned images. From there, they extract patches at random and use a contrastive loss to learn a common representation for the same patch, while ensuring the representations of non-aligned patches differ. To finish it all off, they add a rotational equivariance constraint to their loss function, to ensure the learned representation is invariant to rotation. Rotational invariance is of particular importance to registration problems, as the images might have to be rotated to find optimal alignment.
Overall outstanding work, and i will definitely try this approach the next time I work with multi-modal images.

Darya Trofimova combined two topics I spent a lot of time on recently to solve a quite cool applied problem in her paper <a href='https://arxiv.org/abs/2012.08195'>“Representing Ambiguity in Registration Problems with Conditional Invertible Neural Networks”</a>. They combine ambiguity and image registration to give a probability distribution over patient orientations. Pre-surgery, doctors often take 3D CT/MRI scans of the patients body. During surgery, a 2D X-ray of the patient is taken. We can register the 2D projection of the X-ray to the 3D image to learn about their orientation, but the result is often ambiguous, as the body is symmetric and X-rays taken from the front/back or left/right can not be distinguished. The paper uses multiple interesting techniques, such as combining the output of a registration C-NN with a gaussian prior and an invertible neural network to then allow sampling of orientation. The discussion I had with Darya also gave me lot's of insight into the difference between uncertainty (we are unsure about the presented solution) and ambiguity (there are multiple correct solutions), and the use of invertible neural networks for creating sample-able general distributions.

## The presenters perspective

Finally, I want to highlight my two works presented at NeurIPS. My main-conference paper, <a href='https://arxiv.org/abs/2006.15057'>“A Loss Function for Generative Neural Networks based on Watson's Perceptual Model”</a>, was well received. Prior to the conference discussion already popped up on the GitHub repository, and during the poster session we had many fruitful discussions with well prepared attendees. My workshop paper <a href='https://arxiv.org/abs/2011.05735'>“DeepSim: Semantic similarity metrics for learned image registration”</a> similarly sparked discussion among the medical imaging community, in the more tight-knit format of the satellite event. Both presentations entailed a pre-recoded video, which is up on my <a href='https://www.youtube.com/channel/UC2Icc-xKB7YKcvZGi40NCZw'>youtube-channel</a>, and the in-person poster session / Q&A in gather.town.
