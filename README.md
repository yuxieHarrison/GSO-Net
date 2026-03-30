# GSO-Net

**GSO-Net** is a large-scale benchmark for visual **Standard Operating Procedure (SOP) understanding** under **sparse industrial polling**.

> GSO-Net studies SOP understanding in realistic industrial deployment, where procedural status must be inferred from incomplete observations and localized operational evidence rather than dense temporal continuity.

GSO-Net focuses on **petrochemical unloading scenarios** and is designed for **engineering-oriented industrial vision**. The benchmark evaluates whether current models can recover reliable procedural meaning from localized state evidence under practical constraints such as sparse polling, small critical targets, and long-tailed operational states.

---

## Overview

GSO-Net adopts a hierarchical annotation framework that links:

- **9 macroscopic procedural steps**
- **15 microscopic operational states**

It supports two benchmark tasks:

- **Task 1: Joint Step-State Detection**  
  The core task of GSO-Net. Models jointly detect microscopic operational states and macroscopic procedural steps.

- **Task 2: Frame-Level Step Classification**  
  A diagnostic reference task. Models classify macroscopic SOP steps from global visual evidence only, without explicit localized state grounding.

This design makes it possible to evaluate not only object perception, but also whether models can relate **localized operational evidence** to **procedural stage understanding** in practice.

---

## Highlights

- **Real industrial scenario:** petrochemical unloading under practical surveillance conditions  
- **Hierarchical labels:** 9 macro steps + 15 micro states  
- **Sparse-polling setting:** built for intermittent observation rather than dense continuous video  
- **Challenging factors:** tiny safety-critical cues, long-tailed operational states, cross-site variation, weather and illumination changes  
- **Engineering-oriented focus:** evaluates practical SOP monitoring under realistic deployment constraints  

---

## Dataset Scale

- **Total images:** 50,325
- **Stations:** 64
- **Bounding boxes:** 321,432
- **Training images:** 40,976
- **Validation images:** 9,349
- **Split protocol:** strict cross-site split

---

## Download

The dataset is available at:

- **Google Drive:**  
  https://drive.google.com/drive/folders/1_Rto6-QbdSzsyKairZmY_ImEaaVtPfdC?usp=drive_link

> We recommend downloading the dataset from Google Drive and following the directory structure below.

---

## Tasks

### Task 1: Joint Step-State Detection

Task 1 is the **core benchmark task**.  
Each detector predicts:

- **15 microscopic operational states**
- **9 macroscopic procedural steps**

This task evaluates whether a model can ground localized operational evidence and relate it to procedural stages within a unified benchmark setting.

### Task 2: Frame-Level Step Classification

Task 2 is a **diagnostic reference task**.  
Each classifier predicts one of the **9 macroscopic SOP steps** from the full image based on global visual evidence.

This task is intentionally weaker than Task 1 and is used to show the limitation of holistic classification without explicit localized state modeling.

---

## Why GSO-Net?

Existing industrial benchmarks mainly focus on anomaly detection, object presence, or dense procedural parsing.  
GSO-Net instead targets **hazardous SOP understanding under sparse industrial polling**, where:

- many decisive cues are **small and localized**
- operational states are **long-tailed**
- adjacent procedural stages may appear **globally similar**
- step boundaries often depend on **functional state transitions** rather than large scene changes

GSO-Net is therefore intended as both a **challenging benchmark** and a **diagnostic platform** for future research on fine-grained state perception, sparse temporal reasoning, visual state machines, and engineering-oriented industrial vision.

---

## Data Structure

A typical release is organized as follows:

```text
GSO-Net/
├── images/
│   ├── train/
│   └── val/
├── labels/
│   ├── train/
│   └── val/
├── annotations/
│   ├── instances_train2017.json
│   └── instances_val2017.json
├── splits/
├── README.md
└── LICENSE
