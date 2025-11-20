# Tutorials Overview

The Vampy API tutorials provide step-by-step, hands-on instructions for working with the API. Each tutorial focuses on specific operations and workflows to help you build practical skills.

## Getting started

If you're new to the Vampy API, we recommend starting with one of the following tutorials:

1. **[Creating a Complete Vampire Profile](adding-vampire-tutorial.md)** - Learn how to create a new vampire profile and link it to media and special powers using the `POST` method.

2. **[Filtering Vampires by Trait](filtering-vampires-trait.md)** - Learn how to use query parameters to filter vampire profiles based on specific traits.

## Available tutorials

### Creating and reading resources

| Tutorial | Description | Operations covered |
|----------|-------------|-------------------|
| [Creating a Complete Vampire Profile](adding-vampire-tutorial.md) | Create a new vampire profile with associated media and special powers | `POST` for `/vampires`, `/media`, and `/specialPowers` |
| [Filtering Vampires by Trait](filtering-vampires-trait.md) | Filter vampire profiles using query parameters | `GET` with query parameters for `/vampires` |

### Updating resources

| Tutorial | Description | Operations covered |
|----------|-------------|-------------------|
| [Updating Vampire Information](updating-vampire-information.md) | Update vampire profiles using `PATCH` and `PUT` methods | `PATCH` and `PUT` for `/vampires` |
| [Managing Media Appearances](managing-media-appearances.md) | Retrieve, create, and update media appearances | `GET`, `POST`, and `PATCH` for `/media` |
| [Working with Special Powers](working-with-special-powers.md) | Retrieve, create, and update special powers | `GET`, `POST`, and `PATCH` for `/specialPowers` |

### Deleting resources

| Tutorial | Description | Operations covered |
|----------|-------------|-------------------|
| [Removing Resources](removing-resources.md) | Delete vampires, media, and special powers | `DELETE` for all resources |


## Prerequisites

All tutorials assume that you have:

* The `json-server` app running with the `vampy_db.json` database. For setup instructions, see [Getting started with the Vampy API](../quickstart/getting-started.md).
* Basic familiarity with REST APIs and HTTP methods
* Access to a terminal and `curl` command-line tool

## Need help?

If you encounter issues while following a tutorial:

* Review the [Reference documentation](../reference/operations.md) for detailed API specifications
* Check the [Swagger documentation](../reference/vampy-api.md) for interactive API exploration
* Ensure your `json-server` is running and accessible at `http://localhost:3000`
