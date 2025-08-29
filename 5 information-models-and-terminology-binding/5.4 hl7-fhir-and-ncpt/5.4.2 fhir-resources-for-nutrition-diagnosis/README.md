# FHIR Resources for Nutrition Diagnosis

> Nutrition Diagnosis identifies specific nutrition problems that can be addressed through interventions.

## Nutrition Diagnosis Data and Associated FHIR Resources

The FHIR **Condition** resource is primarily used to represent nutrition diagnoses. It captures the nutrition diagnosis using structured data.

* **Problem** : Represented by the condition code, often using SNOMED CT codes.
* **Etiology** : Captured in the details or extensions of the Condition resource.
* **Signs/Symptoms** : Documented as evidence within the Condition resource, referencing relevant Observation resources.

| Types of data collected | Purpose                                                                                                                                                                                           | Example                                | FHIR Resource                                                        |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------- | -------------------------------------------------------------------- |
| **Diagnosis**           |                                                                                                                                                                                                   |                                        |                                                                      |
| _**Problem**_           | Represents the primary nutrition-related problem using a condition code                                                                                                                           | Malnutrition                           | **Condition**                                                        |
| _**Etiology**_          | Details the cause or contributing factors for the diagnosis                                                                                                                                       | Physical Function, Social-personal     | **Condition**                                                        |
| _**Signs/symptoms**_    | <p>Documents observable signs or symptoms that support the diagnosis<br><br></p><p><em>Documented as evidence within the Condition resource, referencing relevant Observation resources.</em></p> | Unintended weight loss, muscle wasting | <p><strong>Observation</strong></p><p><strong>Condition</strong></p> |

## Example: Nutrition Diagnosis with Etiology

**Clinical scenario**

> This scenario involves a 55-year-old patient with a history of Type 2 diabetes mellitus, managed with medications and lifestyle adjustments. Recent symptoms include unintended weight loss, weakness, and swelling in the lower limbs. Clinical evaluation reveals signs of weight loss and muscle wasting, indicating possible malnutrition exacerbated by chronic diabetes management.

Using FHIR resources, healthcare providers document these findings to support a structured approach to diagnosis and treatment planning.

* The **Condition Resource** represents the nutrition diagnosis (Malnutrition) using a SNOMED CT code.
  * The **evidence** section of the Condition resource includes:
    * **Etiology** : _**Physiologic–Metabolic;**_ Underlying chronic illness (Type 2 diabetes mellitus) as another **Condition** resource.
    * **Signs/Symptoms** : Unintended weight loss and Muscle wasting, which are represented as **Observation** resources linked to the condition. These observations document the presence of each symptom (Boolean value true).

### **Diagnosis (Problem): Malnutrition**

This resource represents the diagnosis of the nutritional disorder (malnutrition).

```json
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
```

### **Etiology (Cause)**&#x20;

This resource represents the underlying chronic condition contributing to the nutritional disorder.

#### **Underlying Chronic Illness, Diabetes Mellitus** :

#### Condition Resource for Underlying Chronic Illness

Here is a JSON representation of a condition resource detailing a chronic illness, Diabetes mellitus type 2:

```json
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
```

This resource uses standard coding systems to describe the clinical and verification statuses, as well as the specific type of diabetes being documented.

### **Signs/Symptoms** : **Unintentional Weight Loss**

This is referenced in the evidence section of the Condition resource, and referencing a condition or observation resource.

#### **Unintentional Weight Loss**

This resource documents the presence of unintentional weight loss.

#### Observation Resource: Symptom - Weight Loss

```json
{
  "resourceType": "Observation",
  "id": "unintentional-weight-loss",
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
```

**Details:**

* **Resource Type**: Observation
* **ID**: unintentional-weight-loss
* **Status**: Final
* **Category**: Clinical
* **Code**: 448765001 - Unintentional weight loss (finding)
* **Subject Reference**: Patient/example
* **Symptom Presence**: True

### **Signs/Symptoms: Muscle wasting**&#x20;

#### Observation Resource: Muscle Wasting

The following JSON represents an HL7 FHIR Observation for the symptom "Muscle Wasting":

```json
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
```

This resource indicates a clinical observation related to the presence of muscle atrophy (disorder) for a patient. The `valueBoolean` attribute confirms the observation is true.

**Linking the Resources**

* The **Condition Resource for Nutritional Disorder** references:
* The **Condition Resource for Type 2 Diabetes Mellitus** in its evidence.detail array to represent the etiology.
* The **Observation Resources** for unintentional weight loss and muscle atrophy to represent signs/symptoms.
* All resources reference the same patient (Patient/example) for proper linkage and context.






<a href="https://docs.google.com/forms/d/e/1FAIpQLScTmbZIf0UEQwYDkY27EEWBkaiYkHSbR0_9DmFrMLXoQLyL7Q/viewform?usp=pp_url&entry.1767247133=NCPT IG&entry.670899847=FHIR%20Resources%20for%20Nutrition%20Diagnosis" class="button primary">Provide Feedback</a>
