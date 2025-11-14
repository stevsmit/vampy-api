# About the `/vampires` resource

The `/vampires` resource represents a vampire profile in the Vampy API.
Each entry contains the vampire's name, abilities, and unique identifier.
This resource is central to link media appearances and special powers.
You can create, read, update, or delete vampire profiles using the corresponding API endpoints.

## Properties

| Property | Type | Description | Example |
|----------|------|-------------|---------|
|`id` |`integer` |Unique identifier for the vampire | `1` |
|`name` |`string` |The common name or title of the vampire. | "Selene" |
|`canFly` |`boolean` |Indicates whether the vampire is capable of flight in their base form. | `true` |
|`batMode` |`boolean` |Indicates whether the vampire can transform into a bat. | `false` |

## Related endpoints

| Path | Description |
|----------|---------|
|`GET /vampires` |Retrieve a list of all vampire profiles. |
|`GET /vampires/{id}` |Retrieve a single vampire profile by its `id`. |
|`GET /vampires?canFly={true/false}` |Retrieve all vampires that can or cannot fly. |
|`GET /vampires/{id}?_embed=specialPowers` |Retrieve a vampire profile along with its assigned special powers. |
|`GET /vampires/{id}?_embed=media` | Retrieve a single vampire profile and embed all associated media appearances in the response. |
|`POST /vampires` |Create a new vampire profile. Requires `name`, `canFly`, and `batMode`. |
|`PATCH /vampires/{id}` |Update one or more fields on an existing vampire. |
|`PUT /vampires/{id}` |Replace an existing vampire with a new object (all fields required). |
|`DELETE /vampires/{id}` |Delete a vampire profile. |
