# Use Cases

Effective nutrition care relies on the ability to share, receive, reuse, and interpret structured nutrition data seamlessly across healthcare settings. Structured nutrition care data play a crucial role in supporting comprehensive care transitions, ensuring continuity and consistency in nutrition interventions as patients move through different levels of care.

The use cases provided on this page serve as examples of how SNOMED CT terms can be applied to document various aspects of nutrition care. These examples are illustrative rather than exhaustive, offering guidance on practical applications of SNOMED CT for capturing nutrition-related information within clinical workflows.

## Use Case 1: Interoperable nutrition care utilizing the Nutrition Care Process Model and standardized terminology

Standardizing the documentation of nutrition care using SNOMED CT allows for consistent recording of patient data across different EHR systems. Structured documentation facilitates interoperability between healthcare providers and enables seamless sharing of nutrition-related data during patient transitions between care settings (e.g. when a patient is discharged from a hospital to a long term care facility). Development of functional digital nutrition care templates in EHR systems, and subsequent seamless data acquisition and analysis are greatly facilitated by the SNOMED CT NCPT reference set and other available concept groupings such as value sets. [Value sets](https://app.gitbook.com/s/P21QucCX9Y41nBQt50ad/v/value-set) are lists of codes and corresponding terms, such as SNOMED CT that define clinical concepts to support effective and interoperable health information exchange. Value sets ensure consistency as the same key concepts are chosen every time for documentation. In the United States, the [Value Set Authority](https://vsac.nlm.nih.gov/) of the National Library of Medicine maintains value sets. The Academy stewards over 72 nutrition and dietetics related value sets that are available at the [Value Set Authority](https://vsac.nlm.nih.gov/) (log in required). An example of such a value set is the '[Nutrition Diagnosis Grouping](https://vsac.nlm.nih.gov/valueset/2.16.840.1.113762.1.4.1095.85/expansion)' value set in VSAC that contains mostly but not exclusively the SNOMED concepts describing NCPT nutrition diagnoses. In future iterations of this guide, broad examples utilizing value sets will be included among use cases. More on value sets is available in section [Terminology Bindings for Nutrition Diagnosis](<../5 information-models-and-terminology-binding/5.4 hl7-fhir-and-ncpt/5.4.2 fhir-resources-for-nutrition-diagnosis/5.4.2.1-terminology-bindings-for-nutrition-diagnosis.md>).

### Example 1.1 - Nutrition **Assessment**

> A patient with **newly diagnosed diabetes mellitus type 2** is referred to a dietitian for nutrition care. The patient has not seen a dietitian before.\
> During the initial assessment, the dietitian records the patient's dietary habits, anthropometric measurements, biochemical data (e.g. blood glucose concentration), and relevant medical and social history using standardized SNOMED CT concepts within the EHR. This structured documentation allows for seamless sharing of the patient's nutrition assessment data with other healthcare providers involved in their care, such as endocrinologists, primary care physicians, and nurses.

**Examples**

* 788472008 Carbohydrate intake (observable entity): > 500 grams per day exceeding recommended range of 250-300 grams per day
* 785891000 Nutrition knowledge of individual client (observable entity): poor
* 819960006 Healthy Eating Index 2015 score (observable entity): 49 (out of 100, which is categorized in the lowest quality)\*: poor
* 405152002 Quality of life satisfaction (observable entity): poor as measured by
* 273725009 Quality of life scale (assessment scale): Health Related Quality of Life (HRQOL)\*\*

\*Healthy Eating Index (HEI) 2015 scale is: from 1 point (lowest) to 100 points (highest diet quality), five categories:

* scores of 90 to 100=excellent
* scores of 80 to 89=very good
* 70 to 79=good
* 60 to 69=fair, and
* 0 to 59=poor

\*\*Health Related Quality of Life (HRQOL) scale is: excellent, very good, good, fair, or poor

{% hint style="info" %}
Best practice tip: There is discussion in many countries like Sweden about minimizing double documentation. In the EHR, any professional can read information other professionals have documented. Thus, it should not be necessary for dietitians to re-document values like blood glucose concentration. The dietitians could refer to the related section in the EHR.
{% endhint %}

#### Benefits for Clinicians:

* **Streamlined Workflow:** Clinicians can efficiently capture and access comprehensive nutrition assessment data within the EHR, reducing documentation time and minimizing redundancies.
* **Enhanced Communication :** Standardized documentation facilitates seamless communication and information sharing among interdisciplinary healthcare teams, improving care coordination and patient outcomes, and helping to provide safe care; also SNOMED CT can facilitate communication within a collaborative team where the client is included.
* **Improved Continuity of Care:** Clinicians can easily retrieve and review recorded nutrition care data from previous encounters, ensuring continuity of care and informed decision-making across care settings.

#### Benefits for Patients:

* **Enhanced Communication:** Standardized documentation facilitates seamless communication and information sharing among interdisciplinary healthcare teams, improving care coordination and patient outcomes, and helping to provide safe care. Standardized terminology promotes health literacy and equity of the client.
* **Improved Continuity of Care:** Clients can retrieve and review recorded nutrition data from provider encounters, ensuring continuity of care and participation in informed goal setting and decision-making across care settings.

### Example 1.2 - Evidence-Based Nutrition **Diagnosis**

> By leveraging SNOMED CT concepts for nutrition diagnosis within the **SNOMED CT NCPT reference set (current release April 2026)** , healthcare professionals can accurately identify and categorize patients' nutrition problems. This standardized approach enhances the ability to apply evidence-based interventions and track outcomes effectively.

**Example of a complete diagnostic statement in PES format (P: problem, E: etiology, S: signs and symptoms)**

* **Problem**: 870404000 Excessive intake of carbohydrate (finding), related to
* **Etiology**: 424890008 Unbalanced diet (finding), as evidenced by
* **Signs and Symptoms**:
  * 788472008 Carbohydrate intake (observable entity): > 500 grams per day exceeding recommended range of 250-300 grams per day and
  * 785891000 Nutrition knowledge of individual client (observable entity): poor
  * 819960006 Healthy Eating Index 2015 score (observable entity): 49 (out of 100): poor
  * 405152002 Quality of life satisfaction (observable entity): poor as reported by patient's Health Related Quality of Life (HRQOL)

By applying standardized terminology, the healthcare team can accurately identify the patient's nutrition-related problems and prioritize interventions to address the patient's specific needs.

#### Benefits for Clinicians:

* **Accurate Problem Identification:** Standardized terminology enables clinicians to accurately identify and document nutrition-related problems, enhancing diagnostic precision and supporting evidence-based decision-making.
* **Consistency in Documentation:** Clinicians can consistently document nutrition diagnoses using SNOMED CT concepts, ensuring clarity and coherence in health records and facilitating effective communication with other members of the healthcare team.
* **Facilitated Care Planning:** Clear and standardized nutrition diagnoses guide clinicians in developing tailored care plans and interventions that address patients' specific nutritional needs and goals.

#### Benefits for Patients:

* **Facilitated Care Planning** : Clear and standardized nutrition diagnoses guide clinicians and patients in developing individualized, tailored care plans and interventions that address patients' specific nutritional needs and goals.

### Example 1.3 - Tailored Nutrition **Intervention**

> Utilizing SNOMED CT for documenting nutrition interventions enables healthcare providers to select and implement appropriate dietary recommendations and therapies based on standardized terminology. This supports personalized care planning and ensures consistency in treatment strategies across different care settings.
>
> The dietitian provides an intervention that supports carbohydrate control and portion sizes. The use of SNOMED CT ensures consistency in documenting dietary recommendations and facilitates communication between the dietitian, nurse, endocrinologist, and other members of the healthcare team involved in the patient's care.

**Examples**

* 445301000124102 Content-related nutrition education (procedure), on
* 787764007 Estimated quantity of intake of carbohydrate in 24 hours (observable entity)

#### Benefits for Clinicians:

* **Personalized Care Planning:** Standardized documentation of nutrition interventions supports clinicians in developing personalized care plans that align with patients' nutrition diagnoses, preferences, and cultural backgrounds.
* **Consistency in Treatment:** Clinicians can consistently implement evidence-based nutrition interventions using SNOMED CT-coded concepts, promoting standardization and quality of care across diverse patient populations and care settings.
* **Enhanced Patient Engagement:** Clear and standardized documentation facilitates effective communication between clinicians and patients, empowering patients to actively participate in their nutrition management and adhere to recommended dietary changes.

#### Benefits for Patients:

* **Personalized Care Planning:** Standardized documentation of nutrition interventions supports clinicians in developing personalized care plans that align with patients' nutrition diagnoses, preferences, and cultural backgrounds.
* **Enhanced Patient Engagement:** Clear and standardized documentation facilitates effective communication between clinicians and patients, empowering patients to actively participate in their nutrition management and adhere to recommended dietary changes.

### Example 1.4 - Continuous Nutrition **Monitoring and Evaluation**

> Standardized documentation of nutrition monitoring and evaluation data using SNOMED CT facilitates ongoing assessment of patients' nutritional status and progress over time. This enables nutrition and dietetics professionals to identify trends, adjust interventions as needed, and evaluate the effectiveness of nutrition care plans in achieving desired outcomes.

**Examples**

* 788472008 Carbohydrate intake (observable entity): **>500 grams per day** exceeding recommended range of 250-300 grams per day
* 785891000 Nutrition knowledge of individual client (observable entity): **poor**
* 819960006 Healthy Eating Index 2015 score (observable entity): **49 (out of 100): poor**
* 405152002 Quality of life satisfaction (observable entity): **poor** as reported by patient's Health Related Quality of Life (HRQOL)

#### Benefits for Clinicians:

* **Timely Assessment:** Standardized documentation enables clinicians to systematically monitor and evaluate patients' nutritional status and response to interventions over time, facilitating early detection of changes and timely adjustments to care plans.
* **Data-Driven Decision-making:** Clinicians can leverage aggregated nutrition monitoring data to identify trends, assess treatment efficacy, and make evidence-based decisions to optimize patient outcomes.
* **Quality Improvement:** Ongoing documentation and evaluation of nutrition care outcomes support quality improvement initiatives by identifying areas for practice refinement and implementing targeted interventions to enhance patient care and safety.

#### Benefits for Patients:

* **Quality Improvement:** Ongoing documentation and evaluation of nutrition care outcomes support quality improvement initiatives by identifying areas for practice refinement and implementing targeted interventions to enhance patient care and safety.
* **Improved health outcomes**

## Use Case 2: Transitions of care include continuity of nutrition care across settings. How does the information follow the patient

Transitional care models are practice systems that “follow patients across settings (e.g., from hospital to home), improve coordination among health care providers, and help individuals better understand their post-hospital care. When implementing SNOMED CT for nutrition care documentation, concurrent effective use of data standards (such as HL7 FHIR) allows for data to follow the patient effectively. Standardized documentation of nutrition care using SNOMED CT is a critical pre-step to the use of data standards such as FHIR as the structured data is more readily exchanged.

### Example 2.1 - Exchanging Nutrition Data

> A standardized digital referral using SNOMED CT codes and a FHIR API is able to transfer nutrition related data of patients with malnutrition between dietitians (from hospital to a community-based meal provision organization) and this communication of care improves health outcomes post discharge.

#### Benefits for Clinicians:

* **Real Time Data Transfer** : Ensures timely continuity of care and reduces clinician and patient burden (no more repeating of information).
* **Reduced Opportunity for Human Error in Clinical Documentation** : Automated data transfer allows for accurate data transmission from hospital to other venues of care.

#### Benefits for Patients:

* **Improved Access to Care** : Interoperable EHR systems facilitate referral completion (closing the loop in transitions of care effectively). After their hospital discharge, patients can be referred to dietitians and/or other healthcare professionals serving in outpatient settings.
* **Enhanced Security and Privacy** : While FHIR is not a security protocol in itself, using data standards to exchange documentation requires advanced security measures that better protect patient privacy.

## Use Case 3: Facilitating Clinical Decision Support and Research

By implementing SNOMED CT for nutrition care documentation, EHR systems can support clinical decision support tools that utilize standardized data to provide tailored recommendations for nutrition management. Furthermore, the consistent use of SNOMED CT enables aggregation of data for research purposes, allowing for the analysis of nutrition care practices, outcomes, and their impact on patient health.

### Example 3.1 - EHR-Integrated Tool for Personalized Care and Research Insights

> A healthcare system implements a clinical decision support tool embedded within its EHR system to assist providers in managing patients with chronic kidney disease. The tool utilizes SNOMED CT-coded nutrition data to generate tailored recommendations for dietary modifications, fluid restriction, and electrolyte management based on the patient's stage of disease and comorbid conditions. Additionally, aggregated SNOMED CT-coded nutrition care data from EHRs across the healthcare system are utilized for research purposes to analyze trends in nutrition-related outcomes among patients with chronic kidney disease and evaluate the impact of various interventions on disease progression and quality of life.

#### Benefits for Clinicians:

* **Enhanced Decision Support:** Clinicians benefit from clinical decision support tools embedded within the EHR that utilize standardized SNOMED CT-coded nutrition care data to provide real-time, evidence-based recommendations for patient care, enhancing clinical decision-making and patient safety.
* **Informed Research:** Aggregated SNOMED CT-coded nutrition data facilitate research initiatives by providing valuable insights into nutrition care practices, outcomes, and trends across diverse patient populations, supporting evidence-based practice and continuous quality improvement efforts.
* **Knowledge Translation:** Research findings derived from SNOMED CT-coded nutrition care data can be translated into clinical practice guidelines and protocols, equipping clinicians with up-to-date evidence to guide their decision-making and improve patient care.

#### Benefits for Patients:

* **Generation of New Evidence:** Aggregated SNOMED CT-coded nutrition care data facilitate the updating of evidence-based nutrition practice guidelines and can be used in quality improvement work, advocacy and policy design efforts for improving nutrition care services and related staffing capacity.

**Users who would like to submit new use cases they have developed may do so at any time, and will be considered for inclusion. Please submit content, comments, and questions at:** [**info@snomed.org**](mailto:info@snomed.org)

***

**REFERENCES**

Chui TK, Proaño GV, Raynor HA, Papoutsakis C. A Nutrition Care Process Audit of the National Quality Improvement Dataset: Supporting the Improvement of Data Quality Using the ANDHII Platform. J Acad Nutr Diet. Jul 2020;120(7):1238-1248.e1. doi:10.1016/j.jand.2019.08.174

Colin C, Arikawa A, Lewis S, et al. Documentation of the evidence-diagnosis link predicts nutrition diagnosis resolution in the Academy of Nutrition and Dietetics' diabetes mellitus registry study: A secondary analysis of Nutrition Care Process outcomes. Front Nutr. 2023;10:1011958. doi:10.3389/fnut.2023.1011958

Kight CE, Bouche JM, Curry A, et al. Consensus Recommendations for Optimizing Electronic Health Records for Nutrition Care. Nutr Clin Pract. Feb 2020;35(1):12-23. doi:10.1002/ncp.10433

Krebs-Smith SM, Pannucci TE, Subar AF, et al. Update of the Healthy Eating Index: HEI-2015. J Acad Nutr Diet. Sep 2018;118(9):1591-1602. doi:10.1016/j.jand.2018.05.021

Lewis SL, Miranda LS, Kurtz J, Larison LM, Brewer WJ, Papoutsakis C. Nutrition Care Process Quality Evaluation and Standardization Tool: The Next Frontier in Quality Evaluation of Documentation. J Acad Nutr Diet. Mar 2022;122(3):650-660. doi:10.1016/j.jand.2021.07.004

Lewis SL, Wright L, Arikawa AY, Papoutsakis C. Etiology Intervention Link Predicts Resolution of Nutrition Diagnosis: A Nutrition Care Process Outcomes Study from a Veterans' Health Care Facility. J Acad Nutr Diet. Sep 2021;121(9):1831-1840. doi:10.1016/j.jand.2020.04.015

Lloyd L, Swan WI, Jent S, Vivanti A, Pertel DG. Worldwide Release of SNOMED CT Nutrition Care Process Terminology Problem List. J Acad Nutr Diet. 2024 Apr;124(4):531-534.

Long JM, Yoder A, Woodcock L, Papoutsakis C. Impact of a Registered Dietitian Nutritionist-Led Food as Medicine Program in the Food Retail Setting: A Feasibility Study. (2212-2672 (Print))

Maduri C, Sabrina Hsueh PY, Li Z, Chen CH, Papoutsakis C. Applying Contemporary Machine Learning Approaches to Nutrition Care Real-World Evidence: Findings From the National Quality Improvement Data Set. J Acad Nutr Diet. Dec 2021;121(12):2549-2559.e1. doi:10.1016/j.jand.2021.02.003

Moriarty DG, Zack MM, Kobau R. The Centers for Disease Control and Prevention’s Healthy Days Measures - Population tracking of perceived physical and mental health over time. Health Qual Life Outcomes. 2003;1:37. [https://doi.org/10.1186/1477-7525-1-37](https://doi.org/10.1186/1477-7525-1-37)

Proaño GV, Papoutsakis C, Lamers-Johnson E, et al. Evaluating the Implementation of Evidence-based Kidney Nutrition Practice Guidelines: The AUGmeNt Study Protocol. J Ren Nutr. Sep 2022;32(5):613-625. doi:10.1053/j.jrn.2021.09.006

Vergili JM, Proaño GV, Jimenez EY, Moloney L, Papoutsakis C, Steiber A. Academy of Nutrition and Dietetics Commentary on the Phosphorus Recommendation in the KDOQI Clinical Practice Guidelines for Nutrition in CKD: 2020 Update. J Ren Nutr. May 2024;34(3):192-199. doi:10.1053/j.jrn.2023.11.001

<a href="https://docs.google.com/forms/d/e/1FAIpQLScTmbZIf0UEQwYDkY27EEWBkaiYkHSbR0_9DmFrMLXoQLyL7Q/viewform?usp=pp_url&#x26;entry.1767247133=NCPT+IG&#x26;entry.670899847=3.%20clinical-use-cases" class="button primary">Provide Feedback</a>
