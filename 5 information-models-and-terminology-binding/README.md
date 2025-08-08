# Information Models and Terminology Binding

A well-defined information model and appropriate terminology bindings are essential to accurately document the NCP within healthcare systems using SNOMED CT. The information model provides a structured framework for organizing data related to nutrition assessment, diagnosis, intervention, and monitoring. Terminology bindings link this data to standardized SNOMED CT concepts, promoting consistent communication and interoperability across healthcare settings. This approach ensures clear and precise documentation, facilitates data sharing, and supports high-quality, patient-centered nutrition care.

To clarify how the NCP can be implemented in clinical information systems and supported by SNOMED CT, a Logical Model for the NCP is presented. This model serves as a technology-agnostic common reference information model, adaptable to specific implementation needs, and highlights points where terminology bindings to SNOMED CT can be effectively applied.

By establishing these models and bindings, healthcare organizations can achieve precise data recording and effective data use.

In recent years, the integration of HL7® FHIR® with SNOMED CT has gained popularity. Given its wide acceptance and capabilities, HL7 FHIR is the preferred information model in this implementation guide. The following sections provide recommended strategies for integrating SNOMED CT with HL7 FHIR to document the NCP within electronic health records (EHRs).

Other information modeling solutions, such as openEHR, may provide useful archetypes. However, they are not included in this version of the guide due to the lack of widely recognized international models in this area. As progress continues, future updates to the guide may include these frameworks.
