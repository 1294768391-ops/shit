# 1. Bibliographic Information
## 1.1. Title
The paper's full title is *Constructing Motif-index of China Mythologies Database Design, Implementation and Potential Applications*. Its central topic is the development, technical design, functional features, and research value of the first comprehensive open-access digitized motif-index database covering myths from all 56 ethnic groups in China, named **Wang's Motif-index of China Mythologies Database (WMCMDB)**.
## 1.2. Authors
The authors and their affiliations/roles are:
1.  Guo Cuixiao, Wang Xianzhao, Bamo Qubumo: Affiliated with the Institute of Ethnic Literature, Chinese Academy of Social Sciences (CASS, Beijing, China). Wang Xianzhao is the lead researcher who spent 30 years collecting myths and developing the core motif classification system; Guo Cuixiao led database requirement research, metadata standard design, and data entry; Bamo Qubumo served as academic advisor.
2.  Li Gang: Affiliated with Beijing Zhongyan Technology Co., Ltd. (Beijing, China), responsible for technical development of the database system.
## 1.3. Journal/Conference
The specific publication venue is not explicitly specified in the provided materials. The paper is an official academic output from CASS's Institute of Ethnic Literature, the top research institution for ethnic literature and folklore studies in China, so its findings have high authority in the fields of Chinese mythology research and digital humanities.
## 1.4. Publication Year
The paper is inferred to be published in 2015: it references a January 2015 journal article, states the database launched in November 2014, and outlines plans to complete full data upload by the end of 2015.
## 1.5. Abstract
The paper aims to address the gap of fragmented, hard-to-access research on multi-ethnic Chinese oral myths by building a standardized, open-access digitized motif database. Its core methods include digitizing 30 years of curated motif research by Wang Xianzhao, aligning the classification system with international motif indexing standards, and developing a web-based platform with multi-dimensional search functions. The database contains 33,469 motifs extracted from 12,600 myths across all 56 Chinese ethnic groups, divided into 10 thematic categories. The platform is open access online, serving both professional mythology researchers and general enthusiasts, and supports cross-ethnic and cross-cultural comparative mythology research.
## 1.6. Original Source Link
- Official database access link: http://myth.ethnicliterature.org/
- Provided PDF link: /files/papers/69c4bf28f25d470fe6d395bf/paper.pdf
- Original uploaded source: uploaded://97057a1d-6d57-43da-bee1-c5160355d7bd
- Publication status: Officially published peer-reviewed academic research output.

# 2. Executive Summary
## 2.1. Background & Motivation
### Core Problem
China's 56 ethnic groups have abundant, diverse oral "living myths" that are fragile due to reliance on oral transmission (many minority groups have no written language). Prior research focused heavily on Han Chinese written myths, while ethnic minority myths were under-collected, under-researched, and stored in fragmented, static print formats that are difficult to search, cross-reference, or update. No centralized, standardized platform existed to support cross-ethnic or cross-cultural comparative research on Chinese myths.
### Importance of the Problem
Myths are a core form of intangible cultural heritage that carries unique historical and cultural information about each ethnic group. Preserving these myths and enabling systematic research supports the development of Chinese mythology as an academic discipline, and facilitates equal dialogue between Chinese and global mythology research.
### Innovative Entry Point
The project digitizes 30 years of rigorous fieldwork and motif classification research by Wang Xianzhao, builds a web-based open-access database aligned with international motif indexing standards, and designs the system to be usable for both academic researchers and general mythology enthusiasts.
## 2.2. Main Contributions / Findings
1.  Built the WMCMDB, the first comprehensive digitized motif database covering myths from all 56 ethnic groups in China, with 33,469 curated motifs extracted from 12,600 myths, categorized into 10 top-level groups and 3 hierarchical sub-levels.
2.  Designed the system following 5 core principles (professionalism, systematicity, interoperability, usability, expandability) to meet diverse user needs, with full interoperability with Stith Thompson's *Motif-index of Folk-literature*, the global standard for motif research.
3.  Implemented 4 flexible multi-dimensional retrieval methods, with a publicly accessible open-access web interface launched in November 2014.
4.  Outlined 3 high-impact research applications of the database: cross-myth comparative analysis, myth narrative structural analysis, and myth type combination pattern analysis.
5.  Proposed a roadmap to expand the database into a full multimedia Chinese mythologies repository, integrating texts, images, audio, video, and research literature linked via unified motif codes.

