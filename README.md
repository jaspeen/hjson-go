# thjson-go

Experiment to add type qualifiers for [hjson](https://hjson.org/) format. Based on https://github.com/hjson/hjson-go hjson parser.

Idea is to have equivalent of [yaml tags](http://yaml.org/spec/1.2/spec.html#id2764295) to annotate objects with some word what can be interpreted by parser client to construct appropriate object from plain map.
Following thjson:
```
  {
    field1: value
    field2: @mytype {
       typeField1: val
       typeField2: val
    }
    array: [ 
      @mytype2 {
         field: val
      }
      @mytype3 {
         field: val
      }
    ]
  }
```
will be translated to following structure:
```
  {
    "field1": "value"
    "field2": {
       "@type": "mytype",
       "typeField1": "val",
       "typeField2": "val"
    }
    "array": [ 
       {
         "@type": "mytype2",
         "field": "val"
      },
      {
         "@type": "mytype2",
         "field": "val"
      }
    ]
  }
```
Then **@type** property can be used to reconstruct object type
# Install

Make sure you have a working Go environment. See the [install instructions](http://golang.org/doc/install.html).

To install thjson run:

```sh
go get -u github.com/jaspeen/thjson-go
```

# Usage
See https://github.com/hjson/hjson-go

