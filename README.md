#  Maize Single-Cell RNA Velocity Pipeline: In Silico Validation & Dynamic Modeling

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](Link_to_your_colab_notebook_here)
[![Python 3.x](https://img.shields.io/badge/python-3.x-blue.svg)](https://www.python.org/)
[![scVelo](https://img.shields.io/badge/scVelo-Dynamic_Modeling-success)](https://scvelo.readthedocs.io/)

## **Overview**
This repository hosts a complete, end-to-end computational pipeline for analyzing cellular dynamics in ***Zea mays* (Maize)** using single-cell RNA sequencing (scRNA-seq) data. 

Traditional scRNA-seq provides a static snapshot of gene expression. This project leverages **RNA Velocity**—analyzing the balance between unspliced (nascent) and spliced (mature) mRNAs—to model the future transcriptomic state of individual plant cells. By doing so, we map the directional flow of cellular differentiation and identify the key driver genes responsible for developmental transitions.

## **Key Features**
* **Automated Data Acquisition:** Fetches raw FASTQ reads and Maize reference genomes (Ensembl Plants) directly within the pipeline.
* **Efficient Quantification:** Utilizes `alevin-fry` for rapid, memory-efficient pseudoalignment and quantification of spliced/unspliced transcripts.
* **High-Dimensional Dynamics:** Computes cellular trajectories and projects them onto 2D UMAP embeddings using `scVelo` stream plots.
* **Driver Gene Discovery:** Quantifies dynamic velocity scores to computationally extract high-confidence candidate genes driving cellular lineage progression.

## **Technology Stack**
This workflow is built on a modern bioinformatics stack designed for speed and scalability:
* **[Alevin-fry](https://alevin-fry.readthedocs.io/):** Fast, memory-frugal quantification tool utilizing the USA (Unspliced-Spliced-Ambiguous) mode.
* **[Scanpy](https://scanpy.readthedocs.io/):** Comprehensive toolkit for scRNA-seq preprocessing, normalization, and quality control.
* **[scVelo](https://scvelo.readthedocs.io/):** State-of-the-art Python package for computing RNA velocity and latent time.
* **SRA-Toolkit:** For seamless retrieval of public single-cell datasets.

## **Pipeline Workflow**
1. **Environment Setup:** Containerized installation of all required system and Python dependencies.
2. **Alignment & Quantification:** Mapping reads against a splici-aware index to generate dual count matrices (Spliced vs. Unspliced).
3. **Data Preprocessing:** Quality control, cell normalization, log-transformation, and identification of highly variable genes.
4. **Velocity Inference:** Computing neighborhood moments and solving dynamical equations to generate the velocity graph.
5. **Visualization & Extraction:** Plotting UMAP streamlines and exporting the top dynamic driver genes (e.g., *Zm00001eb201010*, *Zm00001eb335660*) to a structured CSV for downstream biological validation.

## **Usage**
The easiest way to run and explore this pipeline is via Google Colab, which provides the necessary GPU/CPU resources without local hardware constraints.

1. Click the **Open in Colab** badge at the top of this README.
2. Ensure your Colab runtime is set to GPU (`Runtime` > `Change runtime type` > `Hardware accelerator` > `T4 GPU`).
3. Run the cells sequentially. 

## **Outputs**
Running the notebook will generate:
* **Visualizations:** UMAP plots overlaid with RNA velocity streamlines showing developmental directionality.
* **Data Tables:** `maize_driver_velocity_scores.csv` containing genes ranked by their average velocity scores.


