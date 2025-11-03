---
layout: page
title: DigiScan360
description: Competitive intelligence platform developed and pitched as a startup prototype at UPC's entrepreneurship initiative, integrating multiple data sources for actionable insights.
img: assets/img/digiscan_architecture.png
importance: 4
github: https://github.com/kamrulkonok/DigiScan360
technologies: PySpark, LLMs, Microsoft Fabric, Azure Data Factory, Power BI, GraphDB, SPARQL
---

## Overview

DigiScan360 is a visual competitive intelligence tool, developed and pitched as a startup initiative at Universitat Politècnica de Catalunya (UPC). The platform enables comprehensive analysis and insights through data collection, processing, and visualization from various sources including e-commerce platforms, expert reviews, and social media.

## Challenge

Businesses need comprehensive competitive intelligence to make data-driven decisions. The project aimed to integrate multiple data sources—e-commerce sites, expert reviews, and social media—into a unified platform that provides actionable insights through advanced analytics and visualization.

## Approach

Developed a multi-layered architecture that processes and analyzes data from diverse sources:

### Data Collection & Processing
- Collected data from Amazon, MediaMarkt, CNET, Facebook, and Twitter using custom scripts and notebooks
- Processed data using **PySpark** notebooks on Microsoft Fabric, performing preprocessing and enrichment
- Integrated sentiment analysis and text generation features into the data pipeline
- Stored processed data in Azure Blob Storage and Azure Data Factory for orchestration

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