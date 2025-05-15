# 1. Introduction

# Background

Most nutrition and dietetics professionals work in settings where they treat people (either clients or patients or groups) through medical nutrition therapy (MNT) to manage or prevent nutrition-related disease. 

The Nutrition Care Process (NCP) is a concise framework model for professionals who provide nutrition and dietetics care. The NCP embraces people-centered care and has been evolving since 2003 to become the international standard for nutrition and dietetics care delivery. The NCP encourages the use of standardized terminology. Standardized terminology is necessary for data to follow the patient across settings when different electronic health records (EHR) systems are involved (e.g. all data from an acute care unit is transmitted as documented to a community care setting). 

The documentation and exchange of coded nutrition and dietetics care data vary across EHRs due to a lack of standardized terminology and inconsistent implementation practices, making interoperability and continuity of care challenging.

The lack of interoperability limits the aggregation of nutrition and dietetics care data for informed clinical decision support. It also hinders the ability to research the effectiveness of nutrition care and resulting health outcomes. The documentation of nutrition and dietetics care data must be clearly defined in EHRs to support patient health, safety and a comprehensive health record.

Entry points to the NCP (i.e. initiation of nutrition and dietetics care by a nutrition and dietetics professional) are typically screening and/or referral systems. The NCP framework (or NCP) for nutrition care was designed and approved by the Academy of Nutrition and Dietetics in 2003. Since then, the Academy of Nutrition and Dietetics has collaborated with many international dietetic associations to revise, evolve and adopt the NCP in its current form. Also, alternate iterations of the NCP have since been used and exist. From an international perspective, this demonstrates and solidifies the usability and adaptability of the NCP going into the future. 

In the NCP, there are four steps:

  * Nutrition Assessment and Reassessment
  * Nutrition Diagnosis
  * Nutrition Intervention
  * Nutrition Monitoring and Evaluation

Nutrition and dietetics professionals frequently use the Nutrition Care Process Terminology (NCPT) to communicate the Nutrition Care Process. The NCPT is a standardized terminology that complements the NCP, communicates the functions of nutrition and dietetics professionals, and facilitates research on the outcomes of nutrition and dietetics care.

In its majority, the NCPT (edition 2020) has been integrated into SNOMED CT as a result of many international nutrition and dietetics organizations working collaboratively with the Academy of Nutrition and Dietetics and SNOMED International. The first iteration of SNOMED CT's NCPT reference set (also called refset*) (released in April 2024) contained the concepts that document Nutrition Diagnosis in the NCP (166 concepts), ([related press release](https://www.snomed.org/news/snomed-international-releases-the-first-nutrition-care-process-terminology-reference-set)). The current SNOMED CT NCPT Reference Set (released in April 2025) contains updated nutrition problems and the addition of nutrition intervention terms mapped to SNOMED CT, ([Release notes](https://confluence.ihtsdotools.org/x/agV9Dw)) Nutrition assessment and monitoring and evaluation terms will also be added (April 2026, as time and resources permit). The third update will complete the currently planned content to the reference set.

In a healthcare environment that evolves rapidly, the vision for the NCP and NCPT is to make possible communication within and across healthcare systems for quality care and outcomes research. Implementation strategies should include the development of resources like the present implementation guide, education and training, leadership support, and change-management approaches. 

Standards Development Organizations (SDOs), like HL7, in collaboration with the Academy of Nutrition and Dietetics have developed standards and provided guidance to assist implementers, however specific guidance in using and implementing SNOMED CT in the context of nutrition care is limited. The present implementation guide fills this gap.

  

# Objective

The objective of the SNOMED CT implementation guide for Nutrition Care Process Terminology (NCPT) is to support standardized practices and terminology for documenting nutrition and dietetics care data within Electronic Health Records (EHRs), specifically describing the four steps of the Nutrition Care Process (NCP) Model: 

  * Nutrition Assessment and Reassessment
  * Nutrition Diagnosis
  * Nutrition Intervention
  * Nutrition Monitoring and Evaluation

This guide aims to improve consistency, and quality of nutrition care data documentation and exchange across electronic systems (interoperability), facilitating informed clinical decision support, research on the efficacy of nutrition care, and enhancing patient health, safety, and comprehensive health record management.

