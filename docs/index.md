# The Vampire Tracker API: Immortal Data Tracked Instantly

The Vampire Tracker API (Vampy API) is a small, focused REST API for exploring notable vampires across film, television, literature, and lore. It provides a structured, searchable, and canonical data source that you can plug into demos, prototypes, workshops, and teaching materials.

Built on `json-server` for simplicity and easy local setup, the Vampy API lets you query detailed information about individual vampires, their special powers, and the media where they appear.

## Why use the Vampy API?

The Vampy API gives you:

- **Consistent data model** – A single source of truth for vampire facts, so your examples and demos stay accurate.
- **Familiar REST interface** – Standard HTTP verbs and JSON responses make it easy to integrate with any HTTP client.
- **Rich relationships** – Linked resources for vampires, media, and special powers so you can build realistic scenarios and queries.

## How this documentation is organized

Use these sections depending on where you are in your journey:

| Section | Best for | What you’ll find |
|--------|----------|------------------|
| [**Getting started**](quickstart/getting-started.md) | First-time setup and your first request | How to run the API locally and make an initial `GET /vampires` call. |
| [**Tutorials**](tutorials/tutorials-overview.md)| Guided, task-based learning | Step‑by‑step flows like adding vampires, filtering by powers, and managing media. |
| [**Reference**](reference/operations.md) | Looking up fields, endpoints, and behaviors | Resource schemas, endpoints, query parameters, filtering, sorting, and examples. |

## The Vampy data model at a glance

The Vampy API exposes three primary, interconnected resources. Together they form a small graph you can query in many ways:

- **`/vampires`** – Core vampire profiles, including name, traits, and identifiers used to join to other resources.
- **`/media`** – Film, TV, books, and other appearances, each linked to a specific vampire via `vampireId`.
- **`/specialPowers`** – Unique or notable abilities, also linked to vampires via `vampireId`.

By combining these resources, you can answer questions like:

- “Which powers does this vampire have?”
- “In which movies has this vampire appeared?”
- “Which vampires share a specific ability?”

## Get started in a few minutes

1. **Spin up the API** by following the [Getting started guide](quickstart/getting-started.md).
2. **Make your first request** using your favorite HTTP client (for example, `GET /vampires`).
3. **Explore deeper**:
   - Browse the [Vampy API reference](reference/vampy-api.md) for endpoints and query options.
   - Work through the [tutorials](tutorials/tutorials-overview.md) to add, filter, and update vampires.

## Ready to sink your teeth in?

Head to [Getting started](quickstart/getting-started.md) to launch the API and make your first call, then keep the [reference](reference/vampy-api.md) and [tutorials](tutorials/tutorials-overview.md) handy as you build.