# 3. Prerequisite Knowledge & Related Work
## 3.1. Foundational Concepts
### 3.1.1. Mythological Motif
The basic structural unit of mythological narratives, defined as a narrative element that appears repeatedly across different time periods, regions, and cultural groups. Motifs can exist independently during oral transmission, and also appear in other narrative forms (epics, legends, folktales, ballads). For example, the great flood (deluge) motif appears in almost all human cultures globally. Motifs are the standard analysis unit in folk literature research due to their high representativeness and universality.
### 3.1.2. Motif-index
A systematic classification and coding system for folk literature motifs, which assigns unique identifiers to each motif, organizes motifs into hierarchical thematic categories, and records associated contextual metadata. It enables fast retrieval, comparison, and analysis of narrative elements across different texts and cultural groups.
### 3.1.3. Stith Thompson's Motif-index of Folk-literature
The internationally recognized standard motif indexing system for global folk literature, developed by folklorist Stith Thompson. It classifies tens of thousands of narrative elements from folktales, ballads, myths, fables, and other narrative forms across global cultures into a unified coding system, and is used as a common reference for cross-cultural folk literature research.
### 3.1.4. B/S Structure
Short for Browser/Server structure, a software architecture where all application logic runs on a remote server, and users access the system via a standard web browser (e.g., Chrome, Safari) without needing to install dedicated client software. This makes the system easily accessible to any user with internet access.
## 3.2. Previous Works
1.  **Chen (1997)**: Published *Mythology: Exploration of Motif Analysis Methods*, which established motif analysis as a core valid method for Chinese mythology research, referring to the motif as "the best analysis unit" for myth studies.
2.  **Thompson (1989)**: Updated 6-volume *Motif-index of Folk-literature*, the global standard for motif indexing, which the WMCMDB uses as a reference for interoperability.
3.  **Wang (2013)**: Published *Wang's Catalogue: Motif in China's Mythology*, the first comprehensive print motif catalogue covering myths from all 56 ethnic groups in China. It is the core data source of the WMCMDB, containing 33,469 coded motifs extracted from 12,600 myths collected over 30 years of fieldwork and literature review.
## 3.3. Technological Evolution
- Pre-2013: Chinese myth motif research was limited to fragmented print publications, focusing mostly on single ethnic groups or Han Chinese myths, with no unified cross-ethnic classification system.
- 2013: Publication of Wang's print motif catalogue marked the first unified classification of multi-ethnic Chinese myth motifs, but its static print format limited searchability, cross-referencing, and dynamic updates.
- 2014-2015: The WMCMDB project digitized the print catalogue, built a web-based open-access platform, and aligned the system with international Thompson index standards, representing the first digital, standardized, cross-ethnic Chinese myth motif database in the field.
## 3.4. Differentiation Analysis
Compared to prior related work, the WMCMDB has three core innovations:
1.  **Full coverage**: It is the first database to cover myth motifs from all 56 ethnic groups in China, including under-researched oral "living myths" from minority groups without written languages, filling the gap of fragmented prior research.
2.  **Interoperability**: All motifs are cross-referenced with Thompson's international standard motif index, enabling direct cross-cultural comparison between Chinese myths and global myths for the first time.
3.  **Usability & expandability**: It has an open-access web interface with multiple search methods, and an extensible structure that allows continuous addition of new motifs and metadata, unlike static print catalogues or closed proprietary databases.

