# Chapter 4: What Environments, Policies, and Adaptive Actions Are Essential to Advance AI-Ready Data

_Source: OCF-AI-en.pdf, pp. 19-23._

## Figures

![English chapter 4 main visual showing data governance and legal frameworks](../assets/en-ch4-main-visual.png "英文版 Chapter 4 main visual")

This chapter uses the TOE analysis framework to examine the cases collected in this study, highlighting the institutional, organizational, and environmental contexts that enable open data to gradually transition toward AI-interoperable frameworks. By comparing different countries and cases, the research team aims to show that there is no single perfect institutional environment for achieving AI-ready data. Rather, different governance models can develop implementation approaches suited to their contexts. The chapter further examines how each case advances AI-ready data initiatives through institutional design and organizational collaboration within existing governance structures, regulatory regimes, and available policy support.

## 4.1 Legal Frameworks and Social Institutions for AI-Ready Data

This section focuses on the environmental context in the TOE analysis framework, examining how legal systems and social governance structures define the parameters for the evolution of open data into AI-ready assets. The environmental context considers not only the mere presence of regulations or institutions but also the broader social landscape, including the comprehensiveness of data-related legal concepts, public awareness and expectations regarding privacy and personal data protection, the implementation of copyright and licensing systems, and the social trust foundation for data use and AI development. Through case analyses, this section illustrates how different legal frameworks and social institutions influence the feasibility of data release, the operational space available to organizations, and the practical approaches used to promote AI-ready open data.

### 4.1.1 Clear Legal Frameworks for Open Data

#### 4.1.1.1 Policies and Legislation Supporting Public Information Disclosure

The data acquisition processes of CroissantLLM and Parla clearly demonstrate that a well-established open data legal framework can reduce communication costs for developers and improve operational efficiency, paving the way for AI-driven research. CroissantLLM researcher Manuel Faysse noted in the interview that France’s open data initiative significantly enhances the efficiency of data accessibility.

Because the government has released a large volume of data under permissive licenses, team members openly stated that data licensing ’was not a challenge for us; the model development process only required minimal cleaning of these open datasets.’ Ingo Hinterding, the product lead for Parla, emphasized that ’as long as the research team is handling publicly available data that does not require special protection, the development process is significantly accelerated.’ In some countries, citizens who wish to access government data must obtain formal written clearance from the relevant agency. In practice, however, citizens may not know which agency to contact and therefore cannot obtain the data. In rare cases, even if developers receive verbal permission from an agency, the uncertainty of such informal agreements can generate unforeseen institutional liabilities and operational risks.

#### 4.1.1.2 Correctly Choosing Appropriate Licensing Terms

While a country's policies or legal framework are certainly important, in practice, the primary operational prerequisite lies in correctly labeling datasets with the ’right’ licensing terms. Each license type imposes different rules and restrictions on use, and these differences affect whether a dataset can be lawfully and practically included in AI training corpora. Common licensing terms specify whether the data can be used for commercial purposes, whether modifications or derivative works are allowed, or whether attribution is required. Over time, standardized licenses have emerged internationally, such as Creative Commons (CC) licenses and open government data licenses. Governments need to evaluate stakeholder requirements to designate licensing frameworks that provide the greatest benefit to the public.

In the case of France’s CroissantLLM, it can be observed that the French government had already pre-labeled the licensing terms for datasets on the platform when releasing open data.

This allowed the team to identify training-eligible datasets from a large portal based on the stated license conditions, thereby reducing avoidable legal uncertainty and rework.

#### 4.1.1.3 Clear and Coherent Regulatory Framework

In the previous two sections, this study discussed the importance of licensing terms and supportive policies or legislation. Now we turn to the broader regulatory framework.

When public agencies implement policies or adopt new legislation, failing to clarify relationships and potential conflicts among statutes can leave civil servants uncertain about how to proceed.

