## RMLTTC0002k

**Title**: Multiple Targets: Datatype Map and Graph Map

**Description**: Test exporting all triples to a Target in a Datatype Map and a Target in a Graph Map.

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
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix ex: <http://example.org/> .
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
    rml:graphMap [ a rml:GraphMap;
      rml:constant ex:PeopleGraph; 
      rml:logicalTarget <#TargetDump1>;
    ];
    rml:predicateMap [ a rml:PredicateMap;
      rml:constant foaf:age;
    ];
    rml:objectMap [ a rml:ObjectMap;
      rml:reference "$.age";
      rml:datatypeMap [ a rml:DatatypeMap;
        rml:constant xsd:integer;
        rml:logicalTarget <#TargetDump2>;
      ];
    ];
  ];
.

<#TargetDump1> a rml:LogicalTarget;
  rml:target [ a rml:Target, rml:FilePath;
    rml:root rml:CurrentWorkingDirectory;
    rml:path "./dump1.nq";
  ];
  rml:serialization formats:N-Quads;
.

<#TargetDump2> a rml:LogicalTarget;
  rml:target [ a rml:Target, rml:FilePath;
    rml:root rml:CurrentWorkingDirectory;
    rml:path "./dump2.nq";
  ];
  rml:serialization formats:N-Quads;
.

```

**Output 1**
```
<http://example.org/0> <http://xmlns.com/foaf/0.1/name> "Monica Geller"@en .
<http://example.org/1> <http://xmlns.com/foaf/0.1/name> "Rachel Green"@en .
<http://example.org/2> <http://xmlns.com/foaf/0.1/name> "Joey Tribbiani"@en .
<http://example.org/3> <http://xmlns.com/foaf/0.1/name> "Chandler Bing"@en .
<http://example.org/4> <http://xmlns.com/foaf/0.1/name> "Ross Geller"@en .

```

**Output 2**
```
<http://example.org/0> <http://xmlns.com/foaf/0.1/age> "33"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/1> <http://xmlns.com/foaf/0.1/age> "34"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/2> <http://xmlns.com/foaf/0.1/age> "35"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/3> <http://xmlns.com/foaf/0.1/age> "36"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/4> <http://xmlns.com/foaf/0.1/age> "37"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .

```

**Output 3**
```
<http://example.org/0> <http://xmlns.com/foaf/0.1/age> "33"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/1> <http://xmlns.com/foaf/0.1/age> "34"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/2> <http://xmlns.com/foaf/0.1/age> "35"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/3> <http://xmlns.com/foaf/0.1/age> "36"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/4> <http://xmlns.com/foaf/0.1/age> "37"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .

```

