# RDF and SPARQL #

## Querying data

### The Turtle file

Turtle files are used for importing data into a triple store.  There are a couple of important things to note about a Turtle file:

* prefixes are declared with the @prefix keyword  and *all* statements end with a period, so

```txt
@prefix ab: \<http://www.something.com/ns/cats#> .
```

* comments begin with the \# character

```txt
# ex002.ttl
```

The Turtle files extension is .ttl

### The SPARQL file

SPARQL query files are designated with a .rq extension; update files with a .ru.  (Are delete files handled differently?)