The guide operationalizes the utilization of the SNOMED CT NCPT (Nutrition Care Process Terminology) reference set to enhance the quality of documentation and care in this vital domain.

SNOMED International aims to create a demonstration tool to showcase the principles and techniques elucidated in the guide.

# Scope

The scope of the work presented in this guide includes:

  1. Review standards on nutrition and dietetics care 
  2. Analyze relevant information models
     1. Review existing information models that are in scope, with emphasis on HL7® FHIR® resources that have gained wide adoption in recent years
  3. Provide typical use cases
     1. Describe common and important scenarios for capturing or exchanging nutrition care data
     2. Illustrate how the information can be represented by using FHIR® and SNOMED CT concepts
  4. Explain how nutrition related concepts are represented in SNOMED CT
  5. Support use of the SNOMED CT NCPT refset* and explain how it facilitates implementation of SNOMED CT   

     1. Identify **SNOMED CT****NCPT refset*** concepts used to define nutrition and dietetics care 
     2. Identify existing **value sets**** for specific applications and standards e.g., malnutrition assessment
  6. Provide practical guidance on the use of SNOMED CT in nutrition care as it pertains to the implementation of the following:
     1. Problem list (this edition)
     2. Intervention list (this edition) 
     3. Assessment, Monitoring and Evaluation list (future edition)
     4. Clinical decision support (future edition)

