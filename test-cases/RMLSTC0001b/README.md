## RMLSTC0001b

**Title**: Source with UTF-16 encoding

**Description**: Test source with UTF-16 encoding

**Error expected?** No

**Input**
```
��[ 
     {   
         " i d " :   0 , 
         " n a m e " :   " M o n i c a   G e l l e r " , 
         " a g e " :   3 3 
     } , 
     {   
         " i d " :   1 , 
         " n a m e " :   " R a c h e l   G r e e n " , 
         " a g e " :   3 4 
     } , 
     {   
         " i d " :   2 , 
         " n a m e " :   " J o e y   T r i b b i a n i " , 
         " a g e " :   3 5 
     } , 
     {   
         " i d " :   3 , 
         " n a m e " :   " C h a n d l e r   B i n g " , 
         " a g e " :   3 6 
     } , 
     {   
         " i d " :   4 , 
         " n a m e " :   " R o s s   G e l l e r " , 
         " a g e " :   3 7 
     } 
 ] 
 
```

**Mapping**
```
@prefix rml: <http://w3id.org/rml/> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@base <http://example.com/rules/> .


<#TriplesMap> a rml:TriplesMap;
  rml:logicalSource [ a rml:LogicalSource;
    rml:source [ a rml:FilePath;
      rml:root rml:MappingDirectory;
      rml:path "Friends-UTF16.json"
    ];
    rml:referenceFormulation rml:JSONPath;
    rml:iterator "$[*]";
  ];
  rml:subjectMap [ a rml:SubjectMap;
    rml:template "http://example.org/{$.id}";
  ];
  rml:predicateObjectMap [ a rml:PredicateObjectMap;
    rml:predicateMap [ a rml:PredicateMap;
      rml:constant foaf:name;
    ];
    rml:objectMap [ a rml:ObjectMap;
      rml:reference "$.name";
    ];
  ];
  rml:predicateObjectMap [ a rml:PredicateObjectMap;
    rml:predicateMap [ a rml:PredicateMap;
      rml:constant foaf:age;
    ];
    rml:objectMap [ a rml:ObjectMap;
      rml:reference "$.age";
    ];
  ];
.

```

**Output**
```
<http://example.org/0> <http://xmlns.com/foaf/0.1/age> "33" .
<http://example.org/0> <http://xmlns.com/foaf/0.1/name> "Monica Geller" .
<http://example.org/1> <http://xmlns.com/foaf/0.1/age> "34" .
<http://example.org/1> <http://xmlns.com/foaf/0.1/name> "Rachel Green" .
<http://example.org/2> <http://xmlns.com/foaf/0.1/age> "35" .
<http://example.org/2> <http://xmlns.com/foaf/0.1/name> "Joey Tribbiani" .
<http://example.org/3> <http://xmlns.com/foaf/0.1/age> "36" .
<http://example.org/3> <http://xmlns.com/foaf/0.1/name> "Chandler Bing" .
<http://example.org/4> <http://xmlns.com/foaf/0.1/age> "37" .
<http://example.org/4> <http://xmlns.com/foaf/0.1/name> "Ross Geller" .

```

