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
    - fields can be pre-built or custom like types
    - built in
        - handles things like default behavior
        - this is preferred
        - can be delivered to listings
        - can't update things like type, API name, or validation
    - custom
        - can't be delivered to listings
        - can update things like type, API name, or validation
- how to create custom fields
    - you can create a custom field from the fields page or from the entity type page. The key difference between these two methods are that if you create a field from the custom fields screens you can't set properties that are specific to a field on a given entity type. If you create a field in the custom fields the field will automatically be set to "other fields". This is preferred for adding multiple types, but if you just want to add a field to one type you should use the entity types page. 
    - standard field types (see list for all options)
    - you cannot change a field type after creation
    - other config options:
        - field name (make this human readable/understandable)
        - id
        - field settings (type and validation, and you can make things into lists)
        - alternate language behavior
        - field availability (this is how you add the fields to different types)
        - custom field permission group
        - tooltip description
- how to create custom field types
    - custom field types let you define a new complex field type using the standard field types as sub-fields
    - if you want to create a complex field inside a field (i.e. a CTA in a promotion) you should use the `struct` field which is a nested inline object. Don't go overboard with this. 
- how field sections and custom field groups work
- What are categories
    - category is a field on events and location like built in entity types. 
    - this is important for things like: listings, knowledge tags schema, pages schema, and taxonomy
    - yext maintains a complex taxonomy system for categories that map between yext and endpoints (i.e. google or schema.org)
    - This provides information that maps to third party things in the way the expect (i.e. google might have a different layout than apple etc)
    - Knowledge tags work similarly 
    - when doing your categories, you should strive for simple and accurate, not as many as possible
    - if needed you can override the default mappings, one case might be if a listing service doesn't have the category you'd like to use.
    - don't go overboard with these changes
    -  