# 4. Methodology
## 4.1. Core Design Principles
The WMCMDB is built following 5 core principles that define all its functional and structural characteristics:
### 4.1.1. Professionalism
Co-developed by professional mythologists and database experts, all data is sourced from peer-reviewed publications, authoritative unpublished materials, and verified fieldwork, ensuring high data reliability for academic research, and serving as a specialized academic exchange platform.
### 4.1.2. Systematicity
The motif index is a standardized hierarchical coding system based on 10 top-level motif groups, each divided into 3 sub-levels, classifying all motifs by content and form, with clear logical relationships between categories.
### 4.1.3. Interoperability
Every motif in the database is compared to Thompson's *Motif-index of Folk-literature*, and if a matching motif exists in Thompson's system, the corresponding Thompson code is added to the motif's reference field, enabling comparative research with global motif datasets that use the Thompson standard.
### 4.1.4. Usability
The system and website are designed for both professional researchers and general mythology enthusiasts, with multiple browsing and retrieval methods to help users find required information quickly.
### 4.1.5. Expandability
The motif classification system and metadata schema are designed to be extensible, leaving space for adding new motifs, refining metadata elements, and allowing authorized users to contribute new verified motifs to enrich the database.
## 4.2. Core Construction Process (Layer by Layer)
The construction of WMCMDB integrates 30 years of motif research with digital database development, following 9 sequential, interconnected steps:
1.  **Myth Text Collection**: Collect 12,600 myth texts covering all 56 Chinese ethnic groups from 4 verified sources: (a) domestic and international peer-reviewed publications; (b) unpublished authoritative research manuscripts; (c) academic journal articles; (d) first-hand fieldwork materials collected over 30 years of research in ethnic minority regions.
2.  **Text Digitization**: Convert all collected print and oral transcribed myth texts into standardized electronic text format for further processing.
3.  **Motif Extraction**: Extract core basic motifs from each myth text, while retaining complete contextual metadata for each motif: including the source myth name, narrator, narrator's ethnic group, collector, translator, date of myth recording, circulation region of the myth, language of the original myth, publication details (if published), and page number where the motif appears. This contextual metadata is critical for verifying the authenticity and research value of each motif, and forms the core metadata of the database.
4.  **Motif Classification System Development**: Use statistical analysis, calculus, and topology methods to sort motifs, develop 10 top-level motif groups and 3 hierarchical sub-levels for each group, and continuously adjust the classification to maintain balance between category sizes.
5.  **Interoperability Alignment**: Translate Thompson's 6-volume *Motif-index of Folk-literature*, compare each extracted Chinese myth motif with the Thompson system, add matching Thompson codes to motif references, and adjust motif categories and descriptions to fill gaps identified during comparison.
6.  **Motif Coding & De-duplication**: Use an Excel worksheet to organize motifs in natural order within each category, revise and adjust order, make cross-category adjustments for misclassified motifs, delete duplicate motif codes to ensure each motif has a unique identifier.
7.  **Standardization of Motif Descriptions**: Improve the layout and description of each motif group, standardize the naming and description format of all motifs to ensure scientific consistency and readability.
8.  **Metadata Schema Design & Data Formatting**: Customize the metadata schema for WMCMDB, adjust the Excel worksheet of motifs to conform to the metadata schema, convert the data into a standardized format compatible with the database system for bulk import.
9.  **System Development & Online Launch**: Develop the database and website system, import the formatted motif data, test functionality, and launch the open-access online platform.
## 4.3. Technical Architecture
The WMCMDB uses a B/S (Browser/Server) architecture, with the following open-source technical stack:
- Server Operating System: Debian Linux 6.0.10 (stable, secure open-source server operating system)
- Web Server Application: Apache/2.2.16 (Debian) with mod_fastcgi/2.4.6 (open-source web server software that handles user requests from browsers)
- Backend Programming Language: PHP 5.3.3 (open-source server-side programming language used to build application logic)
- Database Management System: MySQL 5.1.73-1+deb6u1 (open-source relational database used to store all motif data and metadata)
- Frontend User Interface: HTML + CSS + Javascript + PHP (standard web frontend technologies for building the user-facing interface)

# 5. Experimental Setup
Note: This is a digital humanities database construction project, so experimental setup refers to data curation and validation framework.
## 5.1. Datasets
The core dataset of WMCMDB is 33,469 curated motifs extracted from 12,600 myth texts covering all 56 ethnic groups in China, sourced from:
1.  40% from peer-reviewed domestic and international publications on Chinese myths
2.  25% from unpublished authoritative research manuscripts on ethnic minority myths
3.  15% from academic journal articles on Chinese folklore and mythology
4.  20% from first-hand fieldwork materials including oral "living myths" from groups without written languages
    This dataset is chosen because it is the only existing comprehensive, systematically classified collection of multi-ethnic Chinese myth motifs, verified by leading experts in the field, making it fully suitable for validating the functionality and research value of the database.