*The word "refset" is a combination of the two words "reference set". Reference sets are essentially published subsets of the full SNOMED CT. The International Release of SNOMED CT contains over 350,000 concepts. It is understandable that not all users need to use all of these. A practical way to identify easily and use concepts by practice area is by establishing refsets that can be used by related healthcare professionals. This reference set mechanism provides a standardized approach to refer to a subset of SNOMED CT. Here, the NCPT SNOMED refset can be very useful to nutrition and dietetics professionals who provide nutrition care. For more on refsets see: [Reference set tools](https://www.implementation.snomed.org/reference-set-tools)

**The words "value set" mean a group of valid concepts or expressions intended to constrain the permissible content for a particular use (e.g. a value set for malnutrition will be a defined list of concepts used to document the different types of malnutrition). For more information see: [value sets](https://vsac.nlm.nih.gov/) from the US.

  

# Audience

SNOMED CT is a comprehensive, multilingual clinical terminology that can be used to standardize and improve the quality of data related to nutrition and dietetics care. This guide is targeted at the various stakeholders involved with the implementation of SNOMED CT:

  * **[SNOMED International Members](https://www.snomed.org/members)** who are seeking uniform, clear best practices for documenting nutrition and dietetics care, and understanding how SNOMED CT can be applied in this domain.

  * **Clinicians** **and other healthcare professionals** (such as hospital administrators and managers) who are interested in understanding how SNOMED CT can support the clinical needs for data collection and acquisition within the field of nutrition and dietetics care; and how SNOMED CT can facilitate communication within a collaborative team where the client is included.

  * **Quality measure developers** and those implementing quality initiatives who are reporting nutrition care data and/or examining the impact of nutrition on care outcomes.
  * **Information managers** who are looking to learn how SNOMED CT can be integrated into health information models within the domain of nutrition and dietetics care to support the implementation of SNOMED CT and enhance data interoperability.

  * **Software developers** who want to learn how to integrate SNOMED CT into software applications used in the domain of nutrition and dietetics care.

# Attribution

This SNOMED CT Implementation guide and the underlying work have been developed by the **[Nutrition and Dietetics Clinical Reference Group](https://confluence.ihtsdotools.org/display/NDCRG/Meetings+-+Nutrition+and+Dietetics+CRG)**. The Clinical Reference Group (CRG) is composed of experts in the field of **nutrition and dietetics** providing input from the community of practice on the development, maintenance, and use of SNOMED CT in this specific domain. The CRG members have been instrumental in the development of this guide, providing their expertise, knowledge, and experience to ensure that it is accurate, up-to-date, and relevant to the needs of its intended audience. Their dedication and hard work have made this guide possible and SNOMED International is grateful for their contributions. This guide is a product of SNOMED International's ongoing commitment to improving healthcare through the use of high-quality, standardized clinical terminologies. 

  

**Main Contributors**

Acknowledgement to the Academy of Nutrition and Dietetics (<https://www.eatright.org/>)

**Individuals:**

  * Dr. Constantina Papoutsakis, Chair, Nutrition and Dietetics Clinical Reference Group, Academy of Nutrition and Dietetics
  * William Swan, Past Chair, Nutrition Care Process Research Outcomes Committee, Academy of Nutrition and Dietetics, USA
  * Dr. Angela Vivanti, Past Chair, Nutrition Care Process Research Outcomes Committee, Academy of Nutrition and Dietetics, Princess Alexandra Hospital, Australia
  * Dr. Ylva Orrevall, The Swedish Association of Registered Dietitians' working group for Informatics and Ethical code, and Women’s Health and Allied Health Professionals Theme, Karolinska University Hospital, Stockholm, Sweden
  * Lindsay Woodcock, Academy of Nutrition and Dietetics
  * Donna Pertel, SNOMED Author, former Academy of Nutrition and Dietetics
  * Elaine Wooler _, SNOMED International_
  * Ian Green _, SNOMED International_
  * Anne Randorff Højen _, SNOMED International_
  * Alejandro Lopez Osornio _, SNOMED International_

  

# Guide Overview

This SNOMED CT Implementation Guide is designed to provide guidance for the use of SNOMED CT within the domain of nutrition and dietetics care. The guide is organized into the following main chapters:

  * Chapter 1:**Introduction** \- This chapter provides a background on the guide, including the objectives, scope, and target audience.
  * Chapter 2: **What is NCP and NCPT?** \- This chapter provides basic information on the Nutrition Care Process (NCP) Model (NCPM-the graphic depiction of the NCP) and NCP Terminology (NCPT).
  * Chapter 3: **Clinical Use Cases** \- This chapter describes the key use cases that have motivated the creation of this guide and explains scenarios where implementation of SNOMED CT within this domain is needed.
  * Chapter 4:**Content in SNOMED CT** \- This chapter describes how SNOMED CT addresses the terminological needs within the domain of **nutrition and dietetics**. It also elaborates on the major types of related concepts and relative templates that exist in SNOMED CT.
  * Chapter 5: **Information Model and Terminology Binding** \- This chapter introduces a generic logical model for nutrition care records, and general terminology bindings, so that healthcare organizations can ensure data are recorded with precision and utilized effectively. 
  * Chapter 6: **Technical Application** \- This chapter presents technical considerations related to the SNOMED implementation of NCPT including accessing, deploying, and using the SNOMED CT NCPT reference set.

In addition, a number of appendices present additional information and insights into the terms used in this document, and references to relevant resources.

  

# Review

This SNOMED CT Implementation guide represents the culmination of work started by the Implementation SIG (SIG means Special Interest Group) in 2014 and continued by the **[Nutrition and Dietetics Clinical Reference Group](https://confluence.ihtsdotools.org/display/NDCRG/Meetings+-+Nutrition+and+Dietetics+CRG)** starting in 2023. 

We welcome feedback from readers on the guide and encourage them to share their insights and experiences with us. Your comments and suggestions will help us improve the content of the guide and ensure that it is relevant and useful to those who use it. We will review any feedback received and make updates to the guide as needed. 

We appreciate your interest in this guide and thank you for your contributions to the improvement of healthcare through the use of high-quality, standardized clinical terminologies like SNOMED CT. Please raise any comments to this document via the feedback button (At the bottom of the page).

  

**REFERENCES**

Lloyd L, Swan WI, Jent S, Vivanti A, Pertel DG. Worldwide Release of SNOMED CT Nutrition Care Process Terminology Problem List. J Acad Nutr Diet. 2024 Apr;124(4):531-534.

Swan WI, Vivanti A, Hakel-Smith NA, Hotson B, Orrevall Y, Trostler N, Beck Howarter K, Papoutsakis C. Nutrition Care Process and Model Update: Toward Realizing People-Centered Care and Outcomes Management. J Acad Nutr Diet. 2017 Dec;117:2003-14.

Swan WI, Pertel DG, Hotson B, Lloyd L, Orrevall Y, Trostler N, Vivanti A, Howarter KB, Papoutsakis C. Nutrition Care Process (NCP) Update Part 2: Developing and Using the NCP Terminology to Demonstrate Efficacy of Nutrition Care and Related Outcomes. J Acad Nutr Diet. 2019 May;119:840-55.

  

  

