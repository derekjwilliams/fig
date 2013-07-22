# Description

Fig a general purpose graph application with the ability to add types and methods (think MonkeyPatching).  It's basically a framework that can be  customized by IT staff or consultants for specific domains, e.g. patient management, blackboard replacement, asset management.

## Details

An Item is a Vertex, i.e. extends Vertex.  

The Phenotype captures attributes of a specific behavior or functionality that an Item of a specific type may exhibit, as such, an Item has an allowed set of Phenotypes.  The term Facet could be used instead of Phenotype if that is any more clear.

### Confused?  An example might help

In a patient management application the Phenotypes might be

* Healthcare consumer
* Insurance member
* Lab test subject

The Phenotypes above would be added to a PatientVertex (Item) in the graph of a patient management application.  And, as expected, the type of "Patient".

The Item can then have the key:value pairs described by the Phenotype, e.g. the Vertex attributes that the Item has.  The actual Vertex in the graph store may not need to include the references to the Phenotypes, but currently it does.

The Phenotypes catalog is currently in a relational database, but could be moved to a graph store or a key:value store.  A typical domain would only need a few hundred Phenotypes, so storage size is not a issue, and using the ORM and Model classes included with Play! are a little easier to work with.

You may have already guessed that an Item Edge has similar semantics.

## Why this craziness!?!?

This approach avoids creating concrete classes or interfaces so that end user IT staff can create new Item types on the fly.

The graph itself appears to store objects of specific types so it could be deserialized to a domain specific set of classes if ever needed, e.g. for very high performance.

I have not implemented any time variant attributes, or rules (time variant or other).  I'm currently running with Play! 1.2 and Orient, but FIG is in development and uses Play 2.1 and Neo4j 1.9.  I also want to implement simple agents (e.g. consumers and producers  in an economics simulation).
