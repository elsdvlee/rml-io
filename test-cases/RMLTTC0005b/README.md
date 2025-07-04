## RMLTTC0005b

**Title**: Target UTF-16

**Description**: Test export all triples with UTF-16 encoding

**Error expected?** No

**Input**
```
[
  { 
    "id": 0,
    "name": "Monica Geller",
    "age": 33
  },
  { 
    "id": 1,
    "name": "Rachel Green",
    "age": 34
  },
  { 
    "id": 2,
    "name": "Joey Tribbiani",
    "age": 35
  },
  { 
    "id": 3,
    "name": "Chandler Bing",
    "age": 36
  },
  { 
    "id": 4,
    "name": "Ross Geller",
    "age": 37
  }
]

```

**Mapping**
```
@prefix rml: <http://w3id.org/rml/> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix formats: <http://www.w3.org/ns/formats/> .
@base <http://example.com/rules/> .

<#TriplesMap> a rml:TriplesMap;
  rml:logicalSource [ a rml:LogicalSource;
    rml:source [ a rml:FilePath;
      rml:root rml:MappingDirectory;
      rml:path "Friends.json";
    ];
    rml:referenceFormulation rml:JSONPath;
    rml:iterator "$[*]";
  ];
  rml:subjectMap [ a rml:SubjectMap;
    rml:template "http://example.org/{$.id}";
    rml:logicalTarget <#TargetDump1>;
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

<#TargetDump1> a rml:LogicalTarget;
  rml:target [ a rml:Target, rml:FilePath;
    rml:root rml:CurrentWorkingDirectory;
    rml:path "./dump1.nq";
  ];
  rml:serialization formats:N-Quads;
  rml:encoding rml:UTF-16;
.

```

**Output 1**
```

```

**Output 2**
```
��< h t t p : / / e x a m p l e . o r g / 0 >   < h t t p : / / x m l n s . c o m / f o a f / 0 . 1 / a g e >   " 3 3 "   . 
 < h t t p : / / e x a m p l e . o r g / 0 >   < h t t p : / / x m l n s . c o m / f o a f / 0 . 1 / n a m e >   " M o n i c a   G e l l e r "   . 
 < h t t p : / / e x a m p l e . o r g / 1 >   < h t t p : / / x m l n s . c o m / f o a f / 0 . 1 / a g e >   " 3 4 "   . 
 < h t t p : / / e x a m p l e . o r g / 1 >   < h t t p : / / x m l n s . c o m / f o a f / 0 . 1 / n a m e >   " R a c h e l   G r e e n "   . 
 < h t t p : / / e x a m p l e . o r g / 2 >   < h t t p : / / x m l n s . c o m / f o a f / 0 . 1 / a g e >   " 3 5 "   . 
 < h t t p : / / e x a m p l e . o r g / 2 >   < h t t p : / / x m l n s . c o m / f o a f / 0 . 1 / n a m e >   " J o e y   T r i b b i a n i "   . 
 < h t t p : / / e x a m p l e . o r g / 3 >   < h t t p : / / x m l n s . c o m / f o a f / 0 . 1 / a g e >   " 3 6 "   . 
 < h t t p : / / e x a m p l e . o r g / 3 >   < h t t p : / / x m l n s . c o m / f o a f / 0 . 1 / n a m e >   " C h a n d l e r   B i n g "   . 
 < h t t p : / / e x a m p l e . o r g / 4 >   < h t t p : / / x m l n s . c o m / f o a f / 0 . 1 / a g e >   " 3 7 "   . 
 < h t t p : / / e x a m p l e . o r g / 4 >   < h t t p : / / x m l n s . c o m / f o a f / 0 . 1 / n a m e >   " R o s s   G e l l e r "   . 
 
```

