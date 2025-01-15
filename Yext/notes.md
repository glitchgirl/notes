# Module 1:
## The importance of Knowledge Graphs and Yext Content :tm:
- What is a knowledge graph
    - A knowledge graph is a "brain like" graph. Also something like a map graph

    - yext calls this a "Yext Content :tm:"

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
## Navigating Yext Content :tm:
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
    - An entity is the primary object stored in Yext Content :tm: (like a row in a database). 
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


# Module 5:
## Data modeling in Yext
- Principles of data modeling
- difference between entity types and fields
    - entities are things
    - fields describes that thing
    - fields have permissions, but sub-fields don't
    - anything listed on google maps needs to be a built in entity with an address
    - remember to turn on ECLs if you want it to sync with maps
- when & how to link entities together
    - This is done via the entity relationship custom field type
    - one way relationships (a product is available at a location)
        - the source entity
        - the destination entity
        - the relationship context (the field)
    - two way (shared field) relationships (person A and person B are siblings)
        - the related entities
        - the relationship context (shared field)
    - two way (distinct fields) relationships (a person works a company, a company staffs a person)
        - the related entities
        - two relationship context (two distinct fields)
    - the relationship is editable, and you can you use validation on types(i.e. this relationship only exists on location types) and item counts
    - search only uses name right now


# Module 7:
## Data connectors
- How the data connectors framework works
    - A connector is anything that takes data from a source and transforms it into entities in Yext Content :tm:
    - The framework is an ETL
        - Extract 
        - Transform (from whatever to something yext can use)
            - this includes things like formatting dates, or removing special chars. Some data sources are already "correct" and don't need to be transformed
        - Load (into your account)
            - after the connector runs, it will show you any errors it had
- Use cases for leveraging data connectors
- an overview of the available connector sources
    - generic sources - data sources that do not involve third party apps
        - most of these have a pre-built connector, but it isn't customizable
    - native sources - data sources that connect to third party apps
    - fill upload
    - FTP / SFTP (wowo)
    - crawler
    - API (push and pull)
    - functions (typescript)
- how to configure source settings to pull data from the correct endpoint
- how to specify selectors to pull in the relevant data components 
    - default selectors will pull in all identified selectors
- what transformers are
    - things like fix capitalization, merge columns, etc
- the type of transforms that are available with connectors
- how to map fields pulled in from your connector to fields in yext
    - when you are doing the mapping process, you can still map things that have errors, you can fix the error-ed ones after process. this might be good if most of your data is correct, but you have some that are wrong (maybe a field added later or something)
- how to run your connector
    - click run now
- how to view and adjust your existing connectors
    - you can duplicate connectors if you are going to need a similar one (i.e. multiple APIs)
- what connector run modes are
    - you can set frequency from some pre-done times or set a custom time
    - determines if the entities should be deleted in the run or not 
        - default run mode doesn't delete anything, it'll just add new ones and update existing ones. this is less risky, but you might have data that is stale
        - Comprehensive mode will delete things that aren't in the current pulled data set
            - this can be nice for some things like maybe services offered to keep it up to date (i.e. delete all old offers)
        - deletion the connector will delete everything supplied in the run. this is normally used for pushing back to a different source. for example, you want to delete sales from like shopify or something. 
- how to manage connector frequency and run modes
- when to use the various data connectors
    - "best" is hard to define, but in general using an API will be the most "correct" but take the most work. Pre-built connectors will be easier but might not be 100% what you need. 
    - less desirable would be file uploads or crawlers. these can be hard to use, and still not be "correct" 
    - be sure to pay attention to the entity id and only update it when you mean too. 
- important things to keep in mind when leveraging data connectors

# Module 8
## Yext Site Crawler & crawler connector
- how to create a crawler
    - you have to create a crawler before you can create a crawler connector
    - for best results you should white list both the user agent and IP addresses 
    - when setting up your crawler, decide if it should crawl all file (supported) types or select file types
    - you can also tell it what pages to avoid with a blacklist 
    - you can also add a rate limiter so you don't crash your website LOL 
    - crawler can only see public sites
    - crawler (as of right now) can only see desktop sites
- an overview of crawler settings
    - from the edit screen you can:
        - delete
        - disable 