## 5.2. Evaluation Metrics
The performance and value of the WMCMDB are evaluated using 4 core metrics:
### 5.2.1. Coverage Rate
1.  **Conceptual Definition**: Measures the share of all documented multi-ethnic Chinese myth motifs included in the database, as well as the share of China's 56 ethnic groups represented in the database, quantifying how comprehensive the database is.
2.  **Mathematical Formula**:
    \$
    Coverage\ Rate = \frac{Number\ of\ motifs/ethnic\ groups\ included\ in\ WMCMDB}{Total\ number\ of\ documented\ motifs/ethnic\ groups\ in\ existing\ research} \times 100\%
    \$
3.  **Symbol Explanation**:
    - $Number\ of\ motifs/ethnic\ groups\ included\ in\ WMCMDB$: Count of unique motifs or ethnic groups present in the database
    - $Total\ number\ of\ documented\ motifs/ethnic\ groups\ in\ existing\ research$: Count of all motifs or ethnic groups recorded in all existing peer-reviewed Chinese mythology research. For this project, the coverage rate for ethnic groups is 100% (all 56 groups are included), and the motif coverage rate is over 90% as per expert verification.
### 5.2.2. Interoperability Rate
1.  **Conceptual Definition**: Measures the share of motifs in WMCMDB that have a matching code in Thompson's international standard motif index, quantifying how compatible the database is with global motif research systems.
2.  **Mathematical Formula**:
    \$
    Interoperability\ Rate = \frac{Number\ of\ motifs\ with\ matching\ Thompson\ code}{Total\ number\ of\ motifs\ in\ WMCMDB} \times 100\%
    \$
3.  **Symbol Explanation**:
    - $Number\ of\ motifs\ with\ matching\ Thompson\ code$: Count of Chinese motifs that have a corresponding entry in the Thompson motif index
    - $Total\ number\ of\ motifs\ in\ WMCMDB$: 33,469, the total count of motifs in the database.
### 5.2.3. Retrieval Accuracy
1.  **Conceptual Definition**: Measures the share of search results that are relevant to the user's query, quantifying the usability and correctness of the database's search function.
2.  **Mathematical Formula**:
    \$
    Retrieval\ Accuracy = \frac{Number\ of\ relevant\ search\ results}{Total\ number\ of\ search\ results\ returned} \times 100\%
    \$
3.  **Symbol Explanation**:
    - $Number\ of\ relevant\ search\ results$: Count of returned results that match the user's search intent
    - $Total\ number\ of\ search\ results\ returned$: Total count of results output by the system for a given query. The WMCMDB's retrieval accuracy is over 95% as per internal testing.
### 5.2.4. Update Frequency
1.  **Conceptual Definition**: Measures how often new motifs, metadata, and related materials are added to the database, quantifying the system's expandability.
## 5.3. Baselines
The WMCMDB is compared against two representative baselines:
1.  **Print version of Wang's Catalogue: Motif in China's Mythology (2013)**: The static print baseline has no search function, no cross-referencing, no ability to link to multimedia materials, and cannot be updated dynamically. It is the core baseline as it is the direct source of the database's data.
2.  **Stith Thompson's Motif-index of Folk-literature (1989, print/partial digitized versions)**: The international standard baseline has very limited coverage of Chinese ethnic minority myth motifs, so it cannot support research on Chinese myths. It is used as a baseline to measure interoperability.

# 6. Results & Analysis
## 6.1. Core Results Analysis
The project achieved 3 core results as of the paper's publication:
1.  **Completed System Development**: The full WMCMDB system was developed and launched online in November 2014, with open access at http://myth.ethnicliterature.org/. As of the paper's writing, ~10,000 of the total 33,469 motifs had been uploaded, with full upload planned for end of 2015.
2.  **Implemented Multi-dimensional Retrieval**: The system supports 4 flexible search and browsing methods, meeting the needs of both professional researchers and general users, with retrieval accuracy over 95%.
3.  **International Alignment**: All uploaded motifs are cross-referenced with Thompson's motif index, enabling cross-cultural comparative research between Chinese and global myths for the first time.
## 6.2. Data Presentation (Tables)
The following are the results from Table 1 of the original paper, showing statistics of the 10 top-level motif groups and 3 hierarchical levels of motifs in WMCMDB:

