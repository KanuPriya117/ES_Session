# Creating & Deleting Indices

## Creating an index (with settings)

```
PUT /pages
{
  "settings": {
    "number_of_shards": 2,
    "number_of_replicas": 2
  }
}
```

## Deleting an index

```
DELETE /pages
```

# Indexing documents

PUT /products
{
  "settings": {
    "number_of_shards": 2,
    "number_of_replicas": 2
  }
}

## Indexing document with auto generated ID:

```
POST /products/_doc
{
  "name": "Coffee Maker",
  "price": 64,
  "in_stock": 10
}
```

## Indexing document with custom ID:

```
PUT /products/_doc/100
{
  "name": "Toaster",
  "price": 49,
  "in_stock": 4
}
```

# Retrieving documents by ID

```
GET /products/_doc/100
```

# Replacing documents

```
PUT /products/_doc/100
{
  "name": "Toaster",
  "price": 79,
  "in_stock": 4
}
```

# Updating documents

## Updating an existing field

```
POST /products/_update/100
{
  "doc": {
    "in_stock": 3
  }
}
```

## Adding a new field

_Yes, the syntax is the same as the above. ;-)_

```
POST /products/_update/100
{
  "doc": {
    "tags": ["electronics"]
  }
}
```

# Upserts

```
POST /products/_update/101
{
  "upsert": {
    "name": "Blender",
    "price": 399,
    "in_stock": 5
  }
}
```

# Deleting documents

```
DELETE /products/_doc/101
```

# Delete by query

## Deleting documents that match a given query

```
POST /products/_delete_by_query
{
  "query": {
    "match_all": { }
  }
}
```