+++
title = "Dataset"
description = "cdiscount.com Image Dataset"
weight = 20
draft = false
bref = ""
toc = false
+++

This page describes the dataset provided by cdiscount.com and the steps we took to strip down the dataset to better accomodate our limited hardware resources.

## Raw Data and Categories:

#### Data
The datasets were provided in BSON (Binary JSON) format. The training data consisted of a list of 7,069,896 dictionaries each representing a product. Each product consisted of a product identifier `product_id`, category identifier `category_id` and a list of about 1-4 images. A test dataset consisting of 1,768,182 products were also provided. However, it lacked the category identifier `category_id` that was required to validate the accuracy of our methods. Therefore, we disregarded the test dataset and instead used a split of the training dataset for validation purposes. 

**Multiple images of the same product:**

We noticed that only one among the provided images per product represented the face of the product, while others showed different sides (when provided). We only considered the first image for training and prediction, and disregarded the rest as they may induce errors. An example product and its multiple images are shown below.

![1](/img/33492-0.jpg)
![2](/img/33492-1.jpg)
![3](/img/33492-2.jpg)
![4](/img/33492-3.jpg)

#### Categories:

Every top-level category consists of two levels of subcategories, thus establishing a hierarchical category structure. There are 49 total top-level categories and each top-level category has varying number, ranging from 1 to 555, of level-2 subcategories and each level-2 has varying number (about 1-44) of level-3 subcategories.

Each category identifier `category_id` maps to a level-3 category. Specifically, a `category_id` is a combination of level-1, level-2 and level-3 categories. A CSV file mapping `category_id` to the hierarchical category names were also provided. Due to the nature of our approach, this file was crucial in performing the data extractions as outlined below.


## Subset Extraction

Given the huge size of the dataset and our limited hardware resources, we extracted a subset of the data to feasibly train of our models. We also considered only one level of the category hierarchy.

### Tiny dataset (DS<sub>A</sub>)

This dataset consists of only one top-level category and all its subcategories. The top-level category was *EPICIERE* (Grocery). This dataset consists of 19556 images spanning 9 level-2 categories. We did not distinguish among level-3 categories.

### 100MB dataset (DS<sub>B</sub>)

This dataset was constructed by extracting 100MB worth of data from each of the top-level categories. In this case, we did not distinguish among level-2 and level-3 categories. In other words, we mapped a product to its top-level category only. There were cases where a given top-level category consisted of fewer than 100MB worth of images. We disregarded these undersized categories to maintain uniformity.

### 50k dataset (DS<sub>C</sub>)

This dataset consists of 50,000 images from each of the top-level categories. Similar to last dataset, we only mapped a product to its top-level category. Moreover, we also disregarded any undersized categories (with < 50k images) to maintain uniformity. This yielded us 27 categories.


