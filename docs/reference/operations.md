# API reference: REST operations

The Vampy API supports standard RESTful operations (Create, Read, Update, Delete)
on all three primary resources: `/vampires`, `/media`, and `/specialPowers`.
All requests and responses are handled via JSON.

The following sections provide an overview of each operation.

## Read operations (GET)

Use `GET` to retrieve Vampy API resources.

| Operation | Endpoint example | Description |
|---------|------|-------------|
|Get all  | `GET /vampires`  | Retrieve a list of all vampire profiles.  |
|Get by ID  | `GET /vampires/7`  |Retrieve the profile for the vampire with the `7` `id` (Blade).  |
|Filter  | `GET /vampires?canFly=true` | Retrieve all vampires that can fly. |
|Relational data  | `GET /specialPowers?_expand=vampire` | Retrieve all special powers, embedding the associated vampire object with the response for each power. |

**Example request (`GET /vampires`):**

```bash
curl -X GET \
  -H "Content-Type: application/json" \
  http://localhost:3000/vampires
```

**Example response (`GET /vampires`):**

```json
[
  {
    "id": 1,
    "name": "Selene",
    "canFly": false,
    "batMode": false
  },
  {
    "id": 7,
    "name": "Blade",
    "canFly": false,
    "batMode": false
  }
  // ... more vampires
]
```

## Create operations (POST)

Use `POST` to create new resources. The API automatically assigns a unique `id` to the new entry upon success.

| Endpoint | Description | Required fields |
|---------|------|-------------|
|`POST /vampires`  | Adds a new vampire profile.  | `name`, `canFly` (boolean), `batMode` (boolean) |
|`POST /media`  | Records a new media appearance for an existing vampire. | `type`, `title`, `year`, `vampireiD` (integer) |
|`POST /specialPowers`  | Assigns a new power to an existing vampire. | `power`, `vampireId` (integer) |

**Example request (`POST /vampires`):**

```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"name": "Count Orlok", "canFly": false, "batMode": false}' \
  http://localhost:3000/vampires
```

**Example response if successful:**

```json
{
  "name": "Count Orlok",
  "canFly": false,
  "batMode": false,
  "id": 8
}
```

## Update operations (PUT/PATCH)

Use `PATCH` to update one or more fields of an existing resource without altering other fields.

**Example request (`PATCH /vampires/`):**

```bash
curl -X PATCH \
  -H "Content-Type: application/json" \
  -d '{"canFly": true}' \
  http://localhost:3000/vampires/1
```

**Example response if successful:**

```json
{
  "id": 1,
  "name": "Selene",
  "canFly": true,
  "batMode": false
}
```

Use `PUT` to completely replace an existing resource with a new object. You must include all fields of the payload. Missing fields are set to `null` or default values.

```bash
curl -X PUT \
  -H "Content-Type: application/json" \
  -d '{"name": "Selene", "canFly": false, "batMode": false, "id": 1}' \
  http://localhost:3000/vampires/1
```

**Example response if successful:**

```json
{
  "name": "Selene",
  "canFly": false,
  "batMode": false,
  "id": 1
}
```

## Delete operations (DELETE)

Use `DELETE` to remove a resource from the database by using its `id`.

**Example Request (DELETE /media/3):**

```bash
curl -X DELETE http://localhost:3000/media/3
```

**Example response if successful:**

```json
{}
```

## Next steps
