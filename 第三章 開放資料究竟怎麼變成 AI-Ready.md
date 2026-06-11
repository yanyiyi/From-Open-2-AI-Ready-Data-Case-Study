---
title: "Chapter 3: How Open Data Becomes AI-Ready / 第三章 開放資料究竟怎麼變成 AI-Ready"
languages: [en, zhtw]
source_pdfs: [OCF-AI-en.pdf, OCF-AI-zhtw.pdf]
---

# Chapter 3: How Open Data Becomes AI-Ready / 第三章 開放資料究竟怎麼變成 AI-Ready

_Source pages: English PDF pp. 14-18; Traditional Chinese PDF pp. 13-16. Paragraph order is kept parallel by section where the two PDFs correspond._

## Figures / 圖片

![English chapter 3 main visual showing AI-ready data transformation](assets/en-ch3-main-visual.png "英文版 Chapter 3 main visual")

![繁中第三章主視覺：開放資料變成 AI-Ready](assets/zhtw-ch3-main-visual.png "繁中版第三章主視覺")

## English

This chapter summarizes the technical experiences of transforming open data into AI-ready data based on the case study interviews presented earlier. Many people assume that upgrading to AI-ready requires expensive software or labor-intensive manual intervention for data cleaning. However, the interviews indicate that in most cases, simply following existing open data workflows-even in a simplified form-can effectively produce AI-ready data.

A practical approach to AI-ready data prioritizes preserving information in its native, machine-readable form and avoiding conversions (e.g., scanned PDFs) that degrade structure; in many cases, this can be achieved with limited additional processing.

This chapter aims to help agencies optimize the production process for AI-ready open data.

Under the TOE analysis, this chapter focuses on the technological dimension, examining the key technologies required to advance open data toward AI-readiness. It uses case comparisons to illustrate three main topics: data format conversion and enhancement of machine readability, privacy protection and de-identification, and the identification of data bias.

### 3.1 Using Machine-Readable Formats

PDF document processing has become a common challenge for many teams due to modern reading habits. The Parla system developed by CityLAB Berlin aims to make 11,000 parliamentary documents searchable and summarizable by AI. However, because the files are in PDF format, they are not suitable for large language model processing and must first be converted to text using OCR, creating a significant technical debt challenge.

#### 3.1.1 Systematic OCR Conversion and Document Preservation

The Parla team invested substantial resources in OCR to make the content machine-readable, but this caused the loss of structural information such as original formatting, paragraphs, and table headers, affecting semantic integrity and contextual coherence. They found that quality control required a hybrid of semi-automated processing and manual verification. At the start of the project, handling PDF files was critical, and the team had to undergo iterative cycles to ensure optimal outcomes. Eventually, they compiled their experience into technical documentation and shared it publicly to assist stakeholders in mitigating similar difficulties.

#### 3.1.2 Addressing Readability Variations Across Historical Typefaces

The German Commons project faced similar challenges. The project consolidated German texts from 41 sources across seven domains, ultimately producing 154.5 billion tokens of training data. During the interview, project leader Lukas Gienapp explained that they lost nearly half of the original data during the data filtering stage. In addition to language-identification filtering, a major source of loss was errors introduced during OCR conversion.

The project included many older German Frakturschrift documents, which early OCR technology could not accurately recognize, resulting in numerous errors after digitization. To avoid undermining language model training, the team chose to strictly filter the data, accepting reduced dataset volume in order to maintain qualitative rigor. This illustrates that government records lacking machine-readable formats have limited utility for downstream AI training.

#### 3.1.3 Selecting Appropriate OCR Strategies and Formats Based on Data Conditions

It is worth noting, however, that the German Commons team adopts two different technical approaches depending on the nature of the documents requiring OCR. For PDFs that already contain an embedded text layer, they use the tool Grobid [14] to extract text; for PDFs that are exclusively scanned images, they use the Allen Institute for AI's OlmOCR model [15] for recognition.

This strategy of selecting tools based on document characteristics serves as a constructive precedent for other projects. Nevertheless, even with advanced tools like Grobid or Olmocr, current technological capabilities still have significant limitations in accurately recognizing older fonts or complex layouts.

#### 3.1.4 Designing for Machine Readability and Open Licensing at the Point of Data Creation and Preservation

Based on the cases discussed above, several actionable insights can help stakeholders make open data more suitable for AI training. First, prioritize releasing data in machine-readable formats. Using conventional tabular data as a case in point: even if data is released in CSV format, merged cells or empty rows implemented for human legibility can still impede automated processing by AI systems. These ’human-friendly’ layout designs often become confusing noise during AI training. Therefore, it is recommended to also release raw files that are unformatted and maintain consistent header definitions.

