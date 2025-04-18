# April updates
- Listings better screens
- You can now view and respond to direct messages
- Content is now renamed knowledge graph
- To make Headshot photo behavior more consistent, all photos uploaded to the Headshot field will be stored as-is.
- We’ve added the ability to export the display name (the Name field) of linked entities when performing an entity export. Previously, only the Yext ID and Entity ID of linked entities could be included in an export.

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
    - add the content
    - update the stream
    - update the template
    - preview
- update a static page 
    - can be updated like any web page 
    - external API call happens at build time not run time
- Customize components
    - it's best practice to create custom components defined in the components folder.
    - it's be practice to create custom components for any content on your site that will be repeated
    - all custom files or directories MUST live under the src directory for the templates to be able to see them
    - anything that ISN'T a template doesn't go inside the template folder
 
  ## Global Data
  - Learn about common use cases for using global data
  - Set up your content to easily configure global data
  - Set up a site stream to access global data in your site
      - edit it at the config.yaml 
      - fields
      - entity ids
      - locales (default is en)
# Module 3
## Deploy pages
- learn the three phases of deployment process
    - the initial build
        - generating all the static assets
        - this starts when code is pushed to github
        - config.yaml 
    - page generation
        -  generates the HTML web pages that make up the site
        -  uses streams
        -  afterwards, the CDN will serve is
    - ongoing data updates
        - the streams that were set up in step two are still active and you can use them to update pages or entities (might affect more than one page)
        - multi page updates are parallelized 
- learn how the process is structured for faster deployment and better performance
- Deploy changes to github and your yext sites
    - learn how to manage deploy preview, staging, and production links
    - navigate the details of individual deploys
    - on the top of the deploys screen there will be a production and staging link
- View data updates pushed to your deploys
    - production deployment
    - staging deployment
    - head deployment (most recent)
    - previous production deployment
    - once  a new deployment is made, all other deployments become inactive     
- learn how data updates are streamed to deploys

# Module 4
## Create a locator
- what a locator is
    - its just google maps except not
    - but no really why wouldn't I just use google maps? yext already integrates with it??
- add search to your yext account
- learn how search UI react helps you build a store locators in a pages project
- add search UI react to your project
- okay so after doing that whole unit I really don't see why you wouldn't just use google's. you need to set up an API anyways. the only thing I think is cool is the custom icons.

# Module 5
## The yext directory manager
- what directories are
- how to build them using yext directory manager
    - prepare your content
    - configure the direcory manager
    - run the directory manager
    - develop your directory site localy
    - deploy your directory sire to the platform
 
# Module 6
## Implement multi-language support
- Overview of multi-language pages
- Steps needed to implement multi-language support on Pages 
    - set up language profiles for content entities
        - a language profile is a "view" into an entity, for example you could have an English version and a Spanish version of the same entity (i.e. the description would be in both languages)
        - uses top level locales field
    - configure streams to accept multiple profiles
- Configure multi-lang entity profiles
    - how to set up language profiles in the content
    - how to configure slugs for multi-language pages
    - how to edit content on an alternative language profile
- Set up Multi-lang streams
    - how to access language profile data in your Pages UI
    - how to preview multi-lang pages
- Advanced Multi-lang support


|     |   SEARCH  Backend |         |
|-------------- |----------------|------------------ |

# Module 1
## Intro to search
- What is a search experience
    - define the three main components of search
        - Search Backend: configures how the search algorithm determines which results are selected
            - controlled by a search configuration 
            - search algorithm
        - Search Frontend: determines how results are displayed
            - facets or other filtering for uses
            - results cards
            - you can use the default Yext or use React libraries
        - Content: stores the entities and content 
    - Search quality
        - Content :tm: must be filed out correctly 
        - you'll need to contact support if you want your algorithm touched
    - describe how each of those components impacts the search experience and each other
    - identify which component allows you to manage certain behaviors in Search
