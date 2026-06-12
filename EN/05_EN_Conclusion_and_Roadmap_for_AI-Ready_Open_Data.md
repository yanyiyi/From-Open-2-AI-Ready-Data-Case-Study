---
title: "Chapter 5: Conclusion and Roadmap for Promoting AI-Ready Open Data"
tags: [AI-Ready 開放資料, 開放科技]

---

# Chapter 5: Conclusion and Roadmap for Promoting AI-Ready Open Data

[![hackmd-github-sync-badge](https://hackmd.io/XvNPhgwOT4mBtd7oMh8opQ/badge)](https://hackmd.io/XvNPhgwOT4mBtd7oMh8opQ)

_Source: OCF-AI-en.pdf, pp. 24-29._

## Figures

![English chapter 5 main visual showing an AI-ready open data roadmap](https://raw.githubusercontent.com/yanyiyi/From-Open-2-AI-Ready-Data-Case-Study/main/assets/en-ch5-main-visual.png "英文版 Chapter 5 main visual")

![English roadmap tables for collaborative relationships and licensing terms](https://raw.githubusercontent.com/yanyiyi/From-Open-2-AI-Ready-Data-Case-Study/main/assets/en-ch5-roadmap-1.png "英文版 roadmap page 1")

![English roadmap tables for data circulation and technical infrastructure](https://raw.githubusercontent.com/yanyiyi/From-Open-2-AI-Ready-Data-Case-Study/main/assets/en-ch5-roadmap-2.png "英文版 roadmap page 2")

## 5.1 Implementation Modules and Roadmap

Promoting government data toward AI-ready is not a linear, one-way process; rather, it consists of a series of actionable modules that can be deployed according to the needs of each agency. In practice, individual agencies frequently encounter multifaceted and concurrent challenges. For example, an agency may have strong hardware infrastructure yet encounter institutional ambiguity regarding licensing terms, or face operational hurdles in optimizing data interoperability for AI while fostering strategic partnerships. The pace of development can also vary across agencies: some departments may advance more expeditiously due to the nature of their work or organizational culture, while others require more time to establish trust. Based on international case studies, this research categorizes these successful outcomes into four operational modules. Agencies can dynamically combine these practical recommendations according to the challenges they are currently facing, rather than adhering to a rigid, linear implementation path.

This chapter draws on the concrete experiences accumulated from the five case studies, sequentially outlining the technical choices for format conversion, practical methods for personal data de-identification, identification and handling of training data biases, and the planning of long-term data management infrastructure. Each topic presents the tools used in the cases, the limitations encountered, and the considerations behind selecting specific approaches, focusing on actionable steps that frontline practitioners can apply. Some agencies or teams, motivated by professional responsibilities or service quality considerations, may wish to invest extra effort in data processing. This chapter serves as a practical guide for those readers.

This table is designed to help readers quickly identify their own situation and find relevant reference cases. It is important to understand that each case has found feasible solutions within its own constraints, and these solutions are not mutually exclusive-they can be referenced and flexibly combined.

It is not necessary to follow every step exactly.

What matters more is that these solutions are interdependent.

The trust built through collaboration is the foundation for subsequent systematic implementation. Companionship mechanisms developed to overcome obstacles can help more agencies cross initial thresholds. Technical experience accumulated for pursuing high-quality data can be shared back with implementers as a reference. This flexible yet robust approach often handles the complexities of real-world environments better than strictly adhering to a predefined roadmap.

## 5.2 AI-Ready Data Empowering Democracy and Society

When discussing the integration of open data with AI, it is easy to get caught up in purely technical debates and overlook the the more fundamental questions for civil servants, citizens, and stakeholders other than business sectors: ’What is all this for?’ From the cases examined in this study, we identified three dimensions of empowerment, which together form the foundational value of open data in contemporary society.

### 5.2.1 Empowering Civil Servants in Their Work

The most direct beneficiaries of open data initiatives are ultimately the civil servants themselves. The experience of the Parla project provides a robust empirical illustration of this principle. Consultative workshops with Berlin’s administrative personnel identified the manual processing of parliamentary inquiries as a significant operational bottleneck, the solutions developed by CityLAB not only helped them save time but, more importantly, enabled them to respond more effectively to members of parliament, thereby improving the quality of their work.

Spain's ImpulsaDATA program reflects the same value. In the interview, Carlos Alonso Peña, Director of the Spanish Data Office Division, mentioned that many agencies, after receiving guidance, found that establishing good internal data governance not only facilitates external data release but also improves internal workflows. When data is properly organized and managed, staff can handle information retrieval, report preparation, and responses to tasks assigned by superiors much more efficiently. These internal benefits often serve as a key motivation for agencies to continue investing in open data initiatives.

The data literacy training that ODC provides to Cambodian government agencies illustrates the same logic. By helping agencies understand how to organize and manage data, ODC not only lowers the barriers to data release but also enhances the agencies' administrative effectiveness. This experience demonstrates that promoting open data should not be seen as an additional burden, but rather as an opportunity to strengthen the overall capacity of the public service system.

### 5.2.2 Empowering Citizens’ Knowledge and Participation

The contribution of open data to democracy goes beyond increasing transparency; it also lies in how it enables citizens to participate more effectively in public affairs. A typical example is the economic land concession map created by ODC in Cambodia. Before this map existed, indigenous communities had difficulty knowing which lands had been designated as concessions and which areas were still available for community use. Once this information was visualized, communities could concretely advocate to the government for the protection of their traditional territories. When such data is released in an AI-ready format, even citizens without specialized legal or spatial analysis backgrounds can potentially feed structured data into large language models to expeditiously summarize the potential impacts of specific development projects on their traditional territories, or even request AI to generate discussions about these projects.

This form of empowerment helps translate transparency from a principle into practical civic agency. When citizens have access to structured data, they can conduct their own analyses, formulate evidence-based inquiries, or develop alternative solutions. Data-driven civic participation is often more persuasive than non-empirical or purely rhetorical advocacy and is more likely to drive substantive policy change. Such empowerment shifts democratic engagement from passive awareness to active involvement. With well-structured raw data, citizens can use tools like ChatGPT to analyze information, transforming originally dense government budgets or meeting records into accessible, plain-language insights.

Most importantly, combining AI with open data lowers the expertise barrier to public participation. Previously, only senior researchers or large interest groups had the resources to conduct large-scale data analysis. Now, any citizen with basic questioning skills can leverage AI assistance to engage in evidence-based dialogue with the government. When open data transitions from passive digital information to AI-interoperable content, enabling automated synthesis and analysis, it not only strengthens citizens’ right to information but also enhances the efficacy of transparent oversight mechanisms regardless of resource limitations, reshaping the balance of power between citizens and government.

### 5.2.3 Empowering AI with Cultural Diversity

When viewed from a global perspective, the significance of open data for AI development goes beyond a purely technical issue; it touches on fundamental matters of cultural preservation and sovereignty. The goal of the CroissantLLM project is to build a truly bilingual French model, because the team observed that models claiming to support French often only include a small amount of French data within predominantly English training corpora, resulting in performance on French tasks that lags far behind their English capabilities.

The seriousness of this issue lies in the fact that if a country’s language is underrepresented in training data, its citizens risk being marginalized or misinterpreted when using mainstream AI models. Models tend to output values and perspectives present in dominant training datasets. If historical events are deficient in localized linguistic nuances, models may rely on foreign media or biased minority sources to interpret history, leading to distorted public understanding of their own past.

ODC’s experience further highlights the complexity of handling linguistic diversity. Staff members noted in the interviews that Cambodia’s language challenges extend beyond Khmer and English to include numerous indigenous languages. If data are concentrated only on urban or dominant languages, the voices of rural communities and indigenous peoples risk disappearing from the digital sphere.

This cultural-level inequality is likely to become even more pronounced as AI applications become more widespread.

In this context, the role of government is particularly crucial.

When private enterprises tend to collect data with commercial value, governments bear the responsibility to release data that may seem niche but possess high public value-such as local gazetteers, dialect records, or infrastructure data from remote areas. Although these data may not be commercially profitable, they are an essential piece in correcting cultural biases in AI models and building a digital environment that preserves local subjectivity.

The German Commons project, which faced challenges of temporal bias, offers a similar lesson. Because copyright restrictions mean that available cultural works are largely historical documents, models trained on them may adopt outdated language and phrasing. While this problem cannot be fully resolved within existing legal frameworks, it serves as an important reminder: how should governments adjust copyright policies or data release strategies to ensure that contemporary culture is also learnable and preservable by AI models?

### 5.2.4 Towards a Sustainable Open Data Ecosystem

When civil servants realize that open data can improve their work efficiency, they become more willing to engage in these efforts. When citizens can effectively use open data to participate in public affairs, [18] the government experiences positive feedback from data release. And when AI models can more accurately understand and generate local languages and cultures, society as a whole benefits from more appropriate and effective digital services.

Carlos Alonso Peña, Director of the Spanish Data Office Division, highlighted a particularly important point about cultural change. He noted that the greatest challenge in promoting open data is not technical or legal, but organizational culture. When civil servants fear making mistakes or worry that the quality of data is insufficient and might be criticized, open data initiatives stall. However, if the narrative is reframed so that agencies understand that open data is not just about external oversight but also about internal improvement, enabling better citizen participation, and ensuring that local culture is not marginalized in the AI era, the resistance to implementation is greatly reduced.

From this perspective, integrating open data with AI is not merely a technical upgrade. It is about whether civil servants can serve citizens more effectively, whether citizens can genuinely participate in public decision-making, and whether a country’s culture and language can maintain subjectivity in the digital age. These three dimensions of empowerment together form the deeper significance of promoting open data and represent the core purpose that should always be remembered amid various technical and institutional challenges.

## 5.3 Research Limitations and Future Outlook

This study was conducted between August and December 2025. During this period, governments, civic organizations, and academic institutions worldwide continued to release more AI-ready datasets based on open data, as well as publish new policies and research findings. Due to the constraints of the project timeline, it is possible that the collection of cases and the study itself may not be fully comprehensive, and readers’ understanding is appreciated.

Most of the case studies in this report were selected and presented based on the project inventory in Chapters Two and Three and the TOE quadrant blueprint. However, as noted above, AI development across countries is rapidly evolving, and the classification of cases within the analytical matrix remains inherently dynamic. Due to time limitations, this report can only reflect the situation for the majority of the project period. Additionally, cases in the fourth quadrant-characterized by high technological development but low organizational and environmental maturity-remain relatively scarce.

Finally, this study was conducted by a Taiwanese research team, and during the process, we interviewed six experts from the public sector, civic tech communities, and AI data training communities. These experts suggested several Taiwanese cases for potential future investigation. For example, in September, the Ministry of Digital Affairs announced an AI-ready metadata framework, providing Taiwan’s government agencies with more opportunities to improve data quality and its documentation. Additionally, at the end of December, the Ministry officially released Taiwan Sovereign AI Corpus. During the same period, Switzerland also released its own sovereign AI dataset. These cases represent opportunities for the team’s future research. At the same time, Taiwanese government agencies have suggested that, for domestic cases, further integration of local contexts and dialogue with civil servants could be achieved by developing additional operational toolkits or checklists highlighting key aspects of certain cases. This is also the direction our team hopes to pursue in future dialogues.

## 5.4 Conclusion

This report hopes that by documenting these cases, it can serve as a mirror to help public sector workers understand their own roles. Through these writings and the close-to-practice international examples, each agency and every officer can recognize their current position and understand that, even when still in the early stages or facing obstacles, their efforts carry public value. Open data and AI are not solely the domain of technical units or early adopters; they are a collective endeavor in which everyone involved in public service can gradually participate and steadily contribute.

At the same time, this report is intended to serve as a ’communication material’ between the government and civil society. For NGOs and civic tech communities, when engaging with government agencies of varying maturity levels and knowledge backgrounds, it provides concrete examples of ’how to get started,’ ’how others have progressed,’ and ’which paths are feasible and adaptable.’ Such dialogue moves beyond abstract advocacy and is grounded in practical experience and actionable steps.

Future researchers and policymakers are invited to view these cases as a starting point for ongoing dialogue. As AI technologies, regulatory environments, and societal expectations continue to evolve, governance models for open data will inevitably need continuous adjustment and redesign.

Only by establishing long-term collaboration and feedback mechanisms among government, academia, and civil society can this ecosystem grow sustainably. The more people can see their own roles along this path and understand each other’s constraints and expertise, the more open data can truly become a sustainable public infrastructure. This is not the responsibility of any single party, but a collective effort that must be shared and is worth achieving together.