If the nature of the data does not require spreadsheets, beyond traditional plain text files, Markdown format could also be considered. This format allows precise preservation of heading hierarchies, list structures, and references, all while maintaining a minimal storage footprint, enabling AI to understand the content while also capturing the logical structure of the document. Where cross-referential structural integrity is required, structured formats such as JSON or XML can provide a more rigorous data architecture, significantly reducing the cost of subsequent cleaning.

Furthermore, in the past, government agencies often saved files in PDF format and sometimes even released them as PDFs to prevent layout issues when opening documents on different operating systems or software. However, it is advisable to release the original data formats alongside PDFs whenever possible. For example, if the original data is a spreadsheet, release it directly as a CSV or Excel file; if it is a text document, release it as plain text or in a structured format such as JSON or XML. If PDFs must be provided for specific reasons, agencies should prefer PDFs with embedded text layers over purely scanned images. Finally, if institutional capacity allows, agencies can provide multiple formats simultaneously, enabling users with different needs to access the version most suitable for them.

France’s CroissantLLM project demonstrates that releasing data in machine-readable formats from the outset can greatly enhance convenience and efficiency. The project trained a 1.3-billion-parameter bilingual model using open government data. All data were centralized on France’s open data initiative platform (data.gouv.fr) and provided under permissive licenses such as the MIT License or Creative Commons, allowing users to download and use the data directly. The data were already standardized and passed basic validation checks, so the CroissantLLM team required only minimal cleaning before training. This case shows that a unified data platform, clear licensing, and pre-processing can effectively lower the data preparation costs for AI developers.

### 3.2 Personal Data De-Identification Process

Protecting personal data should be an integral part of the open data workflow and is a critical issue that all open data practitioners must address. When releasing raw data, the primary perceived risk for government agencies is unauthorized data disclosure.

#### 3.2.1 Iterative Privacy Risk Mitigation within Controlled Processing Cycles

The CroissantLLM team, when training their French bilingual model, used government open data with permissive licenses and books already in the public domain, so de-identification was not necessary. These sources did not contain personal data, and preliminary administrative review had already removed most sensitive information. The team also stated in the interview that, because they used public government data without personally identifiable information (PII), no traditional de-identification procedures were applied.

Nevertheless, the team exercised caution. Before releasing the model, they conducted privacy verification by embedding specific strings in the training data to test whether the model would memorize and output sensitive content. The results showed that as long as a piece of data appeared fewer than four times in the corpus, the risk of disclosure was low. This indicates that memorization within language models is positively correlated with token frequency; low-frequency sensitive data exhibits a reduced probability of reconstruction. This research has been published at ICML and contributes to discussions on copyright issues for large language models.

#### 3.2.2 Context-Aware Design of De-identification and Anonymization Codes

For handling raw text, the German Commons approach provides a useful technical reference. Most of the data in this project came from historical documents, and the personal information they contained was already outdated. Project lead Lukas Gienapp explained that for historical data, most PII is over eighty years old and does not require urgent protection.

Nevertheless, German Commons still carried out PII removal because the dataset included a small amount of online-sourced text. They used Microsoft’s Presidio framework along with German-optimized regular expressions (Regex) to detect and handle phone numbers, credit card numbers, addresses, bank account numbers, and other information that could be maliciously exploited. Technically, they added regex detection for Germany-specific formats, such as regional phone codes and specific bank account prefixes.

In the interview, Lukas Gienapp shared an important technical insight: when removing PII, sensitive information that has been detected should not be simply deleted but replaced with generic content. Traditional de-identification often removes sensitive strings entirely, but German Commons chooses to replace them with generic labels rather than deleting them.

He illustrated this with an example: if all credit card numbers are simply removed, the trained model will never learn what a credit card number looks like; however, if a set of known safe, generic credit card numbers is used as replacements and randomly inserted in place of the original sensitive content, the model can still learn the relevant contextual patterns.

Similarly, a sentence like ’Zhang Junya lives in Taipei’ would be replaced with ’[PERSON] lives in [LOCATION]’ rather than deleting names or locations. This preserves sentence structure, enabling the language model to learn grammar and context without producing broken sentences due to data removal.

In addition, Lukas Gienapp emphasized that this substitution process must be traceable. In the appendix of their paper, German Commons provides a detailed list of all the synthetic placeholders they used, enabling subsequent users to understand what modifications were made to the data and, if necessary, apply alternative replacement strategies.

#### 3.2.3 Privacy Considerations for Marginalized and Vulnerable Communities

