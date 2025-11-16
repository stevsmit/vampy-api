# POST /specialPowers references

Use the `POST` method to create a new special power for a vampire.

## POST /specialPowers

Create a new special power entry.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| name _(required)_ | The name of the special power. | string |
| description _(required)_ | A short description of the power. | string |
| vampireId _(required)_ | The ID of the vampire who has this power. | integer |

### Responses

| HTTP Code | Description | Schema |
|---------|------|-----------------|
| 201 | Successful creation | SpecialPower object |
| 400 | Bad request | ApiError |

### Example command

```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{
        "name": "Shadow Walk",
        "description": "Allows the vampire to move unseen through darkness.",
        "vampireId": 1
      }' \
  http://{base_url}/specialPowers
```
