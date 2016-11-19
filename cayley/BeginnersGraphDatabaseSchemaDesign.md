# Beginner's Guide to Graph Database Schema Design
## Overview of this Guide
After you read this guide, you will have an understanding of the following concepts:
1. What is a graph and how it can store concepts
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


## Finding and Understanding Existing RDF Schemas


## Extending Existing Schemas


## What is a Quad


## Expressing your graph using N-quads
