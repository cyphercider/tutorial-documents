# Beginner's Guide to Graph Database Schema Design

## Overview of this Guide
After you read this guide, you will have an understanding of the following concepts:

1. What is a graph and how can it store concepts
1. What is a triple and how can it define a graph
1. What is RDF
1. What is an RDF Concrete Syntax
1. Expressing Your Graph using N-triples
2. What is an RDF schema
1. Finding and Understanding Existing Schemas
1. Extending Existing Schemas
1. What is a quad
1. Saving your quads to a file using N-quads

## What is a graph?
A graph has two elements: vertices and edges.  A vertex is an entity, and an edge is a relationship between two entities.

## What is a triple?
A triple is a 3-word statement that specifies a single relationship (edge) between two entities (vertices).  As an example: Bob and Samantha are both entities.  The 3-word statement: "Bob" "knows" "Samantha" specifies that the entity "Bob" is related to "Samantha" in that he "knows" her.  In a graph, "Bob" and "Samantha" are both vertices, and "knows" is an edge connecting "Bob" to "Samantha".  Each term of a triple has its own name.  The first term is the "subject", the second term is the "predicate", and the third term is the "object".  Groups of triples can describe any graph.

## What is RDF?
RDF stands for "Resource Description Framework".  It is a standard maintained by the World Wide Web Consortium (W3C, https://www.w3.org/Consortium/) for describing information on the web.  More generally, RDF is a language for describing graphs (see, https://www.w3.org/TR/rdf11-concepts/#data-model).

## What is an RDF Concrete Syntax
RDF is not a "language" but rather a set of concepts.  There are several concrete syntaxes that can be used to write RDF.  These can be found under the W3C RDF-related standards at (https://www.w3.org/TR/#tr_RDF).  Common examples are Turtle, JSON-LD, and N-triples.  It can be very confusing for a beginner to be presented with several syntaxes, so for this guide, we will use the simplest one of all: N-triples. The N-triples specification can be found here (https://www.w3.org/TR/n-triples/).  

## Expressing Your Graph Using N-Triples
The N-Triples concrete syntax is a collection of an arbitrary number (N) of triples.  These triples are saved in a string, where each triple is:

1. On its own line
2. Composed of a subject, object, and predicate which are surrounded by angle brackets and separated by a space
3. Terminated with a space followed by a period (" .").  

Using our example above, the relationship between Bob and Samantha can be expressed in N-triples syntax as:

```
<Bob> <knows> <Samantha> .
```

Because a string in N-triples format can be any length and contain any number of triples, it can be used to describe a graph of any size or complexity.  For example, let's say that "Samantha" also knows "Bob", and "Bob" is the spouse of "Carolyn".  This expanded graph can be described by adding two more triples:

```
<Bob> <knows> <Samantha>
<Samantha> <knows> <Bob> .
<Bob> <is the spouse of> <Carolyn> .
```

## What is an RDF Schema
As explained previously, an RDF graph can be described by a collection of triples - each of which consists of a subject, predicate, and object.  An RDF schema is a collection of **types** of subjects, **types** of predicates, and **types** of objects.  Because an RDF schema describes the triples in a graph, an RDF schema is metadata.

Note that for a beginner, finding RDF schemas online can be confusing for the fact that not all RDF schemas are referred to as "RDF schemas".  They are sometimes referred to as "vocabularies", "languages", or "ontologies".  We are going to boil all of that down here and say that a schema is metadata that describes triples in a graph. period.

There are many published RDF schemas available online.  One of the most important is "RDF Schema" (https://www.w3.org/TR/rdf-schema/).  Note the confusion starts immediately...  "RDF Schema" is *an* RDF schema, not the only RDF schema.  Another RDF Schema, "Web Ontology Language (OWL)" (https://www.w3.org/TR/owl-guide/) is an *extension* of "RDF Schema" and is an RDF Schema in its own right.

## Components of an RDF Schema
As stated previously, an RDF Schema is *metadata* used to describe subjects, predicates, and objects in a graph.  At the highest level, in RDF, every subject, predicate, and object is referred to as a "Resource".  A resource can be either a specific thing, like "Bob", or a *type* of thing, like "Person".  In an RDF *schema*, a subclass of "Resource" called "Class" is used to define all of the metadata that makes up the schema.

### Examples of Schema Classes
The RDF Schema specification (https://www.w3.org/TR/rdf-schema/) defines some basic RDF classes.  For instance, the class "rdf:Property" is the class that defines "something that relates a subject resource to an object resource".  That is, a "rdf:Property" class describes the set of predicates in a graph.  An example sub class of "rdf:Property" is "rdf:type".  A predicate of class "rdf:type" is used to indicate that the subject of a triple is a *class of* the object of a triple.  Another example of a subclass of "rdf:Property" is "rdfs:label".  A predicate of class "rdfs:label" indicates that its object is a *human-readable* short description of its subject.

### Class prefixes
Note that the discrepancy in the above use of "rdf:" vs "rdfs:" is not a typo.  Because of how various RDF schemas evolved over time, prefixes on various rdf classes may differ.  A prefix is actually a stand-in for a full base URL that is used to aid readability.  In this case, the prefix "rdf:" actually refers to the namespace "http://www.w3.org/1999/02/22-rdf-syntax-ns#".  Such that "rdf:type" fully expanded is "http://www.w3.org/1999/02/22-rdf-syntax-ns#type.  Similarly, the prefix "rdfs:" refers to namespace "http://www.w3.org/2000/01/rdf-schema#", such that the class "rdfs:label" actually refers to "http://www.w3.org/2000/01/rdf-schema#label".  

## Web Ontology Language (OWL)
OWL deserves a special mention, and here we will give a brief explanation.  OWL is a widely-used extension of the "RDF Schema" specification.  the "owl:" prefix refers to the namespace "http://www.w3.org/2002/07/owl#".  An example class from the "owl:" namespace is owl:sameAs.  To type a triple "<subject> <owl:sameAs> <object>" indicates that subject and object are identical.  owl:sameAs as a property is useful when reconciling disparate schemas, to indicate that two graph vertexes are duplicates of one another.

## Finding and Understanding Other Published RDF Schemas
One of the motivations for the creation and standardization of RDF was to add a structure to content on the internet such that it could be more easily searched and organized.  It is an obvious truth that the creation of RDF standards, and the adherence to standards of many different users, improves the ease of linking many datasets together across the internet, and making sense of the relationships between the data.

There are many RDF schemas (also referred to as vocabularies or ontologies) that have been created and published for this purpose.  One site which has aggregated and made available many schemas is "Linked Open Vocabularies" (https://lov.okfn.org/dataset/lov).  One example schema which can be found by searching the site for "biology" is "UniProt RDF schema ontology" (http://www.uniprot.org/core).  The organization Universal Protein Resource (UniProt) (http://www.uniprot.org/help/about) is a "comprehensive resource for protein sequence and annotation data."  A biologist who is creating an RDF graph representing her research and wants to share that research with others would be better off using this schema from UniProt than creating her own.

## Extending Existing Schemas
Because RDF Schema and OWL are the most widely-recognized schema standards for RDF, when designing your project's schema, you should make use of all rdf: rdfs: and owl: schema terms that apply to your project, rather than duplicating those concepts.  In addition, if there are other widely-used schemas such as those which can be found at https://lov.okfn.org/dataset/lov, your project would do well to re-use those schemas as well, instead of defining your own.

Still, with any project in a specific-enough domain, there are likely schema concepts you will need to formalize on your own.  In these cases, you can use whatever published schemas are available, and where a given concept does not exist in those schemas, create new schema terms of your own.  If those schema terms prove to be widely applicable to your domain, you may consider registering your schema with https://lov.okfn.org/dataset/lov so that others can make use of it.

## What is a Quad
Cayley database can be used to store triples, but it can also be used to store an extended form of triple called a quad.  The first three elements of the quad are the same as a triple: subject, predicate, object.  However, a fourth term, "label" indicates that the specified triple is part of the subgraph indicated in the "label" field.  The concept of a quad was created to allow the expression of an "RDF Dataset", which is like a normal "RDF Graph" except that it can contain one or more subgraphs, also called "named graphs".  For a formal explanation of an "RDF Dataset" and its relationship to the quad, see (https://www.w3.org/TR/rdf11-datasets/#quad-semantics).

## Expressing your graph using N-quads
The N-quads concrete language specification (https://www.w3.org/TR/n-quads/) is analagous to the N-triples specification discussed above, but expresses quads rather than triples. As an example of using the N-quads specification, let's say you want to save an RDF dataset that stores both your friends and your acquaintances.  You want to be able to easily filter to the "friends" or "acquaintances" subgraphs for different purposes.  This RDF dataset expressed using N-quads may be:

```
<self> <owl:sameAs> <jeff> .
<self> <talksWith> <david> <friends> .
<self> <goesOutWith> <michelle> <friends> .
<self> <hasMet> <daniel> <acquaintances> .
<self> <hasDoneBusinessWith> <rachelle> <acquaintances> .
```

Note that a line written in N-Triples format is also a valid line in N-quads.  If a fourth term (label) is not specified within an N-quads file, the corresponding triple is assigned to the "default" graph.  Thus in the example above, the triple:

```
<self> <owl:sameAs> <jeff> .
```

Will be assigned to the "default" graph within the dataset.
