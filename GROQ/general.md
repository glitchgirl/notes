# GROQ

- Graph-relational object queries
- Queries look like this:

```
    *[]{} | Function()
```

- - all datasets
- [] filters
  - things like && || > etc
- {} return fields in an array
- functions include thing Order
- data isn't ordered by default
- Slicing
  - [0] or [0...100], returns stuff in that range
- References
  - Standard references are "hard" meaning the target must exist.
  - Refs can be set to \_weak - target doesn't have to exist

```
{
    stuff: "stuff"
    thing: _ref: {"another-thing"}
}
```

- Note: the \_ref returns the entire object referenced, not just a part.
- thing -> {field} to return a field from the ref object
- "fancy Name": thing -> name makes new field in the return object
- If the return type is an array, object[]->, remember to add [] otherwise you get an error
-
