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
    - in default entities you cannot remove fields, but you can add fields
    - default entities are compatible with 3rd party things, but custom entities are not
    - try to use default when possible for max ease and compatibility
- how to enable/disable types in your account
    - in the manage entity types page you can:
        - add custom types
        - enable or disable types (keep custom types disabled until you are ready for users to actually use it)
        - set a primary type. this is the default used for adding entities or when a type isn't specified. This also determines the default field labels. 
        - view details
        - edit fields
        - add an entity 
- how to create custom entity types
    - when you make a custom type you have complete control over:  
        - name, API name, description
        - fields with the exception of: ID, name, folder, and labels. this is so you can't break your API 
        - which fields are required
        - which fields are visible on the "add new entity" screen
    - custom entities cannot be used in listings
    - to create a type
        1. navigate to entity types page
        2. click "add custom entity type"
        3. enter the basic details, like name, API name(this is editable, but be cautious editing it later on), plural entity type name, and if you can multi-language name 
        4. add fields, besides the default fields of: ID, name, folder, and labels 
        5. decide if any of the fields should be required or not
        6. CLICK SAVE
        7. when you are ready for other users to use this entity type, enable it.
    - Entities aren't used in listings or pagers until you launch them 

# Module 4:
## introduction to fields
- what are fields in Yext
    - provide additional information about each entity type
    - ID, name, folder, and labels are on all types of entities
    - some fields are automatically added if you are subscribed to certain publishers (google attributes for example)
    - all fields have:
        - a type (string, phone, url)
        - display name
        - API name
        - validation
    - once defined, a field maintains the same properties like name and validation no matter where it appears
- difference between built in and custom fields
- how to create custom fields
- how to create custom field types
- how field sections and custom field groups work
