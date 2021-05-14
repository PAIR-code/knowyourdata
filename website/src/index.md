---
title: Know Your Data
layout: layouts/main.liquid
---

{% include partials/display1 text:"Know Your Data helps researchers, engineers, product teams, and decision makers **understand datasets** with the goal of **improving data quality**, and  helping **mitigate fairness and bias issues.**" %}

<div class="main-page-demo-button">
{% include partials/home-cta-button text:"Explore Know Your Data" link:"https://knowyourdata-tfds.withgoogle.com/" %}
</div>

{% include partials/spacer height:60 %}

{% include partials/home-card title:"Explore 70+ ML datasets" description:"Interactively explore image datasets from the TensorFlow Datasets catalog" link:"https://knowyourdata-tfds.withgoogle.com" cta-text:"Try it on TensorFlow Datasets" video:"/assets/videos/explore-70-datasets.mp4" %}

{% include partials/home-card title:"Filter & group in real-time" description:"Facet by source labels, Cloud Vision annotations, sharpness & more" link:"https://knowyourdata-tfds.withgoogle.com/#tab=STATS&dataset=imagenet2012" cta-text:"Try it on the ImageNet dataset" video:"/assets/videos/filter-beaver.mp4" reverse:true %}

{% include partials/home-card title:"Find fairness and bias issues by comparing features" description:"See how labels correlate with protected entities" link:"https://knowyourdata-tfds.withgoogle.com/#dataset=coco_captions&tab=RELATIONS&relations=kyd%2Fcoco_captions%2Fcaptions_words_gendered,kyd%2Fcloud_vision%2Flabel&draw=kyd/coco_captions/objects_label,bbox,bbox" cta-text:"Try it on the Coco Captions dataset" video:"/assets/videos/relations-gender-cloud-vision.mp4" %}

<div class="main-page-stay-updated">

### Stay updated

Know Your Data is **under active development** as we continue to expand our offerings. Our **beta version** visualizes image datasets from the TensorFlow catalog. Sign up to stay in the loop.

<div class="main-page-mailing-list">
{% include partials/home-cta-button text:"Join the mailing list" link:"https://groups.google.com/g/knowyourdata-announce" %}
</div>

</div>

{% include partials/spacer height:50 %}
