---
layout: page
title: DigiScan360 — End-to-End Data & Semantic Intelligence for Competitive Analysis
description: An end-to-end data and semantic intelligence system for scalable competitive analysis across heterogeneous market data.
img: assets/img/projects/digiscan360/digiscan360.jpg
importance: 2
year: 2024
semester: Spring 2024
github: https://github.com/kamrulkonok/DigiScan360
technologies: PySpark, LLMs, Microsoft Fabric, Azure Data Factory, Power BI, GraphDB, SPARQL
---

## Team

[Hareem Raza](https://github.com/hareemraza), [Md Kamrul Islam](https://github.com/kamrulkonok), [Muhammad Qasim Khan](https://github.com/QasimKhan5x), and [Narmina Mahmudova](https://github.com/nmahmudova)

## Overview

DigiScan360 is an end-to-end data and semantic intelligence system designed to address the challenges of competitive analysis in modern digital markets. Market-relevant information is inherently fragmented across e-commerce platforms, expert review websites, and social media, spanning structured records, semi-structured logs, and unstructured text. Traditional analytics pipelines—typically centered on relational models—are insufficient to integrate these sources holistically or to capture the complex relationships between products, brands, and consumer behavior.

This project unifies large-scale data ingestion, distributed processing, analytical modeling, and graph-based semantic representations within a single architecture. By combining lakehouse-based analytics with knowledge graph modeling and metadata-aware integration, DigiScan360 enables both quantitative analysis and relationship-driven reasoning over heterogeneous market data. The system is designed to be scalable, extensible, and reproducible, serving as a foundation for descriptive, predictive, and semantic analytics in competitive intelligence scenarios.

## Design Objectives

- **Integrate heterogeneous data** — Structured and unstructured data from multiple external sources
- **Preserve raw data fidelity** — Enable scalable, distributed transformations while maintaining data integrity
- **Enrich with semantic representations** — Analytical datasets augmented with graph-based and semantic models
- **Support multi-mode analytics** — Descriptive, predictive, and relational analytics from a shared data foundation
- **Enable extensibility** — Traceability and schema evolution through metadata-aware design

## System Architecture

DigiScan360 follows a layered, end-to-end architecture that integrates heterogeneous data ingestion, scalable storage, distributed processing, semantic modeling, and analytical exploitation. Data flows through progressively refined stages—from raw source data to analytical tables and semantic graphs—while preserving lineage and traceability.

The architecture intentionally combines a lakehouse-based analytical backbone with graph-based semantic representations. Relational models support scalable quantitative analysis, while knowledge graphs capture higher-order relationships between products, brands, and consumer behavior. This dual modeling strategy enables both traditional business intelligence and relationship-driven reasoning within a single system.

<figure class="figure mt-4 mb-4">
  <img src="{{ 'assets/img/projects/digiscan360/digiscan_architecture.png' | relative_url }}" alt="DigiScan360 system architecture" class="figure-img img-fluid rounded" loading="lazy" />
  <figcaption class="figure-caption text-center mt-2"><strong>Figure 1.</strong> DigiScan360 end-to-end pipeline from data sources through collection, storage, formatting, and exploitation.</figcaption>
</figure>

**Figure 1** illustrates the complete DigiScan360 pipeline from data sources to analytical and semantic exploitation. The following sections walk through each stage.

## Data Collection and Storage

### Data collection

Data is collected from **e-commerce platforms** (Amazon, MediaMarkt), **expert review websites** (CNET), and **social media** (Facebook, X/Twitter). As shown in the leftmost zones of Figure 1, source-specific Python collectors—`amazon_collector.py`, `mediamarkt_collector.py`, `cnet_collector.py`, `facebook_collector.py`, and `twitter_collector.py`—encapsulate extraction logic while producing standardized outputs. This design enables extensibility and isolates downstream processing from source-specific changes.

For platforms with restricted API access, synthetic datasets are generated based on official API specifications and augmented with noise and missing values to realistically simulate real-world conditions. All collection processes are logged and versioned to ensure reproducibility.

### Storage and landing design

The architecture employs a **two-stage landing strategy** (center of Figure 1):

- **Temporal Landing Zone:** Raw CSV and JSON files are stored in **Azure Blob Storage** in their original form via `azcs_uploader.py`. This preserves data fidelity and supports schema-on-read processing, auditing, and reprocessing.

- **Data Persistence Loader:** **Azure Data Factory** orchestrates the ingestion pipeline—copying validated data into the lakehouse and removing temporary files after successful ingestion.

- **Persistent Lakehouse:** **Microsoft Fabric** runs the ingestion pipeline hourly and stores data in a versioned lakehouse. This provides transactional guarantees and efficient analytical access, decoupling ingestion from downstream processing and enabling scalable transformations.

This separation decouples ingestion from downstream processing, enabling scalable transformations and long-term maintainability.

## Data Processing and Feature Engineering

After ingestion into the persistent lakehouse, data is processed using distributed workflows designed to clean, enrich, and align heterogeneous datasets for both analytical and semantic use. Processing is implemented using **Spark-based** transformations to ensure scalability across large volumes of structured and unstructured data.

### Data cleaning and integration

Raw datasets from e-commerce platforms, expert reviews, and social media are first normalized and integrated. This stage includes schema alignment, removal of duplicates, handling of missing values, and noise reduction in textual fields. Multiple e-commerce sources are merged into unified product representations, enabling consistent downstream analysis across brands and platforms.

### Feature engineering and representation learning

To enrich analytical value beyond basic aggregates, the system derives higher-level features from unstructured text:

- **Sentiment signals** are computed from review text to capture consumer perception.
- **Text embeddings** are generated for product descriptions to enable similarity-based analysis.
- **Product similarity features** are derived using vector-based nearest-neighbor search, supporting comparative and competitive analysis.

These features are materialized as versioned tables in the lakehouse, preserving lineage and enabling reuse across analytical and semantic layers.

### LLM-based semantic feature generation

In addition to statistical and embedding-based features, a controlled LLM-based enrichment workflow extracts qualitative semantic insights from reviews, such as **product and brand strengths and weaknesses**. LLM outputs are treated as structured features rather than standalone text.

The LLM pipeline is explicitly modeled as a BPMN process to ensure transparency, fault handling, and reproducibility. Generated semantic features are persisted in the lakehouse and subsequently copied to the **data warehouse**, making them available for both relational analytics and semantic modeling.

The LLM workflow is modeled explicitly as a **BPMN process** to ensure transparency, fault handling, and reproducibility. The process includes conditional execution paths to handle external API availability and local fallback execution, ensuring robustness within automated pipelines.

<figure class="figure mt-4 mb-4">
  <img src="{{ 'assets/img/projects/digiscan360/ecommerce-data-formatter.png' | relative_url }}" alt="LLM enrichment workflow for semantic feature generation" class="figure-img img-fluid rounded" loading="lazy" />
  <figcaption class="figure-caption text-center mt-2"><strong>Figure 2.</strong> BPMN-based LLM enrichment workflow used for semantic feature generation.</figcaption>
</figure>

## Formatting and Exploitation

The **Data Formatters** (Figure 1) integrate and clean datasets using **PySpark**, generate predictive features (sentiments, strengths, weaknesses) via **LLM**, and copy data to the warehouse. The **Formatted Zone** implements a star schema, **Neo4j** property graphs, and **GraphDB** knowledge graphs; **Power BI** provides descriptive analysis.

### Knowledge Graph & Property Graph
- Constructed a **Knowledge Graph** in GraphDB using **SPARQL** for advanced analytics
- Created local schemas and global schema for social media and e-commerce data using RDF
- Implemented **Property Graph** analysis with Cypher queries for product feature analysis
- Utilized **LAV mapping** to transfer RDF data from local repositories to a global repository

### Vector Search & LLM Integration
- Implemented product similarity search using **Pinecone** vector database for fast text similarity searches
- Leveraged **LLaMA-3** via Groq API for text generation, sentiment analysis, and insights extraction
- Generated summaries, extracted topics, and identified strengths/weaknesses at product and brand levels
- Optimized performance by using Groq API when available, falling back to local PySpark notebooks

### Data Warehouse & Visualization
- Built a **SQL Server**-based data warehouse with star-schema design for analytical queries
- Created **Power BI** dashboards for real-time, data-driven insights and visualization
- Developed views and stored procedures for efficient data access and analysis

## Key Results

Successfully created a comprehensive competitive intelligence platform that integrates multiple data sources, enabling businesses to gain actionable insights through knowledge graphs, advanced analytics, and interactive visualizations. The platform was pitched as a startup prototype at UPC's entrepreneurship initiative, demonstrating real-world applicability.

## Technologies

PySpark, LLMs, Microsoft Fabric, Azure Data Factory, Power BI, GraphDB, SPARQL