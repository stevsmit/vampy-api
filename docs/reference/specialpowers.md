# About the `/specialPowers` resource

The `/specialPowers` resource represents a unique ability or power possessed by a vampire in the Vampy API.
Each entry includes the name of the power and a foreign key (`vampireId`) linking it to a specific vampire.
You can create, read, update, or delete special powers using the corresponding API endpoints.

## Properties

| Property | Type | Description | Example |
|----------|------|-------------|---------|
|`id` |`integer` |Unique identifier for the power entry. |`1` |
|`power` |`string` |The name or description of the specific power. |"Day walking" |
|`vampireId` |`integer` |Links to the specific vampire in the `/vampires` resource. |`7` |

## Related endpoints

| Path | Description
| `GET /specialPowers` | Retrieve a list of all special powers. |
| `GET /specialPowers/{id}` | Retrieve a single special power by its id. |
| `GET /specialPowers?vampireId={id}` | Retrieve all special powers associated with a specific vampire. |
| `POST /specialPowers` | Create a new special power. Requires power and vampireId. |
| `PATCH /specialPowers/{id}` | Update one or more fields of an existing special power. |
| `PUT /specialPowers/{id}` | Replace an existing special power with a new object (all fields required). |
| `DELETE /specialPowers/{id}` | Delete a special power entry. |
