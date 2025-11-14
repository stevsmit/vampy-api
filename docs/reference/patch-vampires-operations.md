# PATCH /vampires/{id} references

Use the `PATCH` method to update one or more fields on an existing vampire using the vampire's ID.
Only the fields included in the request will be updated. Other fields remain unchanged.

## PATCH /vampires/{id}

Update the vampire profile.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| **id** (_required_) | Unique ID of the vampire | integer |
| **name** (_optional_) | Friendly name of the vampire | string |
| **canFly** (_optional_) | Whether the vampire can fly | boolean |
| **batMode** (_optional_) | Whether the vampire can transform into a bat |boolean |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 201 | Successful creation | Vampire object |
| 400 | Bad request | ApiError |
| 404 | Vampire not found | ApiError |

### Example command

```bash
curl -X PATCH \
  -H "Content-Type: application/json" \
  -d '{"canFly": true}' \
  http://{base_url}/vampires/1
```
