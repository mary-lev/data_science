# 6. Processing and querying the data

## Summary of the previous lectures

A datum is a declarative statement  <span style="color:#CC0000">subject</span> \- <span style="color:#3C78D8">predicate</span> \- <span style="color:#6AA84F">object</span>  that\, through the  <span style="color:#3C78D8">predicate</span> \, either  __attributes__  a  <span style="color:#6AA84F"> __literal__ </span>  \(i\.e\. a value such as a string\, a number\, etc\.\) to a  <span style="color:#CC0000">subject </span>  <span style="color:#CC0000"> __entity__ </span>  <span style="color:#CC0000"> </span>  _or_  it  __relates__  such a  <span style="color:#CC0000">subject </span>  <span style="color:#CC0000"> __entity__ </span>  with  <span style="color:#6AA84F">another </span>  <span style="color:#6AA84F"> __entity__ </span>

Each entity\, being used either as  <span style="color:#CC0000">subject</span>  or  <span style="color:#6AA84F">object</span>  of a statement\, is characterised by  __a unique identifier__

The  __same entity__  can be used as  <span style="color:#CC0000">subject</span>  or  <span style="color:#6AA84F">object</span>  in one or more data\, while a literal  __cannot be used__  as  <span style="color:#CC0000">subject</span>  in any datum

An attribute is intrinsically  __part of__  the  <span style="color:#CC0000">entity</span>  to which it is associated – modifying the value of an attribute affect  __only__  the  <span style="color:#CC0000">entity</span>  to which it refers to

A data model is an abstract\, simplified and formal representation of some data related to a system or a real domain\, and enables us to describe what a data collection is about and to check data correctness

A data model permit one to specify classes of entities\, their attributes and relations

## Relationships between model and data

![](img/03-Processing_and_querying_the_data2.png)

<span style="color:#3C78D8">publicationVenue</span>

<span style="color:#6AA84F"> _“10\.1016/s1367\-5931\(02\)00332\-0”_ </span>

<span style="color:#6AA84F"> _“_ </span>  <span style="color:#6AA84F"> _In vitro selection as a powerful tool for the applied evolution of proteins and peptides_ </span>  <span style="color:#6AA84F"> _”_ </span>

<span style="color:#6AA84F"> _“_ </span>  <span style="color:#6AA84F"> _Current Opinion in Chemical Biology_ </span>  <span style="color:#6AA84F"> _”_ </span>

## Querying data according to their structure

As we anticipated\, data always define graphs of entities related to each other or having attributes specified

However\, often data are actually represented by formats that force a particular kind of structure\, a structure that obliges one to write a query for assessing data according to the particular data structure in consideration \(graph\, tree\, table\, etc\.\)

In this lecture we provide the intuition on how to deal with the same query depending on the format we are considering to store the data mentioned in the previous slide

Queries \(in natural language\):

<span style="color:#BF9000">Return the title of the publication with DOI  “10\.1016/s1367\-5931\(02\)00332\-0”</span>

<span style="color:#BF9000">Return the name of the venue of the publication with DOI “10\.1016/s1367\-5931\(02\)00332\-0”</span>

## Data structured as tables

As mentioned in the previous lecture\, usually the data referring to the same class are handled within one table \(e\.g\. the table Publication listed below\)

When dealing with a query\, you can access only one table to retrieve the answer of such a query – of course\, if the answer is included there\, then you finished\, as in the case of the query  <span style="color:#BF9000">r</span>  <span style="color:#BF9000">eturn the title of the publication with DOI “10\.1016/s1367\-5931\(02\)00332\-0”</span>

However\, sometimes\, gathering the answer is possible only after we analyse two or more tables simultaneously\, since we need to have a larger view of our data to retrieve the correct information\, e\.g\. for the query  <span style="color:#BF9000">r</span>  <span style="color:#BF9000">eturn the name of the venue of the publication with DOI “10\.1016/s1367\-5931\(02\)00332\-0” </span> where we must access both Publication and Venue table to retrieve the answer

| internalId | doi | title | publicationYear | publicationVenue |
| :-: | :-: | :-: | :-: | :-: |
| Entity 1 | “10.1016/s1367-5931(02)00332-0” | “In vitro selection…” | 2002 | Entity 2 |

