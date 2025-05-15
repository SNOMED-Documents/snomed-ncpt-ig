# 5.4.2 FHIR Resources for Nutrition Diagnosis

Nutrition Diagnosis identifies specific nutrition problems that can be addressed through interventions.

## Nutrition Diagnosis Data and Associated FHIR Resources

The FHIR **Condition** resource is primarily used to represent nutrition diagnoses. It captures the nutrition diagnosis using structured data.

  * **Problem** : Represented by the condition code, often using SNOMED CT codes.
  * **Etiology** : Captured in the details or extensions of the Condition resource.
  * **Signs/Symptoms** : Documented as evidence within the Condition resource, referencing relevant Observation resources.

Types of data collected | Purpose| Example| FHIR Resource  
---|---|---|---  
Diagnosis  
  
  * Problem

| Represents the primary nutrition-related problem using a condition code| Malnutrition| **Condition**  
  
  * Etiology

| Details the cause or contributing factors for the diagnosis| Physical Function, Social-personal| **Condition**  
  
  * Signs/symptoms

| Documents observable signs or symptoms that support the diagnosis  
  
 _Documented as evidence within the Condition resource, referencing relevant Observation resources._|  Unintended weight loss, muscle wasting| **Observation****Condition**  
  
## Example: Nutrition Diagnosis with Etiology

**Clinical scenario**

This scenario involves a 55-year-old patient with a history of Type 2 diabetes mellitus, managed with medications and lifestyle adjustments. Recent symptoms include unintended weight loss, weakness, and swelling in the lower limbs. Clinical evaluation reveals signs of weight loss and muscle wasting, indicating possible malnutrition exacerbated by chronic diabetes management.

  

Using FHIR resources, healthcare providers document these findings to support a structured approach to diagnosis and treatment planning.

  * The **Condition Resource** represents the nutrition diagnosis (Malnutrition) using a SNOMED CT code.
    * The **evidence** section of the Condition resource includes:
      * **Etiology** : _**Physiologic–Metabolic;**_ Underlying chronic illness (Type 2 diabetes mellitus) as another **Condition** resource.
      * **Signs/Symptoms** : Unintended weight loss and Muscle wasting, which are represented as **Observation** resources linked to the condition. These observations document the presence of each symptom (Boolean value true).

### **Diagnosis (Problem): Malnutrition**

This resource represents the diagnosis of the nutritional disorder (malnutrition).

**Condition Resource Representing a Nutrition Diagnosis**
[code] 
    {
      "resourceType": "Condition",
      "id": "nutritional-disorder",
      "clinicalStatus": {
        "coding": [
          {
            "system": "http://terminology.hl7.org/CodeSystem/condition-clinical",
            "code": "active",
            "display": "Active"
          }
        ]
      },
      "verificationStatus": {
        "coding": [
          {
            "system": "http://terminology.hl7.org/CodeSystem/condition-ver-status",
            "code": "confirmed",
            "display": "Confirmed"
          }
        ]
      },
      "code": {
        "coding": [
          {
            "system": "http://snomed.info/sct",
            "code": "2492009",
            "display": "Nutritional disorder (disorder)"
          }
        ]
      },
      "subject": {
        "reference": "Patient/example"
      },
      "evidence": [
        {
          "detail": [
            {
              "reference": "Condition/diabetes"
            },
            {
              "reference": "Observation/weight-loss"
            },
            {
              "reference": "Observation/muscle-atrophy"
            }
          ]
        }
      ]
    }
[/code]

### **Etiology (Cause)** :

This resource represents the underlying chronic condition contributing to the nutritional disorder.

#### **Underlying Chronic Illness, Diabetes Mellitus** :   
  

**Condition Resource for Underlying Chronic Illness**
[code] 
    {
      "resourceType": "Condition",
      "id": "diabetes",
      "clinicalStatus": {
        "coding": [
          {
            "system": "http://terminology.hl7.org/CodeSystem/condition-clinical",
            "code": "active",
            "display": "Active"
          }
        ]
      },
      "verificationStatus": {
        "coding": [
          {
            "system": "http://terminology.hl7.org/CodeSystem/condition-ver-status",
            "code": "confirmed",
            "display": "Confirmed"
          }
        ]
      },
      "code": {
        "coding": [
          {
            "system": "http://snomed.info/sct",
            "code": "44054006",
            "display": "Diabetes mellitus type 2 (disorder)"
          }
        ]
      },
      "subject": {
        "reference": "Patient/example"
      }
    }
[/code]

### **Signs/Symptoms** :

This is referenced in the evidence section of the Condition resource, and referencing a condition or observation resource.

#### **Unintentional Weight Loss**

This resource documents the presence of unintentional weight loss.

**Observation Resource for associated Symptom: Edema**
[code] 
    {
      "resourceType": "Observation",
      "id": "weight-loss",
      "status": "final",
      "category": [
        {
          "coding": [
            {
              "system": "http://terminology.hl7.org/CodeSystem/observation-category",
              "code": "clinical",
              "display": "Clinical"
            }
          ]
        }
      ],
      "code": {
        "coding": [
          {
            "system": "http://snomed.info/sct",
            "code": "448765001",
            "display": "Unintentional weight loss (finding)"
          }
        ]
      },
      "subject": {
        "reference": "Patient/example"
      },
      "valueBoolean": true
    }
[/code]

####  **Muscle wasting** :

**Observation Resource for associated Symptom: Muscle wasting**
[code] 
    {
      "resourceType": "Observation",
      "id": "muscle-atrophy",
      "status": "final",
      "category": [
        {
          "coding": [
            {
              "system": "http://terminology.hl7.org/CodeSystem/observation-category",
              "code": "clinical",
              "display": "Clinical"
            }
          ]
        }
      ],
      "code": {
        "coding": [
          {
            "system": "http://snomed.info/sct",
            "code": "88092000",
            "display": "Muscle atrophy (disorder)"
          }
        ]
      },
      "subject": {
        "reference": "Patient/example"
      },
      "valueBoolean": true
    }
[/code]

**Linking the Resources**

  * The **Condition Resource for Nutritional Disorder** references:
  * The **Condition Resource for Type 2 Diabetes Mellitus** in its evidence.detail array to represent the etiology.
  * The **Observation Resources** for unintentional weight loss and muscle atrophy to represent signs/symptoms.
  * All resources reference the same patient (Patient/example) for proper linkage and context.

