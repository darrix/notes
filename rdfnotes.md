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

#### Namespaces

The namespaces that you define will usally end with either a # or a '/' character.  I think I understand that the hash endings are in relative disfavor now but I don't know that for sure.  Need to check that out.  
When namespaces are combined with the base part of the UUID, are there rules governing what happens if two slashes meet?  This shouldn't happen much but it is something to look at.

In SPARQL files, PREFIX statements **do not** have \@ characters prepended to the word PREFIX and the lines do not end with a period at the end.

The form of the SELECT statement is 
```
PREFIX ab: <http://www.somepath.com/ns/thing#>
SELECT ?heightInCM
WHERE {
    ab:Tom ab:height ?heightInCM .
}
```

Notice that SPARQL is not case-sensitive in the keywords.  (Is it a problem with variable names?)

Like F#, SPARQL is using pattern matching--here saying "find all Tom values that have a height property and return their value in the heightInCM variable"









