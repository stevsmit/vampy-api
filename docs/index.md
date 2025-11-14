# The Vampire Tracker API: Immortal Data Tracked Instantly

The Vampire Tracker API (Vampy API) provides a structured, searchable,
and canonical data source for the notable vampires across film, television, literature, and lore.
Built using json-server for deployment simplicity and accessibility, the Vampy API allows developers to
access detailed information about individual vampires,
their special abilities, and their media appearances.

## Vampy API benefits

The Vampy API provides a reliable endpoint to query the
characteristics and cinematic history of legendary vampires. The Vampy API provides the following benefits:

* The Vampy API data model ensures that your application's facts about vampires are consistent and accurate.

* The Vampy API leverages a standard REST architecture
and clear JSON response, allowing you to quickly recite popular vampires in minutes.

* The relationship structure allows for expansion, letting you link powers, media, and other attributes to create an accurate vampire profile.

## Vampy topics

This website is organized into three primary sections that support developers during all stages of integration.

| Section | Purpose | Topics covered |
|---------|------|-------------|
|Getting started  | Used to get up and running in under five minutes.  | Installation, First API call using GET.  |
|Reference  | Provides comprehensive detail on all resources and operations  | Resources schema, endpoints, methods, filtering, and sorting.  |
|Tutorials  | Provides step-by-step instructions for common tasks related to the Vampy API | Add new vampire profiles, filtering vampires by power. |

## Resource references

The Vampy API exposes three primary, interconnected resources. The core of the database is the `vampires` resources. The `vampires` resource links to the `media` and `specialPowers` resource via the `vampireId` key.

## Ready to sink your teeth in?

Start by reading the **Quick Start** guide to make your first API call. Then, explore the **Reference guide** for advanced querying.
