# Limits and Pagination

There are two ways to apply a limit and offset rows:

* query params 
* request headers

## query params

Using **limit** and **offset** parameters

```sql
GET /people?limit=15&offset=30 HTTP/1.1
```

## request headers

Using **Range** in request header

```sql
GET /bigtable HTTP/1.1
Range-Unit: items
Range: 0-24
Prefer: count=exact
```

> **Prefer: count=exact**  obtain the total size of results in a pagination control

```sql
HTTP/1.1 206 Partial Content
Range-Unit: items
Content-Range: 0-24/3573458
```

> **Partial Content**  respond with the selected range

