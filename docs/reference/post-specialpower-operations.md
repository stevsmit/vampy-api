# POST /specialPowers references

Use the `POST` method to create a new special power for a vampire.

## POST /specialPowers

Create a new special power entry.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| power _(required)_ | The name of the special power. | string |
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
        "power": "Shadow Walk",
        "vampireId": 1
      }' \
  http://{base_url}/specialPowers
```