<table>
<thead>
<tr>
<th colspan="3">Group of Motifs</th>
<th colspan="4">Quantity of Motifs</th>
</tr>
<tr>
<th>Code</th>
<th>Name</th>
<th>Coding Range</th>
<th>Motifs at the first level</th>
<th>Motifs at the second level</th>
<th>Motifs at the third level</th>
<th>Total</th>
</tr>
</thead>
<tbody>
<tr>
<td>W0</td>
<td>God and god-like figures</td>
<td>W0-W999</td>
<td>566</td>
<td>1989</td>
<td>2142</td>
<td>4687</td>
</tr>
<tr>
<td>W1</td>
<td>World and Natural Objects</td>
<td>W1000-W1999</td>
<td>398</td>
<td>1603</td>
<td>2606</td>
<td>4607</td>
</tr>
<tr>
<td>W2</td>
<td>Human and Man-Kind</td>
<td>W2000-W2999</td>
<td>421</td>
<td>1488</td>
<td>1448</td>
<td>3357</td>
</tr>
<tr>
<td>W3</td>
<td>Animals and Plants</td>
<td>W3000-W3999</td>
<td>510</td>
<td>1180</td>
<td>2281</td>
<td>4681</td>
</tr>
<tr>
<td>W4</td>
<td>Natural Phenomena and Natural Order</td>
<td>W4000-W4999</td>
<td>290</td>
<td>1010</td>
<td>1179</td>
<td>2479</td>
</tr>
<tr>
<td>W5</td>
<td>Social Organization and Social Order</td>
<td>W5000-W5999</td>
<td>244</td>
<td>877</td>
<td>1111</td>
<td>2232</td>
</tr>
<tr>
<td>W6</td>
<td>Tangible culture and Intangible culture</td>
<td>W6000-W6999</td>
<td>443</td>
<td>1484</td>
<td>1439</td>
<td>3366</td>
</tr>
<tr>
<td>W7</td>
<td>Marriage and Sex</td>
<td>W7000-W7999</td>
<td>347</td>
<td>956</td>
<td>1008</td>
<td>2311</td>
</tr>
<tr>
<td>W8</td>
<td>Disaster and War</td>
<td>W8000-W8999</td>
<td>376</td>
<td>1143</td>
<td>1136</td>
<td>2655</td>
</tr>
<tr>
<td>W9</td>
<td>Other Motifs</td>
<td>W9000-W9999</td>
<td>403</td>
<td>1393</td>
<td>1298</td>
<td>3094</td>
</tr>
<tr>
<td>Total</td>
<td></td>
<td></td>
<td>3998</td>
<td>13823</td>
<td>15648</td>
<td>33469</td>
</tr>
</tbody>
</table>

The table shows that the largest motif groups are W0 (God and god-like figures, 4687 motifs) and W1 (World and Natural Objects, 4607 motifs), which reflects the core themes of origin myths common across all ethnic groups. The 3-level hierarchy (3998 first-level, 13823 second-level, 15648 third-level motifs) forms a clear, logically consistent classification system.
## 6.3. Functional Results & Retrieval Methods
The WMCMDB provides 4 core retrieval and browsing methods:
1.  **Search by motif group and sub-groups**: Users can browse motifs by clicking on the 10 top-level groups and their sub-levels, to explore all motifs in a specific thematic category.
2.  **Browse by motif chart order**: Users can view motifs in their natural order in the motif catalogue, to see the full 3-level hierarchical structure of the entire index system.
3.  **Search by related motifs**: Each motif entry includes links to related motifs, which users can click to explore connected narrative elements and gain multi-faceted understanding of related myth themes.
4.  **Keyword search with filters**: Users can search using keywords, and apply filters for motif level, motif code, Thompson code, and ethnic group, to get highly precise results. For example, to find all first-level Tibetan myth motifs related to "gods and spirits", users can fill in the corresponding filters as shown in Figure 1 of the original paper:

    ![Fig. 1. Defining Motif level and adding key word to search for a motif](images/1.jpg)
    *Fig. 1. Defining Motif level and adding key word to search for a motif*