- The Search Query Journey
    - list the steps that search goes through to deliver results when a user runs a query
        1. User submits a search query
        2. Algorithm routes queries via federated search
        3. Algorithm evaluates results in each vertical
        4. Algorithm aggregates the results and sends them via the search API
        5. Frontend assembles results for the user
    - recall that each vertical is evaluated by the search algorithm separately
    - explain that vertical results are combined and ranked on universal search 
    - Recall the methods available to build on top of Search and their use cases
        - search API
        - search core
        - search UI react
        - hitchhikers theme
    - Recognize which method of building the search frontend is right for you
    - navigate to the screens used to manage the search backend and search frontend
    - recall what types of information the all search experiences screen provides
    - recall the types of configures found under the five categories of screens for the search backend configuration 
        - test search
        - verticals
        - configuration
        - analysis
        - training
        - deployment

# Module 2
## Search Config Overview
- Define the search configuration
- list features the configuration can control 
    - Verticals
        - define each type of content you want to search on and the specific settings for that class of content
        - includes saved filters
        - define what fields to search
        - define how things should be ranked against other verticals
    - Query suggestions
    - Synonyms: you set these up for your business use (i.e. having both an acronym and the full spelling)
    - Query rules - set these up if you want something that the algo doesn't auto populate (maybe you want to point people to a booking page more than what the algo suggests)
    - General settings
- Create and edit the search config
    - demonstrate how to create a search config
    - edit the search config using the UI and the JSON editor
    - define configuration versions and configuration labels
    - best practices for which versions to pin configuration labels too
- Test search
    - define test search
    - key features
- Overview of algorithm and indexing
    - define tokens and explain how they impact ranking logic
        - Tokens/ tokenization- breaking down a query into discrete units 
        - stop words ```of, the, in``` these are just words humans use but don't mean a lot to the algo
            - keyword search - given smaller weight
            - inferred filter - can still be matched, but won't do just word
            - semantic search - still be matched, might be returned if they are semantically similar
        - custom phrases - this is set up if you know you have something that is close to something you don't want to show. for example a jeweler might want custom phrases about gold and diamonds to be unique so they don't overlap (karats)
        - Search operators
            - and, or, not, double quotes 
    - explain how the multi-algorithm approach works
        - structured data: phrase based searching
        - unstructured data: keyword search and document search 
        - entity ranking logic
        - vertical ranking logic (most helpful for user's)
    - state how the search algo ranks verticals

# Module 5
## Search Optimizations
- Search requires continuous optimization
- list types of search quality improvements you can make grouped by content issues, configuration issues, and algo issues
- Debug the backend
- describe the resources you have to debug the backend and what types of information you can get from each resource
    - test serach
    - serch log details
    - seach query API responses
    - experience training table     
- navigate the platform to access these resources
- Experience training
    - defined what experience training is
    - explain how you can use experience training for three features: featured snippets, inferred filters, and spell checking
- Search merchandiser
    - define
        - reorder entities
        - reorder verticals
        - change featured snippets
    - demonstrate
    - explain
    - Query Rules for Reorder Entities and Verticals
        - name
        - criteria 
        - action
            - boost entities, bury entities, boost verticals, bury verticals
        - can only have one query rule in the search merchandiser
- Search terms and clusters
    - define search teams and search term clusters
        - search terms table gives you an overview of what users are searching for
        - empty search term means a search query was ran with no search term
        - search term clusters automatically group together search terms with similar meaning (i.e. how many ways to people look for a gift card balance)
        - uses BERT (bidirectional encoder representations from transformers - complicated, look at the wiki if you want), then determines "closeness", then labels
        - clustering runs on a weekly basis, using 120 days of previous search data
        - cluster performance groups
            - needs attention(less than 20% click through), large(more than 1% of total searches), small
            - performing well, large, small 
    - examine search terms and clusters to inform decisions on configuring search to improve search results 
- Search analytics
    - name the three buckets of key value drivers
        - revenue generation
            - chart type
            - metrics
            - dimensions
            - filters
        - customer intelligence
        - cost savings
    - list key metrics


|     |   SEARCH  frontend |         |
|-------------- |----------------|------------------ |

# Module 1
## Intro to the search frontend theme
- List and define the two main components of the search frontend
- Explain the importance of Jambo and locate additional jambo resources
- Recall the six steps of the jambo build process
- this isn't important, but i think jambo is a stupid name.
