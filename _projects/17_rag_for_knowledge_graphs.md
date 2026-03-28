---
layout: project_research
title: Applying Knowledge Graphs in Retrieval-Augmented Generation (RAG)
description: Presented at the Twelfth European Big Data Management & Analytics Summer School (eBISS 2024), University of Padova, Italy (July 2024); this work reviews KG-RAG architectures, applications, and open challenges.
img: assets/img/publication_preview/graphrag/GraphRag.jpg
# teaser_image: assets/img/publication_preview/graphrag/GraphRag.jpg
# teaser_caption: "Poster presentation at eBISS 2024, University of Padova, Italy."
year: 2024
semester: Summer 2024
time_order: 20242
research: true
importance: 2
permalink: /research-work/17_rag_for_knowledge_graphs/
authors_list:
  - name: Md Kamrul Islam
    url: https://kamrulkonok.github.io/
  - name: David Garcia Morillo
    url: https://davichete.me/
authors_affiliation: "¹ Universitat Politécnica de Catalunya, Spain"
paper_url: https://zenodo.org/records/17494287
poster_url: https://drive.google.com/file/d/1O6SWY3PyLf2xfbrDDrASmFUANt7EXyWG/view?usp=sharing
nav_hide_motivation_dataset: true
abstract: "This work reviews Retrieval-Augmented Generation (RAG) in the context of Knowledge Graphs (KGs), with emphasis on how graph-structured retrieval improves grounding, factuality, and coverage in LLM-based question answering and decision support systems. The review synthesizes architectural patterns, retrieval strategies, and application trends, and highlights practical limitations such as graph incompleteness, temporal drift, retrieval latency, and evaluation inconsistency across domains."
tldr:
  - "Systematic review of how RAG pipelines leverage knowledge graphs for grounded generation and question answering."
  - "Compares core design choices: graph indexing, retrieval strategy, and generator conditioning."
  - "Highlights open issues in scalability, freshness, and evaluation for real-world deployment."
contributions:
  - "Provide a structured overview of RAG-for-KG architectures and retrieval-generation workflows."
  - "Summarize cross-domain evidence (e.g., healthcare, finance, education) and practical benefits."
  - "Identify key research gaps and future directions for reliable KG-grounded generation."
technologies: Large Language Models, Retrieval-Augmented Generation, Knowledge Graphs, Question Answering
---

### Research problem and motivation {#research-problem}

Large language models can generate fluent responses, but they are still vulnerable to factual errors when relying only on parametric memory. Knowledge graphs provide explicit, structured, and semantically rich knowledge, while retrieval-augmented generation provides a mechanism to ground generation in external evidence.

This review addresses a central question: how can RAG pipelines best exploit graph-structured knowledge to improve factuality, controllability, and domain adaptability?

### Methodology and analysis protocol {#method}

The paper follows a literature-review methodology focused on RAG and KG integration patterns. The analysis groups prior work into recurring design choices:

- **Knowledge representation layer:** RDF and property-graph settings, ontology usage, and schema design.
- **Retrieval layer:** entity-centric, path-based, and hybrid retrievers for selecting relevant graph context.
- **Generation layer:** conditioning strategies that inject retrieved graph evidence into LLM prompts and decoding.
- **Application setting:** task objectives and constraints across domains such as healthcare, education, and finance.

The review also examines practical trade-offs involving graph quality, retrieval latency, and model robustness.

### Results and discussion {#results}

The review finds that KG-aware retrieval can substantially improve grounding and response reliability compared with generation-only baselines, especially for multi-hop and relation-sensitive queries.

Key observations include:

- Graph-aware retrieval improves traceability by connecting generated statements to explicit entities and relations.
- Hybrid retrieval strategies (symbolic + neural) are often more robust than single-strategy pipelines.
- Performance remains sensitive to graph completeness, update frequency, and retrieval quality.
- Evaluation standards are still fragmented, making cross-paper comparison difficult.

### Limitations and future work {#future-work}

#### Limitations

- Most reported systems are evaluated in constrained settings with limited benchmark standardization.
- Real-time graph updates and temporal consistency are under-addressed in many pipelines.
- End-to-end latency and cost can be high when retrieval and generation are both complex.

#### Future work

- Build stronger evaluation protocols for factual grounding, faithfulness, and explainability.
- Improve dynamic KG synchronization for time-sensitive domains.
- Develop efficient retrieval-generation co-design for scalable, production-grade KG-RAG systems.
