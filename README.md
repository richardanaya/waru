# waru
Distributed map reduce using web assembly

# Node API
/GET/info
* returns json info about this waru node

/POST/kernel
* takes in bytes of a web assembly module as bytes of body to used as map reduce processor

/POST/mapreduce/<function>
* takes in data to map reduce as a json array in body
* returns a json array of results

# Running as a node

```
waru
```

# Running as a router

```
waru router a.mynode.com b.mynode.com c.mynode.com
```
