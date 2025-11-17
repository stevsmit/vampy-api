# API reference: REST operations

The Vampy API supports standard RESTful operations (Create, Read, Update, Delete)
on all three primary resources: /vampires, /media, and /specialPowers.
All requests and responses are handled via JSON.

This reference provides a high-level overview of each operation, with examples for common use cases.

## Read operations (GET)

Use GET to retrieve Vampy API resources. You can fetch all resources, a single resource by ID, or filter resources based on certain fields. You can also expand related resources using _embed.

| Operation | Endpoint example | Description |
|---------|------|---------------|
| Get all vampires | `GET /vampires` | Retrieve a list of all vampire profiles. |
| Get vampire by ID | `GET /vampires/7` | Retrieve the profile for the vampire with id=7 (Blade). |
| Filter vampires | `GET /vampires?canFly=true` | Retrieve all vampires capable of flight. |
| Vampire with embedded media | `GET /vampires/1?_embed=media` | Retrieve a vampire profile with all associated media entries. |
| Vampire with embedded powers| `GET /vampires/1?_embed=specialPowers` | Retrieve a vampire profile with all assigned special powers. |
| Get all media | `GET /media` | Retrieve a list of all media entries. |
| Media by ID | `GET /media/3` | Retrieve a single media entry. |
| Media for a vampire | `GET /media?vampireId=1` | Retrieve all media linked to a specific vampire. |
| Get all special powers | `GET /specialPowers` | Retrieve a list of all powers. |
| Special power by ID | `GET /specialPowers/1` | Retrieve a single special power entry. |
| Powers for a vampire| `GET /specialPowers?vampireId=7` | Retrieve all powers associated with a specific vampire. |

### Example request (GET /vampires)

```bash
curl -X GET -H "Content-Type: application/json" http://localhost:3000/vampires
```

## Create operations (POST)

Use POST to create new resources. The API automatically assigns a unique id to the new entry.

| Endpoint | Description | Required fields |
|---------|------|---------------|
| `POST /vampires` | Adds a new vampire profile. | `name`, `canFly`, `batMode` |
| `POST /media` | Records a new media appearance. | `type`, `title`, `year`, `vampireId` |
| `POST /specialPowers` | Assigns a new power to a vampire. | `power`, `vampireId` |

### Example request (POST /vampires)

```bash
curl -X POST -H "Content-Type: application/json" \
  -d '{"name": "Count Orlok", "canFly": false, "batMode": false}' \
  http://localhost:3000/vampires
```

## Update operations (PATCH / PUT)

Use PATCH to update part of a resource, or PUT to replace the resource entirely.

| Endpoint | Operation | Description | Example field updates |
|----------|-----------|-------------|-----------------------|
/vampires/{id} | PATCH | Update one or more fields on a vampire. | {"batMode": true} |
/vampires/{id} | PUT |Replace a vampire object completely. |{"name":"Dracula","canFly":true,"batMode":true} |
/media/{id} | PATCH | Update media fields. | {"title":"Blade II"} |
/media/{id} |PUT |Replace media object entirely.| {"type":"movie","title":"Blade II","year":2002,"vampireId":7} |
/specialPowers/{id} |PATCH |Update one or more fields of a power. |{"power":"Mind Control"} |
/specialPowers/{id} |PUT | Replace a power object completely. {"power":"Invisibility","vampireId":4} |

### Example request (PATCH /vampires/7)

```bash
curl -X PATCH -H "Content-Type: application/json" \
  -d '{"batMode": true}' \
  http://localhost:3000/vampires/7
```

### Example request (PUT /media/3)

```bash
curl -X PUT -H "Content-Type: application/json" \
  -d '{"type":"movie","title":"Blade II","year":2002,"vampireId":7}' \
  http://localhost:3000/media/3
```

## Delete operations (DELETE)

Use DELETE to remove a resource by ID.

| Endpoint | Description |
|----------|-----------|
|/vampires/{id} | Delete a vampire profile. |
|/media/{id} |Delete a media entry. |
|/specialPowers/{id} | Delete a special power entry. |

## Example request (DELETE /media/3)

```bash
curl -X DELETE http://localhost:3000/media/3
```

## Next steps

After reviewing operations, you can explore the detailed reference pages for each resource. Each page includes full property definitions, examples, and endpoint references.

* [About the /vampires resource](about-vampires.md)

* [About the /media resource](about-media.md)

* [About the /specialPowers resource](about-specialpowers.md)