For example, public institutions in Spain must simultaneously comply with the Directive on the Re-Use of Public Sector Information (PSI Directive), the General Data Protection Regulation (GDPR), the Data Governance Act (DGA), the European Data Act, and the emerging AI Act. Without a clear hierarchy or prioritization among these laws, a ’spaghetti bowl of compliance’ situation arises. Regulatory ambiguity and perceived compliance risks can lead agencies to hesitate or even refuse to release data.

To address this issue, the European Commission has launched a Legislative Consolidation initiative. The EU aims to unify definitions across various regulations-for instance, clarifying how the GDPR’s ’legitimate interest’ [17] lawful basis may be interpreted in AI training contexts-and to simplify reporting obligations by implementing a ’report once’ principle. These measures are intended to reduce barriers to promoting open data.

#### 4.1.1.4 Summary

The cases demonstrate that combining an open data system with clearly defined licensing terms and supportive legislation helps research teams focus on AI development without being burdened by complex application procedures. A dataset that is clear and consistent is of higher utility than a large dataset with ambiguous terms. The overlapping regulatory issues in Spain also highlight that a lack of legal integration can cause public agencies to hesitate due to risk concerns.

### 4.1.2 Demonstrating the Value of Open Data to Promote Substantive Collaboration

Cambodia has not yet passed a law on government information disclosure or similar legislation granting citizens the legal right to request government data. Regarding personal data protection, although a bill has been discussed for nearly a decade, the legislative process has been slow due to negotiations and compromises among multiple stakeholders. In contrast, the country has already released a draft national AI strategy, identifying priority sectors such as education, agriculture, and manufacturing. However, documents about this strategy drafts remain at an early stage and have not yet been translated into concrete regulations or implementation guidelines. Despite this context, the civil society organization ODC has attempted to make breakthroughs, and its experiences offer valuable lessons.

#### 4.1.2.1 Understanding the Need of Government

ODC employs a non-adversarial advocacy strategy, offering bespoke technical facilitation to each government agency to build trust and encourage voluntary data sharing.

This voluntary, rather than mandatory, approach makes Cambodian government departments more willing to open data, as they do not perceive data requests as a threat to their authority.

For example, in the case of publicizing Economic Land Concessions data, ODC integrated disaggregated information from different departments to create comprehensive maps, helping define land boundaries and prevent conflicts. This work enabled relevant Cambodian agencies to clearly delineate each concession area, confirm boundaries with environmental protection zones, and avoid overlaps or disputes between different land uses. ODC’s intention was not primarily to retrieve restricted data, but to provide technical facilitation by consolidating and visualizing dispersed departmental information. During this coordination process, as the government recognized that cross-departmental integration could reduce decision-making errors and improve efficiency, previously restricted land information gradually became accessible. This model, starting from governmental needs to facilitate cross-agency information flow, not only addresses immediate issues but also transforms cleaned and structured spatial data into valuable local datasets for future AI models in land forecasting or resource planning.

#### 4.1.2.2 Positive Public-Private Collaboration Cases Promote Legislation

Even more encouraging is that successful public-private collaboration can help drive legislation, filling gaps in national legal frameworks.

After the Economic Land Concessions data were made public in Cambodia, its impact extended further. Land designated as concession areas often encroached on indigenous communities, causing disputes. With map visualizations, indigenous groups could clearly see which lands were under threat and advocate for their protection with the government.

For government agencies, these tools revealed policy blind spots, prompting departments to enhance land administration and optimize resource allocation. International investors and civil society organizations could also use the open data to conduct rigorous impact assessments regarding investment impacts. These experiences provide concrete evidence and justification for future legislation.

#### 4.1.2.3 Summary

After understanding the benefits and operational practices of open data, policymakers became more confident in promoting legal reforms. According to the interview with ODC, the Cambodian government has recognized the problem of inconsistent data structures across departments and has begun discussions on establishing a unified governance framework. ODC’s experience, including data format design, quality management, and balancing openness with protection, has provided valuable reference points for policymakers.

