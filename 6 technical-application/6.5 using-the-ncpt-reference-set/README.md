# 6.5 using-the-ncpt-reference-set

## 6.5 Using the NCPT Reference Set

## Introduction

When working with the Nutrition Care Process Terminology (NCPT) reference set, it’s essential to have efficient access to the content through various systems, regardless of the technology used.

Clinical applications will access the Reference Set content from the selected terminology repository. The main functional requirements include listing all concepts in the Reference Set, filtering by text search strings, and validating whether a concept is a member of the Reference Set.

This page provides examples of how to interact with the reference set, whether you’re using a FHIR terminology server or a relational database like MySQL.

## Accessing the Reference Set from a FHIR Terminology Server

When working with the Nutrition Care Process Terminology (NCPT) reference set, leveraging a FHIR terminology server can simplify access and management.

A FHIR terminology server provides mechanisms to work with the Reference Set as a Value Set; the main operations available are **$expand** and **$validate-code** :

#### FHIR Operations

| **Service Name and Status**                             | **Input** | **Output** |
| ------------------------------------------------------- | --------- | ---------- |
| \*\*$expand\*\*\*\*Get all members of the reference set |           |            |

***

\*\*|

* A reference set specified by its refsetId, in this case the identifier for the [1303957004 |Nutrition Care Process Terminology reference set (foundation metadata concept)|](http://snomed.info/id/1303957004)

|

* A list of concept or description IDs
* Option to include additional information about each concept or description

\*\*$validate-code**Test if a concept or description is a member of a specified reference set**\
\*\*|

* A reference set specified by its refsetId
* A candidate [concept.id](http://concept.id)

|

* If the candidate concept is a member of the reference set: TRUE
* Otherwise: FALSE

#### Example FHIR Requests

These examples use the concept [1303957004 |Nutrition Care Process Terminology reference set (foundation metadata concept)|](http://snomed.info/id/1303957004) as the refsetId.

| **Service Name**                         | \*\*API Call \*\* | **Result** |
| ---------------------------------------- | ----------------- | ---------- |
| **Get all members of the reference set** |                   |            |
| \[code]                                  |                   |            |

```
GET [fhir]/ValueSet/$expand
?url=http://snomed.info/sct?fhir_vs=refset/[refsetId]
&count=10
```

\[/code]

for example\
\[code]\
GET \[fhir]/ValueSet/$expand\
?url=http%3A%2F%2Fsnomed.info%2Fsct%3Ffhir\_vs%3Drefset%2F1303957004\&count=10\
\[/code]\
\[code]

\[/code]

An alternative solution is to use the expression constraint language, as shown here:\
\[code]\
GET \[fhir]/ValueSet/$expand\
?url=http%3A%2F%2Fsnomed.info%2Fsct%3Ffhir\_vs%3Decl%2F%5E%5B1303957004%5D\
\&count=10\
\[/code]\
\[code]\
GET \[fhir]/ValueSet/$expand\
?url=http%3A%2F%2Fsnomed.info%2Fsct%3Ffhir\_vs%3Decl%2F%5E1303957004\
\&count=10\
\[/code]

\| Returns a JSON representation of data about each of the reference set member.The data returned for each concept includes:

* \*\*code: \*\*the conceptId of the reference set member
* **display:** the preferred term for the reference set member

Also returns the **total** number of reference set membersAs some reference sets have very large numbers of children, this service is paged. Requests parameters include:

* **count** to restrict the number of members returned.
* \*\*offset \*\*to specify the start in the results (in multiples of the limit).

**Test if a concept is a member of the reference set**|\
\[code]\
GET \[fhir]/ValueSet/$validate-code\
?system=http://snomed.info/sct\&code=181216001\
\&url=http://snomed.info/sct/\[moduleId]/version/\[effectiveTime]?fhir\_vs=refset/\[refsetId]\
\[/code]\
\[code]\
for example\
\[/code]\
\[code]\
GET \[fhir]/ValueSet/$validate-code\
?system=http://snomed.info/sct\&code=181216001\
\&url=http://snomed.info/sct/900000000000207008/version/20200131?fhir\_vs=refset/723264001\
\[/code]\
\[code]

\[/code]

\| Returns a JSON object with a "Parameters" resource, including a "result" parameter with a boolean value (true/false) indicating whether the member validated OK or not against the reference set.

### Accessing the Reference Set in a Relational Database

If the Reference Set has been loaded in a relational database using a model that complies with the RF2 specification for tables and column names, the reference set content can be accessed using SQL queries in line with the examples below:

| **Service Name**                         | \*\*SQL Query [6](https://confluence.ihtsdotools.org/display/WIPTSG/4.6+Get+and+Test+Reference+Set+Membership#footnotes) \*\* | **Result** |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ---------- |
| **Get all members of the reference set** |                                                                                                                               |            |
| \[code]                                  |                                                                                                                               |            |

```
SELECT referencedComponentId FROM snap_refset_simple
    WHERE active=1 AND refsetId=[refsetId];
```

\[/code]

for example\
\[code]\
SELECT referencedComponentId FROM snap\_refset\_simple\
&#x20;   WHERE active=1 AND refsetId=1303957004;\
\[/code]

\| Returns the ids of all the concepts or descriptions that are the members of the reference set.

**Test if a concept is a member of the reference set**|\
\[code]\
SELECT count(referencedComponentId)\
&#x20;   FROM snap\_refset\_simple\
&#x20;   WHERE active=1 AND refsetId=\[refsetId]\
&#x20;    AND referencedComponentId=\[candidateComponentId];\
\[/code]

for example\
\[code]\
SELECT count(referencedComponentId)\
&#x20;   FROM snap\_refset\_simple\
&#x20;   WHERE active=1 AND refsetId=1303957004    \
AND referencedComponentId=53120007;\
\[/code]

\| Returns:

* 0 : if the candidate component is not in the reference set.
* 1 : If the candidate component is a member of the reference set
  * Some types or reference set can include the same component more than once, so any value greater than zero indicate the component is a member of the references set.
