## POST /vampires

Create a new vampire profile.

| Field | Description | Type |
|---------|------|---------------|
| **name** (_required_) | Friendly name of the vampire | string |
| **canFly** (_required_) | Whether the vampire can fly | boolean |
| **batMode** (_required_) | Whether the vampire can transform into a bat |boolean |

## Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 201 | Successful creation | Vampire object |
| 400 | Bad request | ApiError |

## Example command

```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"name": "Count Orlok", "canFly": false, "batMode": false}' \
  http://{base_url}/vampires
```