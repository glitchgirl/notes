# Module 1:
## The importance of Knowledge Graphs and Yext Content
- What is a knowledge graph
    - A knowledge graph is a "brain like" graph. Also something like a map graph

    - yext calls this a "yext content"

    - An entity is a real world object within your knowledge graph (job, event, person, product, etc)


- Entities in a knowledge graph
    - Different types of entities, based on whatever you are trying to solve
    - Which entities to prioritize, based on whatever you are trying to solve

- how Yext helps you structure content
    - Built in entity types
        - default types
    - Custom entity types
        - create your own if the defaults aren't enough
    - Linked Entities
        - interrelated entities
    - Entity upload tool


# Module 2:
## Navigating Yext Content
- how to navigate around content
- Key screens
    - entities
    - entity edit
    - assets
    - suggestions
    - connectors (anything that takes data from another source and transforms into entities)
    - configuration
    - history
    - enhanced content lists (ECLs) - this to send structured data to listings publishers like google maps

- Terminology

# Module 3:
## Introduction to Entity Types
- What is an entity
    - An entity is the primary object stored in Yext content (like a row in a database). 
    - They have a type (location, person, custom), and are comprised of fields (name, address, etc)
    - Entities are comprised of two parts:
        - metadata (type, ID, language, and country)
        - fields (values of actual information)
    - entities are just a list of field-value pairs
    ```
    "name": "Yext",
    "address":{
        "city": "New York"
    },
    ```
- The difference between custom and built-in entity types
- how to enable/disable types in your account
- how to create custom entity types
