# Analysis of OMOP data model

Vojtech Huser
Sebastiaan van Sandijk

done column indicates analysis was completed for a given table

first tab has input data
subsequent tabs are pivot views of the input data

In designing our purpose-specific [logical] model (see some published info [here](https://github.com/informaticsrepo/omop-onc)), we use the term entity for high level constructs. In OMOP, the counterpart of entity would be table.

Our model adopts the CodeableConcept from FHIR standard. This allows capture of "source_concept_id" without the need to maintain an associated model's terminology layer (=Athena for OMOP) and still allows embracing a number of source terminologies.

# Counts

OMOP has 432 fields

## _concept_id
119 fields (27.6%)  are using the concept_id paradigm.

## source_value
47 fields (10.9%) are source value fields

# Other conventions
## parroting
A model may not have repeat in column name the specific context (e.g., condition_occurrence.start_date) and rely on table context to provide this information.
Or a model does indeed repeat (is "parotting") the context in an effort to be more specific. (e.g.,condition_occurrence.**condition**_start_date
It also is a consideration when doing table joins. If table needs to refer to multiple concepts, then it must distinguish somehow (obviously).

## short names for entities (tables)
Some columns use in parroting a shorter version of the entity. Either the name would be shortened or parroting would be consistent.
e.g.,  
condition_occurrence.condition_occurrence_start_date  
or  
condition.condition_start_date


# Person table

![image](https://github.com/user-attachments/assets/f9d5d94f-a772-4dcb-b5b5-b8477c27ae93)

