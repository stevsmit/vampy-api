# The Vampire Tracker API: Immortal Data Tracked Instantly

The Vampire Tracker API (Vampy API) provides a structured, searchable, 
and canonical data source for the notable vampires across film, television, literature, and lore. 
Built using json-server for deployment simplicity and accessibility, the Vampy API allows developers to 
access detailed information about individual vampires, 
their special abilities, and their media appearances.

## Vampy API benefits

The Vampy API provide a reliable endpoint to query the
characteristics and cinematic history of legendary vampires. The Vampy API provides the following benefits:

* The Vampy API data model ensures that your application's facts about vampires are consistent and accurate.

* The Vampy API leverages a standard REST architecture 
and clear JSON response, allowing you to quickly recite popular vampires in minutes.

* The relationship structure allows for expansion, letting you link powers, media, and other attributes to create an accurate vampire profile.

## Vampy topics

This website is organized into three primary sections that support developers during all stages of integration.

| Section | Purpose | Topics covered |
|---------|------|-------------|
|Quick start  | Used to get up and running in under five minutes.  | Installation, First API call using GET.  |
|Reference  | Provides comprehensive detail on all resources and operations  | Resources schema, endpoints, methods, filtering, and sorting.  |
|Tutorials  | Provides step-by-step instructions for common tasks related to the Vampy API | Add new vampire profiles, filtering vampires by power. |
|  |  |  |

## Resource references

The Vampy API exposes three primary, interconnected resources. The core of the database is the `vampires` resources. The `vampires` resource links to the `media` and `specialPowers` resource via the `vampireId` key.

### About the `/vampires` resource

| Property | Type | Description | Example |
|----------|------|-------------|---------|
|`id` |`integer` |Unique identifier for the vampire | `1`
|`name` |`string` |The common name or title of the vampire. | "Selene"
|`canFly` |`boolean` |Indicates whether the vampire is capable of flight in their base form. | `true`
|`batMode` |`boolean` |Indicates whether the vampire can transform into a bat. | `false`
|  |  |  | |

### About the `/media` resource

| Property | Type | Description | Example |
|----------|------|-------------|---------|
|`id` |`integer` |Unique identifier for this entry. | `1` 
|`type` |`string` |The medium where the vampire appears (for example, movie, television, book, etc.) | `movie`
|`title` |`string` |The title of the work | "Underworld"
|`vampireId` |`integer` |Links to the specific vampire in the `vampires` resource. | `1`
|`year` |`integer` |The year of the media's release or publication. | `2003`
|  |  |  |

### The `/specialPowers` resource

| Property | Type | Description | Example |
|----------|------|-------------|---------|
|`id` |`integer` |Unique identifier for the power entry. |`1` 
|`power` |`string` |The name or description of the specific power. |"Day walking"
|`vampireId` |`integer` |Links to the specific vampire in the `/vampires` resource. |`7`
|  |  |  |

## Ready to sink your teeth in?

Start by reading the Quick Start guide to make your first API call. Then, explore the Reference guide for advanced querying.
