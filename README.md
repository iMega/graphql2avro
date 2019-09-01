# Graphql2Avro


### Graphql

```
type Query {
    collection(id: ID): Collection!
}

interface Node {
    id: ID!
}

type Collection implements Node {
    id: ID!
    title: String!
    description: String!
    items(offset: Int, limit: Int): CatalogItemCollection
}

type CatalogItemCollection {
    totalCount: Int!
    entities(offset: Int, limit: Int): [CatalogItem]
}

union CatalogItem = Product | Collection

type Product implements Node {
    id: ID!
    title: String!
    description: String!
    sku: String
}
```

### Avro

```
{
    "namespace": "ru.imega.collection",
    "type": "record",
    "name": "collection",
    "aliases": ["version", "1.0"],
    "doc": "collection data",
    "fields" : [
        {"name": "id", "type": "string"},
        {"name": "title", "type": "string"},
        {"description": "title", "type": "string"}
    ]
}

{
    "namespace": "ru.imega.product",
    "type": "record",
    "name": "product",
    "aliases": ["version", "1.0"],
    "doc": "product data",
    "fields" : [
        {"name": "id", "type": "string"},
        {"name": "title", "type": "string"},
        {"description": "title", "type": "string"},
        {"sku": "title", "type": "string"}
    ]
}
```