---
title: "Chapter 3: How Open Data Becomes AI-Ready"
tags: [AI-Ready 開放資料, 開放科技]

---

# Chapter 3: How Open Data Becomes AI-Ready

[![hackmd-github-sync-badge](https://hackmd.io/XvNPhgwOT4mBtd7oMh8opQ/badge)](https://hackmd.io/XvNPhgwOT4mBtd7oMh8opQ)

_Source: OCF-AI-en.pdf, pp. 14-18._

## Figures

![English chapter 3 main visual showing AI-ready data transformation](https://raw.githubusercontent.com/yanyiyi/From-Open-2-AI-Ready-Data-Case-Study/main/assets/en-ch3-main-visual.png "英文版 Chapter 3 main visual")

This chapter summarizes the technical experiences of transforming open data into AI-ready data based on the case study interviews presented earlier. Many people assume that upgrading to AI-ready requires expensive software or labor-intensive manual intervention for data cleaning. However, the interviews indicate that in most cases, simply following existing open data workflows-even in a simplified form-can effectively produce AI-ready data.

A practical approach to AI-ready data prioritizes preserving information in its native, machine-readable form and avoiding conversions (e.g., scanned PDFs) that degrade structure; in many cases, this can be achieved with limited additional processing.

This chapter aims to help agencies optimize the production process for AI-ready open data.

Under the TOE analysis, this chapter focuses on the technological dimension, examining the key technologies required to advance open data toward AI-readiness. It uses case comparisons to illustrate three main topics: data format conversion and enhancement of machine readability, privacy protection and de-identification, and the identification of data bias.

## 3.1 Using Machine-Readable Formats

PDF document processing has become a common challenge for many teams due to modern reading habits. The Parla system developed by CityLAB Berlin aims to make 11,000 parliamentary documents searchable and summarizable by AI. However, because the files are in PDF format, they are not suitable for large language model processing and must first be converted to text using OCR, creating a significant technical debt challenge.

### 3.1.1 Systematic OCR Conversion and Document Preservation

The Parla team invested substantial resources in OCR to make the content machine-readable, but this caused the loss of structural information such as original formatting, paragraphs, and table headers, affecting semantic integrity and contextual coherence. They found that quality control required a hybrid of semi-automated processing and manual verification. At the start of the project, handling PDF files was critical, and the team had to undergo iterative cycles to ensure optimal outcomes. Eventually, they compiled their experience into technical documentation and shared it publicly to assist stakeholders in mitigating similar difficulties.

### 3.1.2 Addressing Readability Variations Across Historical Typefaces

The German Commons project faced similar challenges. The project consolidated German texts from 41 sources across seven domains, ultimately producing 154.5 billion tokens of training data. During the interview, project leader Lukas Gienapp explained that they lost nearly half of the original data during the data filtering stage. In addition to language-identification filtering, a major source of loss was errors introduced during OCR conversion.

The project included many older German Frakturschrift documents, which early OCR technology could not accurately recognize, resulting in numerous errors after digitization. To avoid undermining language model training, the team chose to strictly filter the data, accepting reduced dataset volume in order to maintain qualitative rigor. This illustrates that government records lacking machine-readable formats have limited utility for downstream AI training.

### 3.1.3 Selecting Appropriate OCR Strategies and Formats Based on Data Conditions

It is worth noting, however, that the German Commons team adopts two different technical approaches depending on the nature of the documents requiring OCR. For PDFs that already contain an embedded text layer, they use the tool Grobid [14] to extract text; for PDFs that are exclusively scanned images, they use the Allen Institute for AI's OlmOCR model [15] for recognition.

This strategy of selecting tools based on document characteristics serves as a constructive precedent for other projects. Nevertheless, even with advanced tools like Grobid or Olmocr, current technological capabilities still have significant limitations in accurately recognizing older fonts or complex layouts.

### 3.1.4 Designing for Machine Readability and Open Licensing at the Point of Data Creation and Preservation

Based on the cases discussed above, several actionable insights can help stakeholders make open data more suitable for AI training. First, prioritize releasing data in machine-readable formats. Using conventional tabular data as a case in point: even if data is released in CSV format, merged cells or empty rows implemented for human legibility can still impede automated processing by AI systems. These ’human-friendly’ layout designs often become confusing noise during AI training. Therefore, it is recommended to also release raw files that are unformatted and maintain consistent header definitions.

If the nature of the data does not require spreadsheets, beyond traditional plain text files, Markdown format could also be considered. This format allows precise preservation of heading hierarchies, list structures, and references, all while maintaining a minimal storage footprint, enabling AI to understand the content while also capturing the logical structure of the document. Where cross-referential structural integrity is required, structured formats such as JSON or XML can provide a more rigorous data architecture, significantly reducing the cost of subsequent cleaning.

Furthermore, in the past, government agencies often saved files in PDF format and sometimes even released them as PDFs to prevent layout issues when opening documents on different operating systems or software. However, it is advisable to release the original data formats alongside PDFs whenever possible. For example, if the original data is a spreadsheet, release it directly as a CSV or Excel file; if it is a text document, release it as plain text or in a structured format such as JSON or XML. If PDFs must be provided for specific reasons, agencies should prefer PDFs with embedded text layers over purely scanned images. Finally, if institutional capacity allows, agencies can provide multiple formats simultaneously, enabling users with different needs to access the version most suitable for them.

France’s CroissantLLM project demonstrates that releasing data in machine-readable formats from the outset can greatly enhance convenience and efficiency. The project trained a 1.3-billion-parameter bilingual model using open government data. All data were centralized on France’s open data initiative platform (data.gouv.fr) and provided under permissive licenses such as the MIT License or Creative Commons, allowing users to download and use the data directly. The data were already standardized and passed basic validation checks, so the CroissantLLM team required only minimal cleaning before training. This case shows that a unified data platform, clear licensing, and pre-processing can effectively lower the data preparation costs for AI developers.

## 3.2 Personal Data De-Identification Process

Protecting personal data should be an integral part of the open data workflow and is a critical issue that all open data practitioners must address. When releasing raw data, the primary perceived risk for government agencies is unauthorized data disclosure.

### 3.2.1 Iterative Privacy Risk Mitigation within Controlled Processing Cycles

The CroissantLLM team, when training their French bilingual model, used government open data with permissive licenses and books already in the public domain, so de-identification was not necessary. These sources did not contain personal data, and preliminary administrative review had already removed most sensitive information. The team also stated in the interview that, because they used public government data without personally identifiable information (PII), no traditional de-identification procedures were applied.

Nevertheless, the team exercised caution. Before releasing the model, they conducted privacy verification by embedding specific strings in the training data to test whether the model would memorize and output sensitive content. The results showed that as long as a piece of data appeared fewer than four times in the corpus, the risk of disclosure was low. This indicates that memorization within language models is positively correlated with token frequency; low-frequency sensitive data exhibits a reduced probability of reconstruction. This research has been published at ICML and contributes to discussions on copyright issues for large language models.

### 3.2.2 Context-Aware Design of De-identification and Anonymization Codes

For handling raw text, the German Commons approach provides a useful technical reference. Most of the data in this project came from historical documents, and the personal information they contained was already outdated. Project lead Lukas Gienapp explained that for historical data, most PII is over eighty years old and does not require urgent protection.

Nevertheless, German Commons still carried out PII removal because the dataset included a small amount of online-sourced text. They used Microsoft’s Presidio framework along with German-optimized regular expressions (Regex) to detect and handle phone numbers, credit card numbers, addresses, bank account numbers, and other information that could be maliciously exploited. Technically, they added regex detection for Germany-specific formats, such as regional phone codes and specific bank account prefixes.

In the interview, Lukas Gienapp shared an important technical insight: when removing PII, sensitive information that has been detected should not be simply deleted but replaced with generic content. Traditional de-identification often removes sensitive strings entirely, but German Commons chooses to replace them with generic labels rather than deleting them.

He illustrated this with an example: if all credit card numbers are simply removed, the trained model will never learn what a credit card number looks like; however, if a set of known safe, generic credit card numbers is used as replacements and randomly inserted in place of the original sensitive content, the model can still learn the relevant contextual patterns.

Similarly, a sentence like ’Zhang Junya lives in Taipei’ would be replaced with ’[PERSON] lives in [LOCATION]’ rather than deleting names or locations. This preserves sentence structure, enabling the language model to learn grammar and context without producing broken sentences due to data removal.

In addition, Lukas Gienapp emphasized that this substitution process must be traceable. In the appendix of their paper, German Commons provides a detailed list of all the synthetic placeholders they used, enabling subsequent users to understand what modifications were made to the data and, if necessary, apply alternative replacement strategies.

### 3.2.3 Privacy Considerations for Marginalized and Vulnerable Communities

Beyond the technical dimension, ODC’s experience illustrates how practitioners manage data dissemination within nascent regulatory landscapes, while also reminding readers to consider communal and cultural data sensitivities beyond the law. In many developing countries or regions with incomplete legal systems, even data that is legally open may cause real harm if it involves the residences or identities of indigenous peoples or other vulnerable groups. ODC staff explained in the interview that, in building trust with government agencies, they learned to respect and communicate with their counterparts. For example, when collaborating with the Ministry of Environment, if the agency indicated that not all reports could be made public, ODC would ask about the rationale for non-disclosure, seek to understand the agency’s concerns, and learn which reports could be released publicly and which should remain for research or educational purposes. At the same time, ODC would propose potential solutions whenever possible, facilitating dialogue with the government and other stakeholders.

ODC’s approach also highlights how culturally sensitive data should be handled in practice. Staff shared a critical observation: in Cambodia, many indigenous people are reluctant to acknowledge their identities because they wish to avoid legal discrimination. Even merely mentioning a name can potentially harm local communities. The lesson for this study is that protecting personal data goes beyond technical de-identification; it requires a deep understanding of local cultural contexts. When handling such data, ODC implements community guidelines that are stricter than legal requirements, ensuring that data release does not cause adverse downstream impacts to vulnerable groups. This human-centered approach cannot rely solely on automated tools or statutory minimum requirements; it demands cultural sensitivity to the local context and serves as an important reference for all open data practitioners.

### 3.2.4 Summary

From these cases, several practical principles can be drawn.

First, managing data at the point of origin is preferable to addressing issues afterward; by prioritizing the release of datasets inherently devoid of sensitive personal information, the workload for subsequent de-identification can be greatly reduced. Second, when de-identification is necessary, replacement rather than deletion should be used to preserve the integrity and usability of the text. Finally, the de-identification process should be transparent and traceable, allowing users to understand what modifications the data have undergone and recalibrate parameters if necessary.

## 3.3 Eliminating Bias in Training Data

Language model developers must address bias in training data. The quality of the data determines the perspective of the AI; if the data is biased, the model's output will also be affected. Interviews with various teams revealed diverse forms of bias and different strategies to address them.

### 3.3.1 Intentional Dataset Composition and the Release of Open Tools

The CroissantLLM project aimed to build a truly bilingual language model. At the time, most models claiming to support French still relied heavily on English data, resulting in poor performance in French. To address this issue, the project prioritized strategic linguistic allocation from the outset, allocating 40% English, 40% French, and about 20% code, ensuring a balanced corpus and improving the model’s capability and stability in both bilingual and structured data tasks.

Beyond the model itself, the CroissantLLM team also released high-quality French-language datasets and established a dedicated French evaluation benchmark, FrenchBench. This allows subsequent researchers and model trainers to more systematically examine whether models exhibit disproportionate skewness toward English, and whether French-language performance is being sacrificed during training. It also helps safeguard that highly localized knowledge contexts, such as those in administration and law-can be correctly understood and generated by models in future development, rather than being forced through an English-centric mode of thinking before responding to France’s institutional and policy questions.

This experience offers important insights for open data practitioners working with minority languages. Many minority languages have limited online resources, and passively ingesting existing materials risks entrenching or exacerbating linguistic disparities. The experience of CroissantLLM shows that language balance requires deliberate design of data composition, along with the creation of datasets and tools for subsequent research and evaluation. In this way, non-dominant languages can gain opportunities for development and validation in the era of AI and large language models.

### 3.3.2 Recognizing Temporal Bias in Data

The German Commons project faced another form of bias: an imbalance along the temporal dimension. The team observed an interesting phenomenon they called ’nostalgia bias.’ Because German copyright law generally keeps works under copyright until a statutory term after the author’s death, a large proportion of freely usable cultural works and newspaper archives are historical in nature. This creates what project leader Lukas Gienapp refers to as nostalgia bias:

the training data are filled with texts from decades or even over a hundred years ago, while content from the middle period between the very recent and the very distant past is largely missing. As a result, the trained model may sound outdated in tone and vocabulary, as if it were living in the early twentieth century.

Lukas Gienapp acknowledged that this problem is difficult to fully resolve under the current legal framework, since more recent cultural works remain under copyright protection. To mitigate the deficit in modern data, their strategy has been to integrate sources from different domains to attain a degree of structural parity. They actively seek texts such as court judgments and government gazettes, contemporary materials that are legally open, to counter temporal bias. Web-based texts tend to skew toward more recent content. Scientific literature also often gravitates toward more recent periods due to the open-access movement, while historical documents provide necessary temporal depth. Although a perfectly even temporal distribution is difficult, combining sources can reduce extreme temporal bias and ensure the dataset is not confined to a single period.

### 3.3.3 Supporting Multilingual Diversity

Cambodia’s ODC experience underscores the practical and governance complexities of working with linguistic diversity in AI-ready data. Interviewees noted that Cambodia is not a Khmer-only context: alongside Khmer, multiple minority communities, such as the Bunong (M’nong), Brao, Kuoy, Lao, Jarai, Kreung, Kavet, Tampuan, and Kachok, live across different provinces and use distinct Indigenous languages.

However, most available digital corpora remain concentrated in Khmer and tend to reflect urban perspectives; as a result, rural and Indigenous voices are systematically under-represented in the data pipeline and risk continued marginalization within the digital sphere. Because it is not possible to expeditiously produce large amounts of indigenous-language data, ODC has used English as a third language to preserve these perspectives. Although this approach is controversial, English datasets enable researchers who do not understand Khmer or indigenous languages to train AI models that represent more diverse Cambodian viewpoints. This also highlights the role that governments should play: releasing data of high public value but low commercial appeal, such as local gazetteers, dialect records, and information on rural infrastructure, thereby helping mitigate cultural bias in AI systems and supporting locally grounded AI capabilities.

### 3.3.4 Reducing Bias through Workflow and Process Design

In the context of reducing bias, these cases all converge on a unified strategic response: systemic biases require structural countermeasures. Lukas Gienapp of German Commons suggests a two-stage workflow. In the first stage, domain experts take the lead; in the second stage, data aggregators step in to adjust and harmonize the results. In operational terms, domain experts first curate specialized datasets within their own fields. Then, aggregators, who have expertise in corpus development, system architecture, and data processing, use technical methods to integrate these datasets. The advantage of this division of labor is that domain experts possess a more nuanced comprehension of the characteristics and potential biases of data in their fields, while aggregators can balance different sources from a cross-domain perspective.

### 3.3.5 Summary

These experiences lead to several immediately actionable recommendations. First, when formulating strategic data dissemination plans, agencies should review representativeness: consider whether certain groups or time periods are missing, and supplement them where possible. Second, if agencies have multilingual capacity, they should provide multiple language versions; the provision of translated executive summaries can improve accessibility.

Finally, for fields with high professional barriers, explanatory documentation should be included to help users understand the data’s context and limitations.

Eliminating bias does not mean achieving absolute algorithmic neutrality. Every dataset reflects the choices and constraints of its production process. The primary objective is to remain vigilant, mitigate bias where feasible, and disclose limitations transparently. German Commons offers a useful model by analyzing the temporal distribution and disciplinary composition of its data, allowing users to judge applicability against their specific use cases and requirements.
