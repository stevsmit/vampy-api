# About the /media resource

The /media resource represents a media appearance associated with a vampire in the Vampy API.
Each entry includes the title of the media, its release year, and a foreign key (`vampireId`)
linking the appearance to a specific vampire.
You can create, read, update, or delete media entries using the corresponding API endpoints.

## Properties

| Property | Type | Description | Example |
|----------|------|-------------|---------|
|`id` |`integer` |Unique identifier for this entry. | `1` |
|`type` |`string` |The medium where the vampire appears (for example, movie, television, book, etc.) | `movie` |
|`title` |`string` |The title of the work | "Underworld" |
|`vampireId` |`integer` |Links to the specific vampire in the `vampires` resource. | `1` |
|`year` |`integer` |The year of the media's release or publication. | `2003` |

## Related endpoints

| Path | Description |
|----------|---------|
|`GET /media` | Retrieve a list of all media entries. |
|`GET /media/{id}` | Retrieve a single media entry by its `id`. |
|`GET /media?vampireId={id}` | Retrieve all media entries linked to a specific vampire. |
|`POST /media` | Retrieve a vampire profile along with its assigned special powers. |
|`PATCH /media/{id}` | Update one or more fields of an existing media entry. |
|`PUT /media/{id}` | Replace an existing media entry with a new object (all fields required). |
| `DELETE /media/{id}` | Delete a media entry. |