Beyond the technical dimension, ODC’s experience illustrates how practitioners manage data dissemination within nascent regulatory landscapes, while also reminding readers to consider communal and cultural data sensitivities beyond the law. In many developing countries or regions with incomplete legal systems, even data that is legally open may cause real harm if it involves the residences or identities of indigenous peoples or other vulnerable groups. ODC staff explained in the interview that, in building trust with government agencies, they learned to respect and communicate with their counterparts. For example, when collaborating with the Ministry of Environment, if the agency indicated that not all reports could be made public, ODC would ask about the rationale for non-disclosure, seek to understand the agency’s concerns, and learn which reports could be released publicly and which should remain for research or educational purposes. At the same time, ODC would propose potential solutions whenever possible, facilitating dialogue with the government and other stakeholders.

ODC’s approach also highlights how culturally sensitive data should be handled in practice. Staff shared a critical observation: in Cambodia, many indigenous people are reluctant to acknowledge their identities because they wish to avoid legal discrimination. Even merely mentioning a name can potentially harm local communities. The lesson for this study is that protecting personal data goes beyond technical de-identification; it requires a deep understanding of local cultural contexts. When handling such data, ODC implements community guidelines that are stricter than legal requirements, ensuring that data release does not cause adverse downstream impacts to vulnerable groups. This human-centered approach cannot rely solely on automated tools or statutory minimum requirements; it demands cultural sensitivity to the local context and serves as an important reference for all open data practitioners.

#### 3.2.4 Summary

From these cases, several practical principles can be drawn.

First, managing data at the point of origin is preferable to addressing issues afterward; by prioritizing the release of datasets inherently devoid of sensitive personal information, the workload for subsequent de-identification can be greatly reduced. Second, when de-identification is necessary, replacement rather than deletion should be used to preserve the integrity and usability of the text. Finally, the de-identification process should be transparent and traceable, allowing users to understand what modifications the data have undergone and recalibrate parameters if necessary.

### 3.3 Eliminating Bias in Training Data

Language model developers must address bias in training data. The quality of the data determines the perspective of the AI; if the data is biased, the model's output will also be affected. Interviews with various teams revealed diverse forms of bias and different strategies to address them.

#### 3.3.1 Intentional Dataset Composition and the Release of Open Tools

The CroissantLLM project aimed to build a truly bilingual language model. At the time, most models claiming to support French still relied heavily on English data, resulting in poor performance in French. To address this issue, the project prioritized strategic linguistic allocation from the outset, allocating 40% English, 40% French, and about 20% code, ensuring a balanced corpus and improving the model’s capability and stability in both bilingual and structured data tasks.

Beyond the model itself, the CroissantLLM team also released high-quality French-language datasets and established a dedicated French evaluation benchmark, FrenchBench. This allows subsequent researchers and model trainers to more systematically examine whether models exhibit disproportionate skewness toward English, and whether French-language performance is being sacrificed during training. It also helps safeguard that highly localized knowledge contexts, such as those in administration and law-can be correctly understood and generated by models in future development, rather than being forced through an English-centric mode of thinking before responding to France’s institutional and policy questions.

This experience offers important insights for open data practitioners working with minority languages. Many minority languages have limited online resources, and passively ingesting existing materials risks entrenching or exacerbating linguistic disparities. The experience of CroissantLLM shows that language balance requires deliberate design of data composition, along with the creation of datasets and tools for subsequent research and evaluation. In this way, non-dominant languages can gain opportunities for development and validation in the era of AI and large language models.

#### 3.3.2 Recognizing Temporal Bias in Data

The German Commons project faced another form of bias: an imbalance along the temporal dimension. The team observed an interesting phenomenon they called ’nostalgia bias.’ Because German copyright law generally keeps works under copyright until a statutory term after the author’s death, a large proportion of freely usable cultural works and newspaper archives are historical in nature. This creates what project leader Lukas Gienapp refers to as nostalgia bias:

the training data are filled with texts from decades or even over a hundred years ago, while content from the middle period between the very recent and the very distant past is largely missing. As a result, the trained model may sound outdated in tone and vocabulary, as if it were living in the early twentieth century.

Lukas Gienapp acknowledged that this problem is difficult to fully resolve under the current legal framework, since more recent cultural works remain under copyright protection. To mitigate the deficit in modern data, their strategy has been to integrate sources from different domains to attain a degree of structural parity. They actively seek texts such as court judgments and government gazettes, contemporary materials that are legally open, to counter temporal bias. Web-based texts tend to skew toward more recent content. Scientific literature also often gravitates toward more recent periods due to the open-access movement, while historical documents provide necessary temporal depth. Although a perfectly even temporal distribution is difficult, combining sources can reduce extreme temporal bias and ensure the dataset is not confined to a single period.

#### 3.3.3 Supporting Multilingual Diversity

Cambodia’s ODC experience underscores the practical and governance complexities of working with linguistic diversity in AI-ready data. Interviewees noted that Cambodia is not a Khmer-only context: alongside Khmer, multiple minority communities, such as the Bunong (M’nong), Brao, Kuoy, Lao, Jarai, Kreung, Kavet, Tampuan, and Kachok, live across different provinces and use distinct Indigenous languages.

