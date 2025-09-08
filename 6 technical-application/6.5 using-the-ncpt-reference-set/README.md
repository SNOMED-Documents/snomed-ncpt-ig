# Using the NCPT Reference Set

When working with the Nutrition Care Process Terminology (NCPT) reference set, it’s essential to have efficient access to the content through various systems, regardless of the technology used.

Clinical applications will access the Reference Set content from the selected terminology repository. The main functional requirements include listing all concepts in the Reference Set, filtering by text search strings, and validating whether a concept is a member of the Reference Set.

This page provides examples of how to interact with the reference set, whether you’re using a FHIR terminology server or a relational database like MySQL.

***

## Accessing the Reference Set from a FHIR Terminology Server

When working with the Nutrition Care Process Terminology (NCPT) reference set, leveraging a FHIR terminology server can simplify access and management.

A FHIR terminology server provides mechanisms to work with the Reference Set as a Value Set. The main operations available are $expand and $validate-code.

### FHIR Operations

**$expand — Get all members of the reference set**

Required:

*   A reference set specified by its refsetId, for example:

    1303957004 |Nutrition Care Process Terminology reference set (foundation metadata concept)|
* A list of concept or description IDs
* Option to include additional information about each concept or description

**$validate-code — Test if a concept or description is a member of the reference set**

Required:

* A reference set specified by its refsetId
* A candidate concept.id
* Returns TRUE if the candidate is a member, FALSE otherwise

***

#### Example FHIR Requests

_These examples use the concept 1303957004 |Nutrition Care Process Terminology reference set (foundation metadata concept)| as the refsetId._

**Get all members of the reference set**

**API Call:**

{% code overflow="wrap" %}
```
GET [fhir]/ValueSet/$expand?url=http://snomed.info/sct?fhir_vs=refset/[refsetId]&count=10
```
{% endcode %}

Example:

{% code overflow="wrap" %}
```
GET [fhir]/ValueSet/$expand?url=http%3A%2F%2Fsnomed.info%2Fsct%3Ffhir_vs%3Drefset%2F1303957004&count=10
```
{% endcode %}

Alternative using Expression Constraint Language (ECL):

<pre data-overflow="wrap"><code><strong>GET [fhir]/ValueSet/$expand?url=http%3A%2F%2Fsnomed.info%2Fsct%3Ffhir_vs%3Decl%2F%5E%5B1303957004%5D&#x26;count=10
</strong></code></pre>

or:

{% code overflow="wrap" %}
```
GET [fhir]/ValueSet/$expand?url=http%3A%2F%2Fsnomed.info%2Fsct%3Ffhir_vs%3Decl%2F%5E1303957004&count=10
```
{% endcode %}

**Result:**

Returns a JSON representation of the reference set members.

Each concept includes:

* code: the conceptId of the reference set member
* display: the preferred term for the reference set member

Also returns:

* total: the total number of reference set members

Paging Parameters:

* count: limits the number of members returned
* offset: specifies the start position in the results (in multiples of the limit)

***

**Test if a concept is a member of the reference set**

**API Call:**

{% code overflow="wrap" %}
```url
GET [fhir]/ValueSet/$validate-code?system=http://snomed.info/sct&code=181216001&url=http://snomed.info/sct/[moduleId]/version/[effectiveTime]?fhir_vs=refset/[refsetId]
```
{% endcode %}

Example:

{% code overflow="wrap" %}
```
GET [fhir]/ValueSet/$validate-code?system=http://snomed.info/sct&code=181216001&url=http://snomed.info/sct/900000000000207008/version/20200131?fhir_vs=refset/723264001
```
{% endcode %}

**Result:**

Returns a JSON object with a FHIR Parameters resource, including:

* result: a boolean value (true or false) indicating whether the concept is a member of the reference set

***

## Accessing the Reference Set in a Relational Database

If the Reference Set has been loaded into a relational database using a model that complies with the RF2 specification for tables and column names, the reference set content can be accessed using SQL queries.

***

### SQL Query Examples

#### Get all members of the reference set

SQL Query:

```sql
SELECT referencedComponentId FROM snap_refset_simple
    WHERE active=1 AND refsetId=[refsetId];
```

Example:

```sql
SELECT referencedComponentId FROM snap_refset_simple
    WHERE active=1 AND refsetId=1303957004;
```

Result:

Returns the IDs of all the concepts or descriptions that are members of the reference set.

***

#### Test if a concept is a member of the reference set

SQL Query:

```sql
SELECT count(referencedComponentId)
    FROM snap_refset_simple
    WHERE active=1 AND refsetId=[refsetId]
      AND referencedComponentId=[candidateComponentId];
```

Example:

```sql
SELECT count(referencedComponentId)
    FROM snap_refset_simple
    WHERE active=1 AND refsetId=1303957004    
      AND referencedComponentId=53120007;
```

Result:

* 0: if the candidate component is not in the reference set
* 1: if the candidate component is a member of the reference set

Some reference sets may include the same component more than once. Any value greater than zero indicates that the component is a member of the reference set.






<a href="https://docs.google.com/forms/d/e/1FAIpQLScTmbZIf0UEQwYDkY27EEWBkaiYkHSbR0_9DmFrMLXoQLyL7Q/viewform?usp=pp_url&entry.1767247133=NCPT+IG&entry.670899847=Using%20the%20NCPT%20Reference%20Set" class="button primary">Provide Feedback</a>
