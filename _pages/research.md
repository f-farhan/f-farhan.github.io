---
title: "Research"
description: "Research by Faisal Farhan on spatio-temporal remote photoplethysmography, camera-based physiological monitoring, and vascular perfusion mapping."
layout: gridlay
permalink: /research/
---

# Research

<style>
.research-project {
  display: flow-root;
  margin: 24px 0;
  padding: 20px;
  border-radius: 10px;
  background: rgba(127, 145, 165, 0.12);
}

.research-project__media {
  float: left;
  width: 36%;
  max-width: 440px;
  margin: 0 24px 16px 0;
}

.research-project__media video {
  display: block;
  width: 100%;
  height: auto;
  aspect-ratio: 16 / 9;
  border-radius: 8px;
  background: #ffffff;
}

.research-project__media figcaption {
  margin-top: 8px;
  font-size: 0.85em;
  line-height: 1.5;
  opacity: 0.8;
}

.research-project h2 {
  margin-top: 0;
  margin-bottom: 18px;
  font-size: 1.65em;
  line-height: 1.35;
}

.research-project p {
  margin-bottom: 16px;
  line-height: 1.75;
}

.research-project p:last-child {
  margin-bottom: 0;
}

@media (max-width: 767px) {
  .research-project {
    padding: 16px;
  }

  .research-project__media {
    float: none;
    width: 100%;
    max-width: none;
    margin: 0 0 20px;
  }

  .research-project h2 {
    font-size: 1.4em;
  }
}
</style>

<div class="research-project" markdown="0">

<figure class="research-project__media">
<video controls autoplay muted loop playsinline preload="metadata" aria-label="Animated illustration of spatio-temporal rPPG heatmaps" aria-describedby="strppg-video-caption">
<source src="{{ '/videos/strppg-demo.mp4' | relative_url }}" type="video/mp4">
Your browser does not support embedded video.
<a href="{{ '/videos/strppg-demo.mp4' | relative_url }}">Download the video.</a>
</video>
<figcaption id="strppg-video-caption">
Illustrative animation of ST-rPPG heatmaps. The animation does not represent recorded physiological changes.
</figcaption>
</figure>

<h2 id="strppg-title">Design and Validation of Multimodal Spatio Temporal-rPPG Acquisition Systems for Physiological measurements</h2>

<p>
During my master’s thesis, I investigated how camera-based systems can estimate heart rate and reveal spatial distributions of vascular perfusion without physical contact. My research focused on spatio-temporal remote photoplethysmography (ST-rPPG), examining how polarization, spectral filtering, and motion compensation affect perfusion map quality and heart rate estimation.
</p>

<p>
I used two acquisition setups: an RGB camera operating with and without cross-polarization, and a monochrome camera combined with spectral filters. To reduce motion artifacts, I implemented a motion compensation strategy that combined optical flow-based selection of stable video segments with temporal video stabilization. This allowed me to investigate the influence of both acquisition conditions and video processing on the resulting physiological signals. In a study involving 20 participants, I evaluated four rPPG algorithms: GREEN, CHROM, POS, and G-R under cross-polarized and non-polarized illumination. I assessed their performance using Absolute Error (AE), Signal Quality Index (SQI), and Signal-to-Noise Ratio (SNR) to determine their suitability for perfusion mapping. GREEN and G-R delivered the strongest overall results. With the monochrome setup, I tested nine spectral filters across three anatomical regions using the GREEN method. This investigation examined how wavelength selection influences spatial perfusion signal quality. Green, orange, and blue wavelengths produced the most promising results in terms of AE, SQI, and SNR, particularly in the palm region.
</p>



<p>
The spatial perfusion maps demonstrated the benefits of motion compensation, polarized illumination, and appropriate spectral filtering for non-contact vascular perfusion assessment. This research highlights how acquisition design and signal processing can work together to improve camera-based physiological monitoring.
</p>

</div>