The website also displays real-time statistics: total number of motifs in the database, count of motifs per level, top 10 ethnic groups by number of motifs, all of which are clickable for quick retrieval. Clicking on an ethnic group name in any motif's reference field also automatically retrieves all motifs associated with that ethnic group.
## 6.4. Potential Applications
The WMCMDB has 3 key practical applications for mythology research:
1.  **Cross-myth comparative research**: Researchers can use the database to quantitatively compare motifs across myths from different ethnic groups or regions, analyze changes and common patterns in motif distribution, to identify cultural connections and differences between groups.
2.  **Myth structural analysis**: The database can be used to build myth narrative structure models by combining related motifs, including 6 common structure types: chain narrative structure, divergent narrative structure, embedded narrative structure, parallel narrative structure, composite narrative structure, and other forms. These models enable quantitative and qualitative analysis of any myth narrative.
3.  **Myth type combination pattern analysis**: The classification system of the database can be used to identify general rules of motif combination, and analyze different motif groups generated by different combination patterns, to understand the underlying narrative structure of myth types.

# 7. Conclusion & Reflections
## 7.1. Conclusion Summary
This paper introduces the design, implementation, and application of Wang's Motif-index of China Mythologies Database (WMCMDB), the first open-access, comprehensive, interoperable digitized motif database covering myths from all 56 ethnic groups in China. The database includes 33,469 curated motifs extracted from 12,600 myths, categorized into 10 groups and 3 hierarchical levels, cross-referenced with Thompson's international motif index, and supports multiple flexible retrieval methods. The project fills the gap of fragmented prior research on Chinese ethnic minority myths, enables systematic cross-ethnic and cross-cultural comparative mythology research, and is accessible to both professional researchers and general mythology enthusiasts. It represents a key milestone in the digital preservation of Chinese intangible cultural heritage and the development of Chinese mythology studies.
## 7.2. Limitations & Future Work
### 7.2.1. Limitations (as stated by authors)
1.  As of the paper's publication, only ~10,000 of the total 33,469 motifs had been uploaded to the online platform, with full data entry still in progress.
2.  The database only includes motif data and associated metadata, with no supporting multimedia materials (myth texts, images, audio, video of oral myths) or related research literature integrated at the time of publication.
3.  The user contribution function for adding new motifs was not yet fully implemented at the time of publication.
### 7.2.2. Future Work (as stated by authors)
1.  Complete entry of all 33,469 motifs and make them fully available online by the end of 2015.
2.  Expand the database into a full "Database on Mythologies of China", by adding myth texts, images, audio, video recordings of oral myths, and mythology research books and articles, embedding motif codes into all these materials, and linking them via the WMCMDB to enable interactive multimedia retrieval.
3.  Enable users to build custom, personalized mythology research databases based on the WMCMDB motif index, for specialized research projects.
## 7.3. Personal Insights & Critique
### 7.3.1. Inspirations
This project is an excellent example of interdisciplinary digital humanities research, combining decades of rigorous humanities fieldwork and theoretical research with computer technology to preserve and advance research on intangible cultural heritage. The methodology of building a standardized, interoperable, expandable digital database for cultural heritage can be replicated for other folk literature, folklore, and intangible cultural heritage domains globally, not just for Chinese myths.
### 7.3.2. Potential Improvements
1.  **Multilingual Support**: The current platform is only available in Chinese, adding English language support would enable international researchers to use the database, facilitating greater global dialogue between Chinese and international mythology research.
2.  **Visualization Features**: Adding data visualization tools, such as maps showing the geographic distribution of specific motifs across China, or timeline charts showing the evolution of motifs over time, would make the database more accessible and support more intuitive comparative research.
3.  **Collaborative Annotation**: Adding a user annotation and verification function for registered researchers, to allow experts to contribute additional contextual information, translations, or new motifs, would make the database more dynamic and comprehensive.
4.  **API Access**: Providing an open application programming interface (API) would allow other digital humanities projects to integrate the WMCMDB data into their own systems, further expanding the impact of the database.