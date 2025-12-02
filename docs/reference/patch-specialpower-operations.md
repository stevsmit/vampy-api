# PATCH /specialPowers references

Use the `PATCH` method to update one or more fields of an existing special power.

## PATCH /specialPowers/{id}

Update a special power entry by ID.
Only the fields you include in the request body will be updated.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| id _(required)_ | Unique ID of the special power.| integer |
| power _(optional)_ | The name of the special power. | string |
| vampireId _(optional)_ | The ID of the vampire who has this power. | integer |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Successful update | SpecialPower object |
| 400 | Bad request | ApiError |
| 404 | Special power not found | ApiError |

### Example command

```bash
curl -X PATCH \
  -H "Content-Type: application/json" \
  -d '{"power": "Shadowmeld"}' \
  http://{base_url}/specialPowers/3
```
