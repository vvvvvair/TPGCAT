# TPGCAT: Text Prior-Guided Cell Alignment with Transformer for Robust Table Structure Recognition

<p align="center">
  <b>Official implementation of TPGCAT</b><br>
  <i>Text Prior-Guided Cell Alignment with Transformer for Robust Table Structure Recognition</i><br>
  <b>Pattern Recognition, 2026</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Pattern%20Recognition-2026-blue" alt="Pattern Recognition 2026">
  <img src="https://img.shields.io/badge/Task-Table%20Structure%20Recognition-green" alt="Table Structure Recognition">
  <img src="https://img.shields.io/badge/Code-Coming%20Soon-orange" alt="Code Coming Soon">
</p>

> 🚧 **Release status:** We are organizing the code, pretrained models, data processing scripts, and the MixTable benchmark. They will be released progressively in this repository.


## Overview

Table Structure Recognition (TSR) aims to convert visually represented tables into machine-understandable structured data. A common detection-based paradigm first obtains spatial representations and then transforms them into logical table structures. However, existing approaches still face two major issues:

1. **Text-based methods** are sensitive to text position, missing text, and text wrapping. Their detected text regions may not be sufficiently aligned for direct logical inference, often requiring extra logical-relation prediction modules.
2. **Cell-based methods** directly detect table cells, but may produce insufficiently aligned cell regions because textual information is not fully exploited, leading to complicated post-processing.

We propose **TPGCAT (Text Prior-Guided Cell Alignment Transformer)**, a cascaded Transformer framework that combines the complementary advantages of text-region and cell-region modeling. TPGCAT uses textual information as a prior to guide aligned cell prediction and introduces explicit cell coordinate alignment supervision. The resulting aligned cells can be converted into logical table structures using a simple threshold-based inference procedure.

## Highlights

- **Text prior-guided cell prediction.**  
  A text region decoder first captures spatial layout and region-level semantics. Its predictions are then used as priors for the subsequent cell region decoder.

- **Cascaded decoding architecture.**  
  TPGCAT connects a text region decoder and a cell region decoder in cascade, enabling progressive refinement from textual regions to aligned table cells.

- **Cell Coordinate Alignment (CCA) loss.**  
  We explicitly constrain cells belonging to the same logical row or column to share consistent coordinates, significantly improving cell alignment robustness.

- **Logical structure reconstruction.**  
  The proposed **Threshold-based Logical Position inference (T-LogP)** directly converts aligned cell coordinates into start/end row and column indices without additional learned relation-prediction networks.

- **MixTable benchmark.**  
  We introduce a real-world generalization benchmark containing diverse table styles, domains, languages, and content types.


## MixTable Dataset

We introduce **MixTable**, a real-world benchmark designed to evaluate the generalization ability of table structure recognition models.

MixTable contains **2,000 table images** collected from diverse real-world sources, including academic papers, financial reports, and books. It covers fully wired, partially wired, and wireless tables, as well as challenging cases involving row/column spans, empty cells, diverse background styles, multilingual content, mathematical formulas, and chemical equations.

📦 **Dataset:** [Download MixTable](https://drive.google.com/file/d/1zmcWePyD0J9-4eMeqK0pB0YUJFKr8R0o/view?usp=drive_link)

## Acknowledgements

TPGCAT builds on ideas from the broader table-structure-recognition community. 

We thank the authors of the related open-source projects and benchmark datasets for making their work publicly available.


⭐ **If you find this project useful, please consider giving it a star!**