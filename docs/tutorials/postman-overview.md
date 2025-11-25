# Postman Tutorials Overview

The Vampy API Postman tutorials walk through three common CRUD workflows: creating a new vampire, filtering existing vampires by trait, and updating or deleting a record. Each tutorial highlights the tabs and scripts you need inside Postman to replicate the CLI-based procedures.

## Prerequisites

Before starting, make sure you have:

* Postman Desktop or Web app installed
* The Vampy API Postman environment imported from the `postman` folder (see [Getting started with the Vampy API](../quickstart/getting-started.md))
* The `json-server` app running with the `vampy_db.json` database

## Available tutorials

| Tutorial | Description | Operations covered |
|----------|-------------|-------------------|
| [Creating a Vampire Profile in Postman](creating-vampire-postman.md) | Build and send a basic `POST /vampires` request and store the returned `id` | `POST` for `/vampires` |
| [Retrieving Vampires by Trait in Postman](retrieving-vampires-trait-postman.md) | Filter vampires with query parameters (for example, `canFly=true`) | `GET` with query parameters for `/vampires` |
| [Updating or Removing Vampires in Postman](updating-removing-vampires-postman.md) | Apply `PATCH`/`PUT` updates and delete records safely | `PATCH`, `PUT`, `DELETE` for `/vampires` |

## Need help?

If you get stuck while using Postman:

* Confirm the correct environment is selected and `baseUrl` points to `http://localhost:3000`
* Review the [Reference documentation](../reference/operations.md) for payload details
* Check [Swagger documentation](../reference/vampy-api.md) to compare request/response schemas
* Reset collection variables or re-import the environment if IDs get out of sync