## Sketch of the resolution of complex query in tables

Query:  <span style="color:#BF9000">return the name of the venue of the publication with DOI “10\.1016/s1367\-5931\(02\)00332\-0”</span>

To answer the query above that involves two or more table\, join all the tables that are necessary to come to the answer into one \(virtual\) bigger table containing all the information

<span style="color:#CC0000">Join via B and D</span>

| A | B | C |
| :-: | :-: | :-: |
| X1 | Y1 | W1 |
| X2 | Y2 | W2 |
| X3 | Y1 | W3 |

| D | E |
| :-: | :-: |
| Y1 | Z1 |
| Y2 | Z2 |

| A | B | C | D | E |
| :-: | :-: | :-: | :-: | :-: |
| X1 | Y1 | W1 | Y1 | Z1 |
| X2 | Y2 | W2 | Y2 | Z2 |
| X3 | Y1 | W3 | Y1 | Z1 |

# 

__Query: __  <span style="color:#BF9000">return the name of the venue of the publication with DOI “10\.1016/s1367\-5931\(02\)00332\-0”</span>

## Table query resolution: example

| internalId | doi | title | publicationYear | publicationVenue |
| :-: | :-: | :-: | :-: | :-: |
| Entity 1 | “10.1016/s1367-5931(02)00332-0” | “In vitro selection…” | 2002 | Entity 2 |

| internalId | id | name |
| :-: | :-: | :-: |
| Entity 2 | “1367-5931” | “Current Opinion…” |

<span style="color:#3C78D8"> __Publication JOIN Venue__ </span>

| P.<br />internalId | doi | title | publicationYear | publicationVenue | V.internalId | id | name |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| Entity 1 | “10.1016/s1367-5931(02)00332-0” | “In vitro…” | 2002 | Entity 2 | Entity 2 | “1367-5931” | “Current…” |

## Data structured as graphs

Graphs are more flexible as a data structure since they are not tied to a particular tabular organisation\, and are easy to extend if new requirements are introduced in the data model

For instance\, if we structure a data model according to a tabular format\, the addition of one attribute of a given class results in rethinking entirely the table referring to that class – and some times\, it requires the creation of new tables that must be interlinked\, somehow\, with the existing ones

Using graph\-based formats for defining data\, the extension of a data model is handled simply by adding additional edges and nodes\, without changing the implicit structure of how data are organised

In addition\, the gathering of an answer for a given query is performed by browsing the components of the graph\, following the existing paths between nodes to reach the components representing the answer of a given query

## Sketch of the resolution of the query in graph

<span style="color:#CC0000">\[?1\]</span>   <span style="color:#3D85C6">j</span>   <span style="color:#6AA84F">B</span>  \+  <span style="color:#CC0000">\[?1\]</span>   <span style="color:#3D85C6">i</span>   <span style="color:#6AA84F">\[?2\]</span>  \+  <span style="color:#CC0000">\[?2\]</span>   <span style="color:#3D85C6">k</span>   <span style="color:#6AA84F"> _y_ </span>

# 

__Query: __  <span style="color:#BF9000">return the name of the venue of the publication with DOI “10\.1016/s1367\-5931\(02\)00332\-0”</span>

## Graph query resolution: example

![](img/03-Processing_and_querying_the_data3.png)

<span style="color:#3C78D8">publicationVenue</span>

<span style="color:#6AA84F"> _“10\.1016/s1367\-5931\(02\)00332\-0”_ </span>

<span style="color:#6AA84F"> _“In vitro selection as a powerful tool for the applied evolution of proteins and peptides”_ </span>

<span style="color:#6AA84F"> _“Current Opinion in Chemical Biology”_ </span>

## Take away

Depending on the structure in which data are stored \(or exposed\)\, you need to approach the queries from a different angle

When you have tabular data\, often you have to combine tables between them to obtain bigger \(virtual\) tables which contain the answer to a query

When you have graph data\, you explore the graph starting from “fixed” points \(i\.e\. known entities\, values\, predicates\) to find a pattern that is compliant with the query

