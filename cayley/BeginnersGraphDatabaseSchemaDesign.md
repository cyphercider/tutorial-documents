# Beginner's Guide to Graph Database Schema Design
## Overview of this Guide
After you read this guide, you will have an understanding of the following concepts:
1. What is a graph and how it can store concepts
2. What is a triple and how can it define a graph
3. What is RDF
4. Finding and Understanding Existing Schemas
5. Extending Existing Schemas
6. Saving your triples to a file using N-triples
7. What is a quad
8. Saving your quads to a file using N-quads
## What is a graph?
A graph has two elements: vertices and edges.  A vertex is an entity, and an edge is a relationship between two entities.
## What is a triple?
A triple is a 3-word statement that specifies a single relationship (edge) between two entities (vertices).  As an example: Bob and Samantha are both entities.  The 3-word statement: "Bob" "knows" "Samantha" specifies that the entity "Bob" is related to "Samantha" in that he "knows" her.  In a graph, "Bob" and "Samantha" are both vertices, and "knows" is an edge connecting "Bob" to "Samantha".  Groups of triples can describe any graph.
