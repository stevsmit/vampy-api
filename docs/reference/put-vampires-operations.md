# PUT /vampires/{id} references

Use the `PUT` method to replace an existing vampire with a new object.
All fields must be included in the request. Missing fields will be set to null or default values.

## PUT /vampires/{id}

Update the entire vampire profile.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| **id** (_required_) | Unique ID of the vampire | integer |
| **name** (_required_) | Friendly name of the vampire | string |
| **canFly** (_required_) | Whether the vampire can fly | boolean |
| **batMode** (_required_) | Whether the vampire can transform into a bat |boolean |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 201 | Successful creation | Vampire object |
| 400 | Bad request | ApiError |
| 404 | Vampire not found | ApiError |

### Example command

```bash
curl -X PUT \
  -H "Content-Type: application/json" \
  -d '{"name": "Selene", "canFly": false, "batMode": false, "id": 1}' \
  http://{base_url}/vampires/1
```
