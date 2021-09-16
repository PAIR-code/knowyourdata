---
title: KYD - Documentation
layout: layouts/sub.liquid

hero-height: 100
hero-image: /assets/images/LIT_FAQs_Banner.png
hero-title: 'Documentation'

sub-nav: '<a href="#introduction">Introduction</a><a href="#ui-overview">UI Overview</a><a href="#datasets">Datasets tab</a><a href="#stats">Stats tab</a><a href="#item-browser">Item browser</a><a href="#item-tab">Item tab</a><a href="#relations">Relations</a>'
color: '#000'
---

<div class="kyd-docs-page mdl-cell--8-col mdl-cell--8-col-tablet mdl-cell--4-col-phone">

<a name="introduction"></a>
## Introduction

Know Your Data is a tool to help researchers, engineers, product teams and
policy teams explore datasets, improve data quality and mitigate bias issues.

KYD aims to answer the following questions:

- Is my data corrupted? (e.g. broken images, garbled text, bad labels, etc).
- Is my data sensitive? (e.g. are there humans, explicit content).
- Does my data have gaps? (e.g. lack of daylight photos).
- Is my dataset balanced across various attributes?

{% include partials/info-box title: 'NOTE', text: "The initial external release of Know Your Data supports image datasets
supported by the TensorFlow Datasets API. We plan to support text and tabular
datasets soon."S %}

<a name="ui-overview"></a>
## UI Overview

The UI is organized in tabs.

![The header bar]({% root %}/assets/images/kyd-header.png 'The header bar')

The header shows the different tabs:

- _Datasets_ – A list of all the datasets that are visualized by Know Your
  Data
- _Stats_ – Global statistics of the features for a given dataset
- _Item_ – Metadata associated with an individual item in the dataset
- _Relations_ – Correlations between two different features

The header also shows the currently selected dataset name, as well as links on
the right hand side to dataset information, feedback form, and this
documentation.

The main panel (anything below the header) splits into two vertical sections:

- The left side shows the contents of the currently selected tab.
- The right side shows the Item Browser, an infinitely scrollable list of the
  currently selected items.

<a name="datasets"></a>
## Datasets tab

The _Datasets_ tab shows a list of all the datasets that are currently available
in Know Your Data, along with a few sample thumbnails and the dataset size.

<a name="stats"></a>
## Stats tab

The _Stats_ tab shows histograms of all the source features (also referred to as
ground-truth features) in the dataset. In addition to those, Know Your Data also
augments the dataset with _derived_ features such as:

- [Cloud Vision Label Detection](https://cloud.google.com/vision/docs/labels)
- [Cloud Vision face detection](https://cloud.google.com/vision/docs/detecting-faces)
- Generic image properties such as brightness, sharpness, resolution, format,
  aspect ratio, etc
- EXIF metadata

The main goal of the Stats tab is to give a quick overview of the distribution
of feature values and to allow the user to filter the data and explore subsets.

Clicking on a specific histogram bar applies a filter for that value on the
dataset. When a filter is applied, all other histograms, as well as the Item
Browser, react to that filter. Multiple filters can be chained together.

<video class="animation" loop autoplay muted playsinline>
  <source src="{% root %}/assets/videos/stats.mp4" type="video/mp4">
</video>

The same action can be achieved by clicking the “Add Filter” button.

<img src="{% root %}/assets/images/kyd-add-filter-button.png" title="Add filter button" alt="Add filter button" width="600">

<a name="item-browser"></a>
## Item browser

The _Item Browser_ located on the right side is an infinitely scrollable list of
item thumbnails.

The control bar located at the top of the item browser allows you to do various
queries on the dataset.

{% include partials/video-with-description 
  url:"/assets/videos/select.mp4" description:"Select and show metadata" %}

{% include partials/video-with-description 
  url:"/assets/videos/draw.mp4" description:"Draw annotations" %}

{% include partials/video-with-description 
  url:"/assets/videos/groupby.mp4" description:"Group items that share the same feature" %}

{% include partials/video-with-description 
  url:"/assets/videos/sort.mp4" description:"Sort the results by a feature value" %}

{% include partials/tip title: 'One of the derived features in Know Your Data is **similarity→cluster**,
which groups visually similar images together.' %}

<video class='animation' loop autoplay muted playsinline>
<source src='{% root %}/assets/videos/groupby-cluster.mp4' type='video/mp4'>
</video>

<a name="item-tab"></a>
## Item tab

The _Item_ tab shows all (source & derived) features associated with a specific
item in the dataset. Clicking on a thumbnail in the item browser switches you to
the Item tab and shows the metadata associated with that item.

<video class="animation" loop autoplay muted playsinline>
  <source src="{% root %}/assets/videos/item.mp4" type="video/mp4">
</video>

<a name="relations"></a>
## Relations

In addition to browsing individual signals, KYD allows you to explore the
_relation_ between two different signals. For example, we can measure the
correlation between
[`Cloud Vision Labels`](https://cloud.google.com/vision/docs/labels) and
`caption_words_gendered` in the
[Coco Captions](https://www.tensorflow.org/datasets/catalog/coco_captions)
dataset.

There are two ways to open to the Relations table:

{% include partials/video-with-description 
  url:"/assets/videos/open-relations1.mp4" description:"Using the menu in the stats card" %}

{% include partials/video-with-description 
  url:"/assets/videos/open-relations2.mp4" description:"Selecting features in the Relations tab" %}

Each cell indicates either a positive (blue color) or negative (orange color)
correlation between two specific signal values along with the _strength_ of that
correlation. The metric we use is inspired by the research of
[Aka et al., AIES '21](https://dl.acm.org/doi/pdf/10.1145/3461702.3462557) and is closely related to the
[PMI](https://en.wikipedia.org/wiki/Pointwise_mutual_information) metric that
tells us if two different feature values co-occur less or more than chance.

To explain the values in the table, let's hover over a specific cell:

<img src="{% root %}/assets/images/relations_cell.png" title="A cell in the relations table">

Based on the color of this cell, we can see that this dataset lacks images with
the word `girl` in the caption and the label `Baseball park` from Cloud. In
particular, it shows:

- **1061** images with **Baseball park** (row counter).
- **4057** images with **girl** (column counter).
- **11** images with **Baseball park & girl**, but expected **112** by chance,
  which is **10.18X less** than expected.

The expected count is computed based on the global counts of `Baseball park` and
`girl` assuming no correlation between those signals.

### Sort Order & Searching

Since the table can have many rows (e.g. thousands for Cloud labels), the UI
shows the first 100 rows and provides a search box at the top of the page to
search for specific rows. The rows are automatically sorted by strongest
correlation in any of its cells.

The search box is useful for testing a specific hypothesis. For example, we can
search for images with the `Kitchen` label, which shows overrepresentation with
the word `woman` and underrepresentation with the word `man`:

<img src="{% root %}/assets/images/relations_search.png" title="Searching in the table">

### Interactive exploration

The Relations table is interactive. We can click on a row, a column, or a cell
and immediately see the images behind the derived correlation. For example, we
could click on the **Kitchen** row and see images that Cloud Vision labeled as
**Kitchen**, while visually inspecting for any correlation with perceived
gender. We can also click on the **Kitchen & man** cell to see images in that
intersection:

<video class="animation" loop autoplay muted playsinline>
  <source src="{% root %}/assets/videos/relations-cell-click.mp4" type="video/mp4">
</video>

### Statistically significant correlations

To avoid surfacing spurious correlations, KYD uses a 95% confidence interval and
computes a _conservatively adjusted_ correlation strength. We compute this by
taking the upper or lower 95% bound of the expected count, whichever one results
in a weaker correlation. The table does not show this number directly. Instead,
the adjusted correlation strength is used to color the cell and to sort the
rows. Therefore cells with strong correlations that are not statistically
significant won't be colored strongly, and their rows won't be ranked highly in
the table.

The example below showcases this where the **Computer desk & female** cell is
not colored blue because there was only 4 observed images, and the correlation
strength of **1.24x** is not statistically significant:

<img src="{% root %}/assets/images/relations_significance.png" title="Statistically insignificant row">


{% include partials/spacer height:60 %}