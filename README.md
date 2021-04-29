# Extreme Data hub

Extreme Data hub is a model for collecting, sharing and displaying data with very loose technical constraints. Data in the hub can be used for health checks, reporting, searching, exhibitions or creating other data-related services.

## sets
Use any storage system you like. Set can be a MongoDB collection for example
TASK:
provide queryable data storage for harvester and transformers

RULES:
- Set name starts with "set__"


## harvesters
Use any tools you like (python, javascript, java etc.)

TASK:
make sure that set is up to date

RULES:
- harvesters must not have dependencies to other harvesters
- items must have unique id (eg. handle)
- items must have timestamp

## queries
Use query language of your storage system (MongoDB, SQL, Cycper...)
TASK:
Provide a subset from set

## transformers
Use any tools you like (python, javascript, java etc.)
TASK:
make data usable for your purposes (can be based on queries)

RULES:
- **do not edit harvested data** (i.e. do not change values in original fields but create new fields for edited data or create entire new set)
- if transformer depends on other transformer (for example lookup for other transformet set), the execution order must be the same as the alphabetical sort order of transformer scripts (name like 1_myfirst.py, 2_mylookup.py)


## endpoints
Use any tools you like

TASK:
provide data in different formats (like csv, RSS, REST) to OTHER users

## exhibitions
Exhibitions are DISPLAYS of your data based on data providec by query or queries.
Exhibition can be a website, Omeka-S site or any other display mechanism.

TASK:
Keep exhibitions up to date.


RULES:
- items in exhibitions must store original item id so that updates can be done correctly.

## metadata (registers)
Registers are metadata about harvesters, transforers, queries and exhibitions. It is easier to manage system if settings are not hidden in individual scripts.
It might be a good idea to create collections for different parts of the flow.
- meta__sets
- meta__queries
- etc..


# Execution

In order to implement Extreme Data hub, one must first choose underlying data storage. In this example it is assumed that we want to use MongoDB.

First harvesters are run in any order. This could be done via bash script, for example:

    fetch_thesis.js
    fetch_dissertations.js
    fetch_some_other_data.py

Then we run transformers:

    extract_authors.js
    make_isbn_lookup_dissertations.py



For managing the system,
- meta__sets
- meta__queries
-