- additional details on the crawler functionality
- how to convert crawled pages into entities
- using ```*``` you can get the most of the pages you need
- page types
    - detail page
        - this is a one-to-one relationship between the page and the entity (i.e. a blog post, individual product page)
    - list page
        - this is a one-to-many relationship between the page and the entities (i.e. FAQ pages, catalog pages)
        - need to provide something that points to the outer container for each entity on the page (i.e. the CSS "container" selector or xpath)
    - specify selectors
        - pre-built
            - page ID - unique for each unique URL 
            - Item Id - unique id for each item on a page (for list pages) it looks like ```[Page ID]-[Item Index]```
            - page URL
            - page title (defined by HTML)
            - cleaned body content
        - manual
            - css
                - class names
                - css selectors
                    - https://try.jsoup.org/
            - xpath
                - XML path
    - transformers
        - map to field
- an understanding of all connector settings for the crawler 
    - connector schedule
        - if you want the crawler to run again right after finishing a crawl set schedule to "auto", otherwise if you want to control when it runs set schedule to "manual"
- when to use a crawler
    - pulling in unstructured long-form content (blog posts)
    - highly structured pages
- when not to use a crawler
    - when content is changing frequently
    - pages not as structured as the entity types you are trying to map it too
    - one time imports can be good to set up the flow
- entity IDs! remember to not update them unless you REALLY mean it 

# Module 10
## Embedded Fields
- how to use embedded fields to create unique content at scale
- what are embedded fields
    - embedded fields allow you to dynamically insert fields within other text fields from a single profile. they use the example of madlibs. 
    - they look like: ```vist our location in [[address.city]]```
- how to add embedded fields
    - only text fields and subfields can have embedded fields
    - types that can be embedded:
        - strings
        - options
        - text lists
        - addresses
        - entity ids
        - other fields might come later
    - the embedded icon is a little plus sign in the corner of other fields. kinda looks what you would expect to expand the field box
    - you can also use this in APIs
- how embedded fields work 
    - creating unique content at scale
    - helping content stay fresh and accurate
    - URL and URL tracking management
        - you can add tracking to URLs that are dynamic
    - website field components
        - the url
        - the display url
        - an option "use my reg web link one" or "use the display URL only"
- embedded field use cases
- how embedded fields can help you
- seo value of differentiated content
- common use cases

# Module 14
## Save filters
- what is a saved filter and how it used across the platform
- what are saved filters
    - just a combination of different searches to help you get the data you actually want
- how advanced filters work
    - has things like AND / OR / CONTAINS / DOES NOT CONTAIN / EQUAL TO / STARTS WITH 
    - you can also looks for things "fields without data"
- how to save an advanced filter
    - there is a tiny greyed out save icon in a different location from all the other save buttons, you hit that to save it
    - you can also pin things
- how to find a saved filter ID
- how to create a saved filter
- different filter criteria available for saved filters
- why saved files are important
- use cases



|     |   PAGES   |         |
|-------------- |----------------|------------------ |

# Module 1
## Build your site
- What pages is
    - Pages is a powerful platform for developing performant and SEO websites that leverage Yext Content :tm:
- how the pieces of the development process fit together
- these set up steps are pretty clear BUT
    - make sure you keep the same yext account ID (write it down somewhere)
    - make sure you follow the directions closely

# Module 2
## Customize your site
- templates
    - entity templates :ocean:
        - stream templates allow you to generate pages based on entities in your content that have the same styling and structure 
        - each "stream" is powered by a stream (content in JSON format)
        - each has config export. This is where you specify the entity and fields you require in your template. In the example, the location template is used. You can also apply filters here. 
        - these kinds of templates are useful for things that similarly structured but you need a lot of (product pages)
    - static page templates :no_entry_sign:
        - one off pages not powered by streams
        - config not necessary but allows you to name it
        - can still use data from Global Data (like headers and footers)
    - transformProps function can be used to make external API calls. this could be for getting content not in your Yext Content :tm: or to modify other props in the default export
- customize templates
- add new content
    - streams generated page templates creates pages for entities in the Yext platform
    - both the Content :tm: :tm:
- update a streams-generated page template and preview those changes
- update a static page 