## 4.2 Comparative Analysis of Collaboration Models

This section focuses on the organizational context in the

TOE analysis framework, examining the practical challenges faced in cross-organization and inter-agency collaboration during the promotion of open data and AI-ready initiatives.

The organizational context emphasizes differences among participating units in organizational culture, roles and responsibilities, resource allocation, and decision-making processes, all of which directly affect whether data can be seamlessly released and reused.

In practice, different government agencies may adopt disparate institutional dispositions and approaches to open data due to differences in their operational goals, risk tolerance, and understanding of data openness. At the same time, when civil society or academic institutions participate in data initiatives, differences in organizational culture and work pace can also influence communication efficiency and collaborative outcomes. Therefore, establishing clear collaboration mechanisms and role definitions becomes a critical task in promoting open data and AI-ready data initiatives.

### 4.2.1 Establishing Institutionalized Inter-Agency Collaboration within Government

Berlin’s Parla project established a long-term collaboration framework spanning both administrative and legislative branches, rather than merely a simple procurement relationship. Through regular innovation grants from the Berlin Senate, administrative agencies empowered CityLAB to act as a ’bridge between information technology and government departments,’ enabling the innovation lab to operate cross-functionally and integrate parliamentary records with the operational data of various Senate offices.

Essentially, this grant mechanism represents an investment in "collaborative infrastructure." Spain’s ImpulsaDATA initiative demonstrates another model of achieving inter-agency collaboration through institutionalization. The Spanish government established the Data Office as a centralized administrative node. Leveraging a statutory national data framework and annual reporting mechanisms, the office elevated simple inter-agency consultation into a legal obligation. Within the ImpulsaDATA framework, the Data Office does not merely provide advice; it standardizes a process, from diagnosis and gap analysis to concrete action, translating complex EU regulations into actionable plans for government agencies.

### 4.2.2 Integrating Needs through a Bottom-Up Approach

As previously noted in the case studies, CityLAB conducted

’AI Ideas Workshop’ sessions, inviting Berlin administrative staff to collaboratively discuss ’which routine tasks could be supported by AI?’ Participants highlighted that receiving and responding to parliamentary written inquiries was a time-consuming task that consumed significant resources.

CityLAB therefore addressed this specific operational bottleneck directly, without needing additional persuasion for administrative adoption. This development model, which integrates user needs from the conceptual stage, ensured the project’s practical relevance. A similar approach can be seen in Cambodia with ODC.

ODC provides technical support and training to government agencies willing to collaborate, helping them improve data management capabilities in a mutually beneficial way. This direct technical facilitation allows agencies to experience the benefits of cooperation, making them more willing to adopt a proactive approach to data release. For example, the Ministry of Post and Telecommunications and the Ministry of Environment were relatively open, inviting ODC to participate in policy draft discussions and, under certain conditions, share data; the Ministry of Planning also accepted technical training and support offered by the organization. Both cases demonstrate that, beyond technical development skills, the ability to understand practical needs and engage in cross-domain dialogue is crucial.

### 4.2.3 Selection of Data Topics

#### 4.2.3.1 Consider the Complexity of the Data Topic

In general, different data topics imply that organizations must handle varying levels of complexity inherent in the data itself.

Before discussing data selection strategies, the experience of the German Commons provides an important point of reference for this study: when facing vast potential data sources, systematic topic selection and strategic prioritization remain essential. Prior to deciding which sources to select, it is also necessary to gain a broad understanding of the existing data sources worldwide in order to choose the most representative datasets.

From the outset, the German Commons team established clear domain boundaries: law, science, culture, politics, news, economics, and web texts, ultimately collecting 154.56 billion tokens from 41 sources. While this seems like a massive amount, it is attributed to careful selection. The team explicitly stated that their strategy was to choose the "largest and most representative single source" in each domain, rather than attempting to include all available datasets.