However, most available digital corpora remain concentrated in Khmer and tend to reflect urban perspectives; as a result, rural and Indigenous voices are systematically under-represented in the data pipeline and risk continued marginalization within the digital sphere. Because it is not possible to expeditiously produce large amounts of indigenous-language data, ODC has used English as a third language to preserve these perspectives. Although this approach is controversial, English datasets enable researchers who do not understand Khmer or indigenous languages to train AI models that represent more diverse Cambodian viewpoints. This also highlights the role that governments should play: releasing data of high public value but low commercial appeal, such as local gazetteers, dialect records, and information on rural infrastructure, thereby helping mitigate cultural bias in AI systems and supporting locally grounded AI capabilities.

#### 3.3.4 Reducing Bias through Workflow and Process Design

In the context of reducing bias, these cases all converge on a unified strategic response: systemic biases require structural countermeasures. Lukas Gienapp of German Commons suggests a two-stage workflow. In the first stage, domain experts take the lead; in the second stage, data aggregators step in to adjust and harmonize the results. In operational terms, domain experts first curate specialized datasets within their own fields. Then, aggregators, who have expertise in corpus development, system architecture, and data processing, use technical methods to integrate these datasets. The advantage of this division of labor is that domain experts possess a more nuanced comprehension of the characteristics and potential biases of data in their fields, while aggregators can balance different sources from a cross-domain perspective.

#### 3.3.5 Summary

These experiences lead to several immediately actionable recommendations. First, when formulating strategic data dissemination plans, agencies should review representativeness: consider whether certain groups or time periods are missing, and supplement them where possible. Second, if agencies have multilingual capacity, they should provide multiple language versions; the provision of translated executive summaries can improve accessibility.

Finally, for fields with high professional barriers, explanatory documentation should be included to help users understand the data’s context and limitations.

Eliminating bias does not mean achieving absolute algorithmic neutrality. Every dataset reflects the choices and constraints of its production process. The primary objective is to remain vigilant, mitigate bias where feasible, and disclose limitations transparently. German Commons offers a useful model by analyzing the temporal distribution and disciplinary composition of its data, allowing users to judge applicability against their specific use cases and requirements.

## 繁體中文

本章將從上一章提及的案例訪談中，擷取讓開放資料變成 AI-ready 的技術實務經驗。

人們容易有個迷思，認為要將手邊的資料轉變到當前最熱門的 AI-Ready 的狀態，肯定需要額外採購昂貴的軟體，或是讓同仁加班進行繁瑣的資料清理。然而從本研究訪談的多個國際案例中，發現絕大多數情況下，只需要依循既有的開放資料流程，甚至可以比過去做得更少都有機會為 AI-Ready 貢獻一份心力。

AI-Ready 講求找回資料最原始、最樸素的樣貌，不同於過去講求民眾的易用性，無需將試算表或文件轉換成圖片或 PDF，因此不必然會增加工項只專注於釋出原始和機器可讀的格式。換言之，對於第一線工作人員，直接匯出並上傳原始檔，無需編輯或另存新檔是可行的，且是最高規格的 AI-Ready 實踐。本章的目的便是為願意直接產出 AI-Ready 開放資料的機關，指出重新規劃或簡化流程的方向。

在 TOE 分析框架下，本章聚焦於科技脈絡的綜合分析，探討各案例在推動開放資料邁向 AI-Ready 過程中，所需關鍵技術如何被具體實踐。透過案例比較，本章將進一步剖析其因應技術發展的三項核心面向，包括資料格式轉換與機器可讀性提升、隱私保護與去識別化技術的應用，以及資料偏見的辨識的方法。

### 3.1 使用機器可讀格式

受現代社會的閱讀習慣影響，在所有受訪案例中，PDF 文件的處理幾乎是每個團隊都必須面對的共同課題。柏林市政府創新實驗室 CityLAB 所開發的 Parla 系統，他們希望能讓超過一萬一千份的議會文件能夠被 AI 搜尋與摘要。這本該是 AI 最擅長的領域，專案負責人卻在訪談中直言，因爲這些極具價值的行政紀錄全數是以 PDF 格式儲存，並非適合 LLM 處理的格式，必須先透過 OCR 軟體轉換成機器可讀的文字，讓他們遭遇了巨大的技術債（Technical debt）挑戰。

#### 3.1.1 有系統地 OCR 轉換與文件傳承

