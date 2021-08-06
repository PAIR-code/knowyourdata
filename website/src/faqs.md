---
title: KYD FAQs
layout: layouts/sub.liquid

hero-height: 100
hero-image: /assets/images/LIT_FAQs_Banner.png
hero-title: 'Frequently Asked Questions'

sub-nav: '<a href="https://github.com/pair-code/knowyourdata/issues/new" target="_blank">Ask a question</a>'
color: '#000'
---

<div class="mdl-cell--8-col mdl-cell--8-col-tablet mdl-cell--4-col-phone">

{% include partials/faq-element
f-title: "How does KYD work?",
f-copy: "

KYD allows users to explore the dataset by information that wasn’t originally in the dataset. The tool annotates the existing data using machine learning models like [Cloud Vision labels](https://cloud.google.com/vision/docs/labels), [Cloud Vision face detection](https://cloud.google.com/vision/docs/detecting-faces), and general [image quality metrics](https://en.wikipedia.org/wiki/Image_quality) (e.g. sharpness and brightness). We compute these annotations in an [Apache Beam](https://beam.apache.org/) pipeline. We then load the database in a web server to enable interactivity. The statistics are computed on the fly, each time you click.
" %}

{% include partials/faq-element
f-title: "Can I run Know Your Data on my own data?",
f-copy: "

Not yet. For now, we’re only serving Know Your Data for image-based datasets supported by the TensorFlow Datasets API.
" %}

{% include partials/faq-element
f-title: "Will KYD work for other types of data?",
f-copy: "

Yes. We are actively working on other modalities, including text datasets.
" %}

{% include partials/faq-element
f-title: "What about model analysis?",
f-copy: "

We are actively thinking about model analysis in KYD.
" %}

{% include partials/faq-element
f-title: "How do I report an issue?",
f-copy: "

For any bugs and feature requests related to the application, please [file a bug](https://github.com/pair-code/knowyourdata/issues/new). For any other questions, issues or concerns, email us at [knowyourdata-feedback@google.com](mailto:knowyourdata-feedback@google.com).
" %}

{% include partials/faq-element
f-title: "Will KYD add more signals?",
f-copy: "

KYD will continue to develop over time and we are very interested in making datasets more understandable by adding more signals. If you have a specific signal in mind, please [let us know](mailto:knowyourdata-feedback@google.com).
" %}

{% include partials/faq-element
f-title: "Why doesn’t KYD use automated signals for protected attributes (for example, perceived gender expression, age or skin tone)?",
f-copy: "

Although we are aware that signals on protected attributes can help tackle fairness issues in datasets, labeling individuals in datasets could lead to undesirable outcomes. We seek to avoid creating or reinforcing unfair bias and are looking into trusted responsible approaches to adding more signals before proceeding forward.
" %}

{% include partials/faq-element
f-title: "Why are not all of the datasets supported by the TFDS API enabled in KYD?",
f-copy: "

KYD features datasets with the appropriate licenses for us to serve them. We accept [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0), [MIT](https://en.wikipedia.org/wiki/MIT_License) and [Creative Commons](https://creativecommons.org/). If you don’t see a TFDS supported dataset enabled in KYD, it’s likely that it may not have one of these licenses. If you are a dataset author interested in visualizing your dataset in KYD, please [let us know](mailto:knowyourdata-feedback@google.com).
" %}

{% include partials/faq-element
f-title: "How can I learn more about the performance of KYD’s machine learning models?",
f-copy: "

A key design principle of KYD is to always show the underlying data points to earn user trust. In addition, we offer details on KYD’s machine learning (ML) models. To understand their overall performance and limitations you can look at the publicly available [model cards](https://modelcards.withgoogle.com/model-reports).
" %}

</div>
