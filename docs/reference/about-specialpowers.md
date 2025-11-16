# About the /specialPowers resource

The `/specialPowers` resource represents individual supernatural abilities associated with vampires in the Vampy API.
Each entry includes the name of the power and a foreign key (`vampireId`) linking the ability to a specific vampire.
You can create, read, update, or delete special power entries using the corresponding API endpoints.

## Properties

| Property | Type | Description | Example |
|----------|------|-------------|---------|
| `id` | integer | Unique identifier for the special power entry. | `1` |
| `power`| string | Name of the special ability.| "Day-walking" |
| `vampireId` | integer | Links to the specific vampire in the vampires resource. | `7` |

## Related endpoints

| Path | Description |
|----------|---------|
| `GET /specialPowers` | Retrieve a list of all special powers. |
| `GET /specialPowers/{id}`| Retrieve a single special power entry by its id. |
| `GET /specialPowers?vampireId={id}` | Retrieve all powers linked to a specific vampire. |
| `POST /specialPowers` | Create a new special power entry. |
| `PATCH /specialPowers/{id}` | Update one or more fields of a special power entry. |
| `PUT /specialPowers/{id}` | Replace an existing special power entry with a new object (all fields required). |
| `DELETE /specialPowers/{id}` | Delete a special power entry. |
