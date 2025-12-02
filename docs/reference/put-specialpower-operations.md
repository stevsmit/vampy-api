# PUT /specialPowers references

Use the PUT method to replace an existing special power with a new, complete object.

## PUT /specialPowers/{id}

Replace an entire special power entry by ID.
All fields are required — the existing object will be fully overwritten.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| id _(required)_ | Unique ID of the special power. | integer |

### Required request body fields

| Field | Description | Type |
|---------|------|---------------|
| power | The name of the special power. | string |
| vampireId | The ID of the vampire who possesses the power. | integer |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Successful replacement | SpecialPower object |
| 400 | Bad request | ApiError |
| 404 | Special power not found | ApiError |

### Example command

```bash
curl -X PUT \
  -H "Content-Type: application/json" \
  -d '{
        "power": "Shadowmeld",
        "vampireId": 1
      }' \
  http://{base_url}/specialPowers/3
```
