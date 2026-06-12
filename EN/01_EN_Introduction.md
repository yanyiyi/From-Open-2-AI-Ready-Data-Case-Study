---
title: "Chapter 1: Introduction"
tags: [AI-Ready 開放資料, 開放科技]

---

# Chapter 1: Introduction

[![hackmd-github-sync-badge](https://hackmd.io/XvNPhgwOT4mBtd7oMh8opQ/badge)](https://hackmd.io/XvNPhgwOT4mBtd7oMh8opQ)

_Source: OCF-AI-en.pdf, pp. 7-9._

## Figures

![English AI-ready open data FAQ graphic](https://raw.githubusercontent.com/yanyiyi/From-Open-2-AI-Ready-Data-Case-Study/main/assets/en-ch1-ai-ready-faq.png "英文版 AI-ready open data FAQ graphic")

This report aims to introduce the concept of AI-ready data, assess its contributions to innovation and democratic governance, explore how it can be achieved, and examine how it is being practiced in countries around the world.

By synthesizing these international experiences, the study provides a framework of regulatory and practical approaches to facilitate the creation of high-quality, AI-ready data. It also demonstrates to public sector officials that producing AI-ready data can often be integrated into existing open data workflows and, in many cases, may not require proprietary software. However, resourcing and staffing needs will vary by dataset and agency. In many cases, the main changes involve selecting appropriate formats and documenting update and temporal metadata, such as update frequency.

In order to encourage public agencies in different countries to proactively disseminate high-quality data and increase the global volume of cross-cultural and cross-national AI-ready data, thereby fostering cultural diversity and enriching human civilization-this study discusses which types of open data can be utilized within AI systems in a lawful and compliant manner, consistent with prevailing legal and regulatory frameworks.

At the same time, for those involved in civic technology or open-source communities, this study also serves as a technical resource for engagement and advocacy with government authorities. By examining public-private collaboration processes around AI-ready data in different countries, readers may draw on the experiences, tools, and modes of cooperation introduced in this research to support future policy dialogue and practical implementation.

## 1.1 Why This Case Study Is Needed

Since 2022, AI technologies have developed rapidly, and large language models (LLMs) have shown a continuously growing demand for training data. Due to their public nature and clear licensing, government open data has long been an important source for AI training. At the same time, countries around the world regard AI as a key driver of competitiveness, creating a synergistic ecosystem between open data initiatives and AI development.

However, the structure and formats of existing open data do not necessarily fully align with the requirements of AI training and applications. Optimizing data release standards to meet AI structural requirements and streamline training pipelines has therefore become a priority for governments and public-sector decision-makers. This study examines international case studies to identify feasible approaches for upgrading existing open data into AI-ready data.

### 1.1.1 How Traditional Open Data Can Be Made AI-Usable

When comparing AI-ready data with traditional government open data, and taking the one-star level of Tim Berners-Lee’s (2006) 5-star Open Data rating system as a baseline, it becomes clear that both are fundamentally grounded in “open” licensing. However, because different AI systems have different training requirements, they require data in different formats, particularly formats and specifications that differ from those commonly found in basic open data [1]. Taking large language model (LLM) training as an example, most datasets released by government agencies on Taiwan’s open data platform have historically been provided in CSV format. Yet, because many field names and metadata are inconsistently defined or under-specified, this often leads to semantic ambiguity when models interpret the data during training. By contrast, the Markdown (MD) format, which is often referred to as the “native language” of LLMs, facilitates the structured processing of extensive textual corpora, such as reports and official documentation.

Despite its efficiency, MD has not yet been widely adopted by government agencies in Taiwan. Similarly, although producing four- and five-star open data poses a higher threshold for public institutions, the defining features of these higher-rated data formats, such as persistent URIs and semantically linked data networks provide critical technical foundations for the development of scalable AI-driven applications.

The same principle applies to multimodal AI. Images, audio, geospatial information, and other multimedia content are also essential for developing sovereign AI that can embody richer cultural contexts. In this regard, the construction of high-quality metadata is a core component of sovereign AI development. In the past, many valuable cultural, historical, or governmental report materials in Taiwan were preserved primarily in PDF format. To comply with open data regulations, public agencies have often sought to convert these files into other machine-readable formats. However, layout-driven design elements, such as embedded non-machine-readable images, mixed tables, and multi-column layouts can make automated interpretation difficult. In recent years, advances in AI technologies, open-source tools for optical character recognition (OCR) and automated layout analysis have made it more feasible to integrate these digital assets into training pipelines. If these efforts are further complemented by more robust metadata, specifically through the precise annotation of document hierarchies and tables of contents, the accuracy of automated parsing can be significantly improved, thereby enhancing the availability of high-fidelity datasets for AI development.

### 1.1.2 Understanding “AI-Ready Data”

Against this background, the central concern of this study is how existing open data can be progressively improved into AI-ready open data. In Taiwan, one important point of reference in this process has been the FAIR data principles, which emphasize Findability, Accessibility, Interoperability, and Reusability [2]. These four dimensions, together with metadata governance frameworks as a practical entry point, provide a basis for strengthening data provenance transparency and improving overall data quality. The U.S. Department of Commerce likewise notes in Generative AI and Open Data: Guidelines and Best Practices that the needs of AI systems [2] for automated extraction and interpretation should be considered at the point of data release, so that published data already satisfies the baseline conditions needed to support AI training (U.S. Department of Commerce, 2025).

A related framework is the World Bank’s concept of AI-ready development data, which identifies three core conditions for advancing data toward AI readiness. The first is the development of AI-ready Data Systems, including data discovery platforms, application programming interfaces (APIs), and relevant technical standards that enable data to be effectively found, accessed, and used across systems. The second is the Provision of High-Quality Data and Metadata:

data should be reliable and timely, and accompanied by structured, sufficiently complete metadata so that both machines and human users can accurately interpret its content and context. The third is Sound Governance and Strategic Collaboration, through which policy frameworks, standardized processes, and cross-sector coordination can help ensure data quality and consistency, enhance transparency, and promote the responsible use of data, thereby strengthening trust in the broader data ecosystem [3].

Taken together, these principles suggest that AI-ready open data should be understood as data that is prepared, at the point of release, takes into account its potential future application scenarios; adopts appropriate data formats; and simultaneously establishes the necessary metadata.

Where appropriate, releases can be accompanied by clearer documentation, quality controls, and reuse permissions, so that, when used for AI training, data is more likely to be accurate, complete, reliable, and extensible.

### 1.1.3 Key Considerations for AI-Ready Open Data

When online information involves copyright infringement or privacy disputes, the spread of such information can be curtailed by removing the original webpage or requesting search engines to de-index it, reducing its visibility over time. However, when AI-ready data is used to train AI models, the information may be reflected in model parameters and deeply internalized within complex neural structures. Existing studies describe this as high data persistence in AI systems [4]. Therefore, before training, data should be audited for copyright, licensing status, applicable exceptions and limitations, and possible personal or private information.

## 1.2 Concrete Benefits of AI-Ready Open Data

In 2009, a research team led by Professor Fei-Fei Li at Stanford University created the open ImageNet dataset, which covers more than 20,000 categories and contains over 14 million labeled images [5]. This dataset fundamentally transformed the development of AI-based image recognition:

image classification accuracy increased from 71.8% to over 95% within seven years, and ImageNet went on to become a foundational training resource for applications such as medical imaging, autonomous driving, and facial recognition [6]. This example demonstrates that high-quality, well-annotated public datasets can catalyze technological breakthroughs across entire industries. It also suggests that AI-ready data can be expected to bring tangible benefits to the development of human civilization.

### 1.2.1 Industry Development and Value Creation

According to data from McKinsey & Company, open data can generate up to USD 5 trillion in economic value annually across seven major global industries. This enormous economic value is largely derived from the use of open data in AI training, highlighting the substantial industrial benefits of AI-ready data [7].

The report also notes that researchers working on LLM models spend as much as 80% of their time converting government open data into formats suitable for AI training.

This underscores that if governments were able to produce AI-ready data directly, it would not only accelerate national technological development but also significantly reduce the high data processing costs borne by domestic enterprises.

### 1.2.2 Cultural Preservation and the Consolidation of Sovereignty

When a nation’s linguistic data represents a marginal share of publicly available training datasets, its citizens are unlikely to receive information that accurately reflects their national context when using mainstream AI models. This can contribute to ’marginalization’ and ’misinterpretation’ over time, shaping persistent misunderstandings in public discourse and educational contexts. If unchecked, such conditions will undermine the preservation and accurate representation of cultural and historical knowledge within AI-mediated information environments, ultimately putting national identity and heritage at risk.