為了讓機器讀懂這些內容，Parla 團隊不得不投入大量資源進行 OCR 轉換。然而這個將圖片轉回文字的過程中，原始文件的結構性元素，例如格式編排、段落分隔、表格標題等，都可能在轉換過程中流失，進而改變文字的脈絡意涵。因此從這個經驗指出，品質控管只能部分自動化，開發過程中的人工檢查絕對不可或缺。因此在專案啟動初期，如何處理 PDF 文件的最佳實務知識成為了研發關鍵，團隊投入了大量反覆試驗才逐漸摸索出可接受的成果。有鑒於這段學習歷程的艱辛，他們後來將經驗整理成技術文件公開分享，希望後來者不必重蹈覆轍。

#### 3.1.2 注意不同時代字體差異造就的可讀性差異

德國語料庫計畫 German Commons 的經驗也遭遇到類似挑戰。這個計畫彙整了來自 41 個來源、涵蓋七大領域的德語文本，最終產出 1,545 億個詞元（token）的訓練語料。計畫主持人 Lukas Gienapp 在訪談中解釋，他們在資料過濾階段損失了將近一半的原始資料量，其中最主要的原因除了語言辨識過濾之外，就是 OCR 轉換所產生的錯誤。

問題的根源在於，German Commons 整合了大量歷史文獻，這些文獻通場使用古老德語字體 Frakturschrift，其外觀與現代字型差異甚大。這些歷史文獻最初被數位化時，當時的 OCR 技術尚未成熟，無法準確辨識這類古老字體，產生了大量的辨識錯誤。這些錯誤一旦存在於原始資料中，將對於語言模型的訓練將造成嚴重的負面影響，因此團隊必須選擇採取較為積極的過濾策略，也就是寧可損失資料量，也要確保整體成果品質。這樣的策略提高了資料損失率，也反映出許多政府公開紀錄即便名義上開放，在缺乏機器可讀性格式的情況下，卻無法達到開放的實質影響力。

#### 3.1.3 配合不同資料狀態選擇適合 OCR 策略及格式

在另一方面，值得注意的是，German Commons 團隊在處理確實需要執行 OCR 的文件時，會依據資料現況，給予兩種不同的技術路徑選擇。對於已經內嵌文字層的 PDF 文件，他們使用 Grobid 這套工具來萃取文字；對於純粹是掃描影像的 PDF，則採用 Allen AI 研發的 Olmocr 模型進行辨識。這種根據文件特性選擇適當工具的策略，值得其他計畫參考。然而現實是，即便他們使用了如 Grobid 或 Olmocr 等先進工具，在現存技術下，對於舊式字體或複雜排版的辨識率仍有極限。

綜合以上案例，對於希望讓開放資料更適合 AI 訓練的讀者，可以歸納出幾項實務建議。首先是優先釋出機器可讀格式，以最普遍的試算表資料為例，即便釋出的是 CSV 格式，假如其中包含為了人類閱讀方便而存在的合併儲存格、空行，AI 依舊無法順利理解試算表的內容。這些「人眼友善」的排版設計在 AI 訓練過程中往往會變成混亂的噪音。因此應同時釋出未經美化加工、具備一致性標頭欄位定義的原始檔。

若資料性質不需要試算表，除了傳統的純文字檔，或許也能考慮採用 Markdown 格式。這種格式能在極小的檔案體積下，精準地保留標題層級、列表結構與引用關係，讓 AI 能夠在理解內容的同時，也掌握文章的邏輯骨架。假如文章內需要連結不同段落的資訊，JSON 或 XML 等結構化格式則能提供更嚴謹的資料基礎，大幅降低後續清理的成本。

