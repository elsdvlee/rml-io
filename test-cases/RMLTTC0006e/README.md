## RMLTTC0006e

**Title**: Target TarGzip compression

**Description**: Test export all triples with TarGZip compression

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
    rml:path "./dump1.nq.tar.gz";
  ];
  rml:serialization formats:N-Quads;
  rml:compression rml:targz;
.

```

**Output 1**
```

```

**Output 2**
```
�      ���j�0�\�)B -�ҋ��0�����j &N-�o?�޸9�l��	ϟ1���%��D/UjX�6��@F*%R�H('�$B�O)�➥&��
�$�:�����jWv]�ȹ��v����bO�ח���e�⧠O\0�ua�t��~������LӃq�4s��j]z���8zh��s��%5�u��K0W�����jo�F�K����c��R��?�d}17I-�]���%�����۷                �o�M��( (  
```

