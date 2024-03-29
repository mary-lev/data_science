# 2. What is a datum and how it can be represented computationally

## Two questions

- <span style="color:#595959">What is a datum?</span>
- <span style="color:#595959">What is the difference between “datum” and “value”?</span>

## Value vs datum: an intuition

![](assets/images/raw.jpg)

## Datum: a definition

A datum is a declarative statement  <span style="color:#CC0000">subject</span> \- <span style="color:#3C78D8">predicate</span> \- <span style="color:#6AA84F">object</span>

A datum either

- _attributes_  \(through the  <span style="color:#3C78D8">predicate</span> \) a value \(the  <span style="color:#6AA84F"> _“object”_ </span> \) to an entity \(the  <span style="color:#CC0000">subject</span> \)\, 

or

- _relates_  \(through the  <span style="color:#3C78D8">predicate</span> \) an entity \(the  <span style="color:#CC0000">subject</span> \) to another entity \(the  <span style="color:#6AA84F">object</span> \)

Examples:

- <span style="color:#CC0000">Entity 1</span>   <span style="color:#3C78D8">is a</span>   <span style="color:#6AA84F">Person</span>
- <span style="color:#CC0000">Entity 1</span>   <span style="color:#3C78D8">has given name</span>   _<span style="color:#6AA84F">“Silvio”</span>_
- <span style="color:#CC0000">Entity 2</span>   <span style="color:#3C78D8">is a</span>   <span style="color:#6AA84F">Document</span>
- <span style="color:#CC0000">Entity 2</span>   <span style="color:#3C78D8">has title</span>   <span style="color:#6AA84F"> _“What is a datum and how it can be represented computationally”_ </span>
- <span style="color:#CC0000">Entity 2</span>   <span style="color:#3C78D8">was created by</span>   <span style="color:#6AA84F">Entity 1</span>

## How to represent a datum

We can use a directed graph with labelled edges representing the  <span style="color:#3C78D8">predicate</span>  while the nodes identifies the  <span style="color:#CC0000">subject</span>  and the  <span style="color:#6AA84F">object</span>  of the declarative statement

![](assets/images/entity.jpg)

## Same data, in tabular form

![](assets/images/tablular.jpg)

## Attributes and relations

As anticipated\, each datum can be of two different types depending on the kind of  <span style="color:#6AA84F">object</span> :

1. __Attribute__ : associating a literal \(a string\, a number\, etc\.\,  _underlined_ \) to a subject entity <span style="color:#CC0000">Entity 1</span>   <span style="color:#3C78D8">has given name</span>   <span style="color:#6AA84F"> _“Silvio”_ </span>

2. __Relation__ : a labelled link between two entities <span style="color:#CC0000">Entity 2</span>   <span style="color:#3C78D8">was created by</span>   <span style="color:#6AA84F">Entity 1</span>

The object \(i\.e\. the node in the graph\) specified as an attribute of an entity cannot be reused in other data \(i\.e\. involved by more than one edge\)

However\, it is possible to have two distinct objects of two attributes that share the same value

## Attributes and relations: an example

![](assets/images/relations.jpg)

## Characteristics of attributes

<span style="color:#595959">An attribute is </span>  <span style="color:#595959">intrinsically</span>  <span style="color:#595959"> part of the entity to which it is associated</span>

<span style="color:#595959">It is reasonable that the attribute of an entity can have the same value of an attribute of another entity\, even when the same predicate is used \(e\.g\. </span>  <span style="color:#3C78D8">was born</span>  <span style="color:#595959"> in the previous example\)</span>

- <span style="color:#595959">There exists people born the same day</span>
- <span style="color:#595959">There exists people having the same given name</span>
- <span style="color:#595959">…</span>

<span style="color:#595959">However\, modifying the value of a certain attribute affects only the entity to which the attribute is associated</span>

## Alternatives to express data

![](assets/images/alternatives.jpg)

## It is important to express data correctly to avoid issues, but the right way depends on the context

## Some hints

1. Each entity in a collection is uniquely identified by an identifier that can be explicitly defined \(for instance\, in databases\, it is known as  _[primary key](https://en.wikipedia.org/wiki/Primary_key)_ \) or implicit \(as in the example in the table presented at the beginning of this lecture\)
2. When an object of a statement refers to a thing that\, potentially\, can be involved in other data \(as either a subject or an object\)\, then it should be described as an entity and not as a literal
3. When defining a collection of data\, it is necessary to use a predicate in the same way \(i\.e\. either to associate attributes or to define relations\)
4. Avoid to use two distinct predicates to convey the same semantics

## Laboratory

Material:

- An A4 sheet of paper
- A pen

\(alternatively\,  _[https://www\.yworks\.com/yed\-live/](https://www.yworks.com/yed-live/)_  or similar\)

Create a graph that describes the following scenario:

_The article entitled “OpenCitations\, an infrastructure organization for open scholarship” was published by the journal Quantitative Science Studies in 2020\. The authors of this article\, i\.e\. Silvio Peroni and David Shotton\, also co\-authored another conference paper entitled “The SPAR Ontologies”\, that was published in the Proceedings of the Seventeenth International Semantic Web Conference\, in 2018\._