註: OCR的工具在2025年小型VLM(例如: Qwen3-VL https://github.com/QwenLM/Qwen3-VL)有非常良好的辨識效果，在文本內容抽取/轉換的格式上，建議需配合一般VLM能轉換的格式, 例如: Markdown格式.

#### 3.1.4 資料產製留存即思考機器可讀性與開放授權

此外，過往公務機關為了避免檔案在不同作業系統、軟體開啟會有跑版問題，會直覺以 PDF 檔案格式存檔，甚至將其做為釋出格式，然而各種原始的資料格式如得以一起開放釋出會是更佳的選項。舉例來說：如果原始資料是試算表，直接釋出 CSV 或 Excel 檔案；如果是文字文件，直接釋出純文字檔或結構化格式如 JSON、XML 等。其次，若因特定原因必須提供 PDF，應優先選擇內嵌文字層的 PDF，而非純粹的掃描影像。最後，如果機關內部有餘力，可以考慮提供多種格式並存，讓不同需求的使用者都能找到最適合的版本。

法國的 CroissantLLM 計畫則展示如果資料一開始都以機器可讀格式釋出，會帶來多大的便利與效益。這個計畫訓練了一個 13 億參數、真正雙語的開放語言模型，其法語訓練資料主要來自法國政府的開放資料倡議。根據團隊成員說明，法國政府透過開放資料倡議平台（data.gouv.fr）集中釋出各部會資料，這些資料均採用如 MIT License 或 Creative Commons 等寬鬆授權條款，使用者無需逐一向各機關申請授權即可直接下載使用。資料釋出時已完成格式標準化與基礎品質檢核，因此 CroissantLLM 團隊只需進行少量的資料清理工作，整體流程相當順暢。這個案例說明，當政府端建立統一的開放資料平台、採用明確的授權機制、並在釋出前完成基礎處理時，下游的 AI 開發者確實能夠大幅降低資料準備的成本。

### 3.2 個資去識別化流程

個人資料保護原本就應在開放資料工作流程內，也是所有開放資料工作者都必須審慎面對的議題。當談論釋出原始資料，公務機關最擔心的莫過於隱私外洩。

#### 3.2.1 四次內的隱私風險控制

法國的 CroissantLLM 團隊在訓練其法語雙語模型時，採取了相當務實的策略。他們優先採用法國政府開放資料平台上已具備寬鬆授權的資料集，以及法國國家圖書館中已經進入公共領域的書籍，進而免去了去識別化相關的工作。這些資料來源本身就不包含需要保護的個人資料，因此在釋出前通常已經過初步的行政審查，去除了大部分敏感個資。此外，團隊成員更在訪談中坦言，他們並沒有執行傳統意義上的去識別化處理，就是因為所使用的公開政府資料本來就不含個人可識別資訊（Personally Identifiable Information，簡稱 PII）。

但這不代表 CroissantLLM 團隊便因此掉以輕心。為了進一步確保安全，他們採取了另一種形式的隱私保護驗證，也就是在模型釋出前，針對模型記憶（model memorization）現象進行實驗。這項實驗會在訓練資料中植入特定字串，藉此觀察模型是否會重新輸出涉及個人隱私的內容，以防止人工智慧因過度學習而背誦敏感資訊。實驗結果顯示，當訓練語料中的單一資料重複次數控制在四次以內，其隱私洩漏風險則對應較低。這個實驗也再次反映大型語言模型的其中一個特性，就是「模型對訓練語料的記憶力與資料出現的頻率呈正相關」。當特定敏感資訊的出現次數極低時，模型權重則不足以支撐其精準複誦出該段內容。這項研究後來也發表於機器學習頂尖研討會 ICML，協助延伸與 LLM 的著作權陷阱相關的探討。[^12]

#### 3.2.2 有語境脈絡地設計去敏感代碼

若要處理未經清洗的文本，German Commons 的作法同樣具有技術參考價值。該計畫整合的絕大多數資料來自歷史文獻，所包含之個人資訊早已不具時效性。計畫主持人 Lukas Gienapp 解釋，對於歷史資料而言，其中的個人可識別資訊（Personally Identifiable Information, PII） 大多已經超過八十年，沒有具有保護的急迫性。

儘管如此，German Commons 仍然選擇執行 PII 移除程序，主要是考量到資料集中也包含了少量的網路來源文本。他們使用微軟的 Presidio 框架搭配針對德語優化的正規表示式（Regular Expression，簡稱 Regex），來偵測並處理電話號碼、信用卡號碼、地址、銀行帳號等可能被惡意利用的資訊。在技術實作上，團隊在 Presidio 之上增加了針對德國特定格式的正規表達式偵測，例如德國區域碼的電話號碼、德國銀行帳號的特定前綴等。

Lukas Gienapp 在訪談中分享了一項重要的技術觀察：執行 PII 移除時，不應該單純地刪除偵測到的敏感資訊，而應該以通用的替代內容取代。傳統的去識別化往往是直接刪除敏感字串，但 German Commons 團隊選擇以通用標籤替換（Replacement）而非刪除。他舉例說明，如果只是移除所有信用卡號碼，訓練出來的模型將永遠學不會信用卡號碼的樣貌；但如果準備一組已知安全可用的通用信用卡號碼作為替代，隨機插入取代原本的敏感內容，模型仍然能夠學習到相關的語境脈絡。例如將「張君雅住在台北市」改為「\[PERSON\] 住在 \[LOCATION\]」，而非直接刪除人名與地名。這麼做的目的是為了保留句子的語法結構，讓語言模型能學習到正確的文法與上下文關係，而不至於因為個資刪除而學出破碎的語句。

此外，Lukas Gienapp 也強調這個替代過程必須具備可追溯性，German Commons 在論文附錄中詳細列出了他們選用的所有通用替代值，讓後續使用者能夠掌握資料經過哪些修改，必要時也能進行不同的替代處理。

#### 3.2.3 弱勢文化的隱私議題

除了技術層面，ODC 的經驗則呈現了在法律框架尚發展中的環境，實務工作者如何謹慎拿捏資料釋出的分寸，同時提醒讀者需注意法律之外的文化隱私。在許多開發中國家或法律尚未完備的地區，即便某些資料依法可公開，但若涉及原住民族或特定弱勢社群的居住地與身份，仍可能造成實質傷害。ODC 的工作人員在訪談中解釋，他們與政府機關建立信任關係的過程中，學會了尊重對方與溝通。例如與環境部合作時，對方表示並非所有報告都能公開， ODC 會詢問對方原因，了解對方的思維和顧慮，學著判斷對政府而言哪些報告可以對外公開、哪些只能作為研究或學習用途。同時 ODC 也會盡可能提出潛在解決方案，和政府與利害關係人對話。

更值得關注的是 ODC 對於文化敏感資料的處理態度。工作人員在訪談中分享了一個發人深省的觀察：在柬埔寨，許多原住民不願意承認自己的身份，因為他們不希望在法律上受到差別對待。即使只是提及一個名字，都可能對當地社群造成傷害。這對本研究的提醒在於，個資保護不僅僅是技術層面的去識別化處理，更需要對在地文化脈絡有深刻的理解。ODC 在處理這些資料時，會引入比法律更嚴格的社群準則，在資料釋出前確保不會對弱勢族群造成二次傷害，這種以人為本的思維，不能僅依賴自動化工具與法規底線，更需具備對在地脈絡的文化敏感度，值得所有開放資料工作者借鏡。

#### 3.2.4 小結

從這些案例中，可以整理出幾項實務原則。首先是源頭管理優於事後處理，如果能在一開始就選擇本質上不含敏感個資的資料類型進行開放，後續的去識別化工作量將大幅降低。其次，當確實需要執行去識別化時，應採用替代而非刪除的策略，以保持文本的完整性與可用性。最後，去識別化的處理過程應該透明且可追溯，讓後續使用者能夠理解資料經過哪些處理，並在必要時進行調整。

### 3.3 消除訓練資料偏見

訓練資料的偏見問題，是所有語言模型開發者都必須面對的課題。資料的品質決定了 AI 的視野，若餵給模型的資料存在偏差，模型輸出的觀點自然也會偏頗。從各個團隊訪談的案例中，本研究團隊觀察到偏見可能以多種形式存在，而不同團隊也發展出各自的應對策略。

#### 3.3.1 有意識地設計語料比例與釋出開放工具

CroissantLLM 計畫的核心目標之一，是打造一個真正具備雙語能力的語言模型。這個目標的背景是，當時坊間聲稱支援法語的模型，往往仍以英語訓練資料為主，僅在其中摻入少量法語內容，導致模型在法語相關任務上的表現明顯落後於英語。為了解決這種不平衡的問題，CroissantLLM 計畫在建置之初即高度重視語言的主體性，並刻意將語言比例視為一項需要人為介入與設計的重點。在訓練資料配置上，有意識地規劃以英文 40%、法文 40% 作為核心比例，並搭配約 20% 的程式碼資料，形成自然語言與結構性資料並行的混合語料。如此配置下，一方面得以避免模型能力向單一語言傾斜；另一方面，亦有助於強化模型在語言推理與模式辨識上的穩定性。

除了模型本身，CroissantLLM 團隊也同步釋出了高品質的法語資料集，並建立專門的法語評測基準 FrenchBench。這使後續研究者與模型訓練者得以更系統性地檢視模型是否仍存在過度偏向英語的情況，並在多樣化任務中實際驗證法語能力是否在訓練過程中被犧牲。這也確保未來延續發展之行政、法律等高度在地化的知識脈絡，能夠被模型正確理解與生成，而非被迫經由英語思維轉譯後再回應法國的制度與政策問題。

這個經驗對於其他非主流語言的開放資料工作者具有重要的啟示意義。許多語言在網路世界中的資料本就相對稀缺，若僅被動彙整既有資源，往往只會複製甚至放大既存的語言不平衡。CroissantLLM 的實踐清楚說明，語言平衡並非自然生成，是需要刻意策劃其組成，並同時建立與釋出可供後續研究與評估參考的資料集與評測工具，才能讓非主流語言在 AI 時代各種大型語言模型中逐步站得住腳，並同時具備長期發展與被持續驗證的可能性。

#### 3.3.2 意識到時間維度造成的偏見

German Commons 計畫則面對了另一種形式的偏見，也就是時間維度上的不均衡。該團隊觀察到一種有趣的懷舊偏見（nostalgia bias）。由於德國著作權法規定，作品在原作者過世一定年限後才會進入公共領域，因此大量可以自由使用的文化作品與報紙文獻都是歷史性的。這造成了計畫主持人 Lukas Gienapp 所稱的懷舊偏見，也就是訓練資料中充斥著數十年甚至上百年前的文本，而缺乏介於非常近期與非常久遠之間的中間時期內容。這導致訓練出來的模型在語氣和用詞上可能顯得過時，彷彿活在二十世紀初。

Lukas Gienapp 坦承這個問題在現有的法律框架下難以完全解決，因為較新的文化作品仍受著作權保護。為了彌補這個現代資料的斷層，他們的應對方式是透過整合不同領域的資料來源來達成某種程度的平衡。必須積極尋找法律判決書、政府公報等當代且著作權開放的文本來平衡時間軸上的偏差。網路來源的文本自然會偏向近期內容，科學文獻由於開放取用運動興起較晚，也會呈現近期偏向，而歷史文獻則填補了更久遠的時期。雖然無法做到完美的時間分布，但至少確保了資料集不會只侷限於單一時期。

#### 3.3.3 多語系的多樣性支援

柬埔寨 ODC 的經驗則突顯了語言多樣性處理的複雜性。同樣的挑戰也發生在柬埔寨，工作人員在訪談中指出，柬埔寨並非僅使用高棉語，同時仍有包含墨儂族（Bunong）布婁族（Brao）、歸族（Kuoy）、佬族（Lao）、嘉萊族（Jarai）、客隆族（Kreung）、卡維特族（Kavet）、坦普安族（Tampuan）和卡秋族（Kachok）等少數民族生活在不同省份，並且使用不同的原住民族語言。然後現在柬埔寨的語料庫資料多從高棉語出發，且集中在城市觀點，未來鄉村與原住民族的聲音可能會在數位世界中消失。考量現實環境無法快速產出大量原住民語言資料，ODC 的應對策略是引入第三方語言-英語，藉由外援的方式盡可能先保留鄉村觀點和原住民文化。雖然以英語來平衡高棉語，進而避免國家內部訓練資料偏見的做法難免引來微詞，但非柬埔寨裔的工作人員以自身經驗為例說明，由於她不諳原住民語和高棉語，在擔任研究實習生期間，他仍能大量仰賴 ODC 提供的英語版資料集，協助訓練 AI 多元的柬埔寨觀點。

這案例中也幫助本研究，也回扣到臺灣公務機關的角色，當民間企業傾向蒐集具商業價值的資料時，政府更有責任釋出那些看似冷門、卻具備高度公共價值的資料，例如地方誌、方言紀錄或是偏鄉的基礎建設資料。這些資料或許無利可圖，但對於修正 AI 模型的文化偏見、建構具備臺灣主體性的數位大腦而言，卻是不可或缺的關鍵拼圖。

#### 3.3.4 透過流程設計減少偏見

從消除偏見的角度來看，這些案例也指向一個共同的解決路徑：偏見的存在往往是系統性的，因此應對策略也必須是系統性的。German Commons 的 Lukas Gienapp 建議採取兩階段的工作模式，第一階段由領域專業知識的人員先行，第二階段再讓資訊整合者（Aggregator）介入調整。具體而言是先讓具有領域專業知識的人員，先行整理各自領域的專業資料集，然後再由具備開發語料資源、系統架構規劃能力、資料處理能力的整合者，以技術再來將這些資料集彙整起來。這種分工方式的好處在於，領域專家更能夠理解該領域資料的特性與潛在偏見，而整合者則可以從跨領域的視角來平衡不同來源的比重。

#### 3.3.5 小結

這些經驗提供了幾項可以立即採行的做法。首先是在規劃資料釋出時，應該有意識地檢視資料的代表性，思考哪些群體或時期可能被遺漏，並在可能的範圍內補充。其次，當機關內部具備多語能力時，應考慮提供多語版本，即使只是先提供主要內容的摘要翻譯，都能大幅提升資料的可及性。最後，若機關所轄領域具有特殊的專業知識門檻，應考慮提供適當的詮釋資料或說明文件，幫助後續使用者正確理解資料的脈絡與限制。

值得強調的是，消除偏見並不意味著追求不可能達成的完美中立。每一份資料集都必然反映了其產製過程中的各種選擇與限制。重要的是對這些偏見保持警覺，在可能的範圍內加以緩解，並且誠實地向使用者揭露已知的限制。German Commons 的做法就是一個好的示範，他們在論文中詳細分析了資料集的時間分布與領域組成，讓使用者能夠根據自身需求判斷這份資料是否適用。

[^12]:  Meeus, Matthieu, Igor Shilov, Manuel Faysse, and Yves-Alexandre de Montjoye. “Copyright Traps for Large Language Models.” In Proceedings of the 41st International Conference on Machine Learning (ICML 2024), 2024\. https://dl.acm.org/doi/10.5555/3692070.3693506.