However, it is equally important to understand what data sources exist globally at the start. For example, in the cultural domain, although German is Germany’s primary language, high-quality German content does not exist solely within Germany. National libraries in Switzerland and Austria also hold rich German-language materials with open licenses.

However, because the team only expanded their perspective to these cross-border sources later in the project, they had to undergo iterative refinements of their data processing workflows. This experience illustrates that at the initial stage, implementers should adopt a transnational perspective, conduct cross-jurisdictional assessments, and map all institutional data holders globally. This ’comprehensive first, filter later’ approach not only ensures the completeness of data coverage but also effectively avoids the sunk costs associated with retrospective data integration.

#### 4.2.3.2 Emphasizing Data Applications to Lower Government Concerns about Releasing such Data

Although both the German Commons and ODC use government open data to produce AI-training datasets and pay close attention to topic selection, their purposes are entirely different. The German Commons’ topic selection strategy is primarily driven by ensuring data quality, whereas ODC approaches topic selection from the perspective of facilitating access to government data, especially when open data involves areas such as fiscal revenue, mining rights, or land interests.

In the interview, ODC noted that datasets related to taxation or mineral extraction involve conflicting institutional and commercial interests, making government agencies more cautious or even conservative, often deflecting responsibility when faced with data requests. For example, when requesting mining revenue data, the Ministry of Mines and Energy would state that they do not hold the data and refer the request to the Ministry of Economy and Finance, while the Ministry of Economy and Finance would respond that they only have aggregate figures, not detailed company-level data.

This institutional responsibility deflection reflects that when data involve sensitive commercial interests or government revenue, agencies tend to adopt the most conservative stance.

In response to this situation, ODC developed a strategic, gradual approach. For more conservative agencies, the organization does not apply pressure, but instead first builds trust in areas that are less directly tied to economic interests or political sensitivity, such as environmental data, telecommunications policy, and development planning, and waits for the right moment to make data requests. The partnership with the Ministry of Environment is a successful example. At the outset, the ministry was cautious about ODC’s requests. Through sustained engagement over time, the ministry came to recognize that ODC handled released data responsibly and in the public interest. As a result, the ministry became more willing, under specified conditions-to share environmental impact assessment reports. Although not all reports can be made public, at least a channel for dialogue and negotiation has been established.

This difference reflects an important reality: the sensitivity of a data topic is closely tied to an agency’s willingness to open it, and promotion strategies must be adapted to local conditions. From the German Commons’ experience, this study observes that even in legally favorable environments with relatively clear data licensing, strategic topic selection and data curation are necessary to ensure dataset quality and usability. ODC’s experience further reminds us that within nascent regulatory landscapes, topic selection is not merely a technical issue but also a matter of building trust and facilitating collaboration. Starting with less sensitive domains and gradually establishing successful cases often provides an effective pathway to unlock access to additional data sources.

### 4.2.4 Summary

Effective collaboration is key to the success of open data initiatives and AI applications. Whether within government agencies or in partnership with civil society organizations, establishing trust and shared understanding is essential.

This study identifies the following factors for successful collaboration:

1. Technical capability is important, but understanding needs and communicating effectively are equally indispensable.
2. A bottom-up, demand-driven approach can promote collaboration and enhance the practical relevance of outcomes.
3. Adjusting strategies according to institutional environments and data sensitivity helps address challenges. Institutional design and flexible collaboration models are complementary, and both can produce tangible results.

For government agencies considering the integration of open data and AI, the message from these experiences is clear: collaboration is a necessary condition for success, whether it is cross-agency cooperation within the public sector or public-private partnerships among stakeholders. Sincerely understanding each other’s needs and constraints, and finding shared values and goals on that basis, is essential. Once mutual understanding and trust are established, data can flow more smoothly, technology can be applied more effectively, and broader socioeconomic benefits become more achievable.
