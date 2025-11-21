---
title: A brief overview of high-content imaging
subject: Tutorial
subtitle: How imaging grounds drug treatment
short_title: Intro
authors:
  - name: Vipin Kumar
    affiliations:
      - Bioinformatics Core Facility, OUS
      - Highthroughput Chemical screening, NCMBM
    email: vipin.kumar@ncmbm.uio.no
license: CC-BY-4.0
keywords: high-content imaging, introduction, open-science
---

The inception of this project can be traced to a Science paper introducing the cell painting technology whose main aspects can be summarised as:

- **Morphology as a Comprehensive Readout of Cell State**
- **Sufficiency of High-Dimensional Features**
- **Utility of Profile Similarity for Biological Interpretation**
    - _Mechanism of Action (MoA) Equivalence_
- **Assay Robustness and Reproducibility**
- **Single-Cell Data Aggregation Simplifies Analysis**

Let us examine each of them in more details:

### 1. Morphology as a Comprehensive Readout of Cell State

The foundational assumption is that **cellular morphology—the visual appearance of cells and their components—is intricately linked to a cell's overall physiology, health, and function**.

- Cell Painting is a method of **morphological profiling** that aims to capture a cell’s phenotypic state and its response to diverse perturbations, effectively acting as an **unbiased source of quantitative information** about cell status.
- The approach relies on **hypothesis-free molecular cytology** to provide multidimensional single-cell phenotypic information. These are produced through Feature Extraction .
- It is assumed that by staining key organelles and components—specifically **DNA, cytoplasmic RNA, nucleoli, actin, Golgi apparatus, plasma membrane, endoplasmic reticulum, and mitochondria**—the assay captures sufficient morphological changes across these eight major cellular compartments to reflect the impact of compounds or genetic perturbations.

### 2. Sufficiency of High-Dimensional Features

The success of the assay assumes that **measuring a large set of quantitative morphological features** (e.g., size, shape, intensity distributions, and textures) transforms the raw image data into a robust, high-dimensional profile capable of supporting meaningful conclusions.

- This process yields a **high-dimensional dataset** that is analogous to transcriptional profiles or proteomic profiles.
- The premise is that the detailed pixel information, even details often **invisible to the human eye**, is sufficient to cluster samples effectively.
- Their analysis and accompanying processing relies on careful considerations for the Data Structure to leverage when representing the data and derived quantities.

### 3. Utility of Profile Similarity for Biological Interpretation

The subsequent analysis is based on the assumption that quantifiable similarities or differences between morphological profiles directly correlate with biologically relevant distinctions between the samples.

- **Mechanism of Action (MoA) Equivalence:** A key assumption for predicting MoA is that perturbations (e.g., small molecules) believed to share a MoA will produce **similar morphological profiles** and thus cluster together (measured by the _percent matching_ metric).
    - _Caveat:_ It is acknowledged that this assumption is not always perfect, as many compounds annotated as sharing a target often _do not_ produce similar morphological profiles.
- **Identification of Activity:** The method assumes that comparing a query compound's profile against profiles of compounds with known activity (or "landmark compounds") will enable the identification of its cellular effects, MoA, or toxicity profile.
- The actual interpretation of the data relies on Analytical pipelines downstream of the Feature Extraction, that facilitates the integration of the high-dimensional description of cell morphology

### 4. Assay Robustness and Reproducibility

The wide applicability of Cell Painting depends on the robustness and standardization of the underlying experimental protocol.

- **Reproducibility of Replicates:** It is assumed that wells subjected to **identical treatment conditions** should produce highly correlated morphological profiles (_percent replicating_ score), validating the stability of the assay against technical variations.
- **Tolerance to Variation:** Experience has shown that the Cell Painting assay is **remarkably robust**; minor modifications to the protocol or the use of different vendor dyes or various imaging systems generally yield consistently similar and high-quality results.
- These properties are in part endowed by the robust image processing workflows composed essentially of effective Illumination correction steps and accurate Segmentation of cells within the image data.

### 5. Single-Cell Data Aggregation Simplifies Analysis

A practical assumption relates to data aggregation during processing:

- **Well-level Aggregation:** Many high-throughput image-based profiling campaigns rely on **well plate averaging** (or median profiles), which summarizes the cell population with a single value per feature. This practice implicitly **assumes cell homogeneity** within the well, offering simplified interpretation and faster analysis. However, this simplification may also risk obscuring subtle differences or cellular heterogeneity.