# DELETE /specialPowers references

Use the DELETE method to remove a special power entry.

## DELETE /specialPowers/{id}

Delete one special power resource by ID.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| id (required) | Unique ID of the special power. | integer |

### Responses

| HTTP Code | Description | Schema |
| 200 | Delete successful | {} |
| 404 | Special power not found | ApiError |

### Example command

```bash
curl -X DELETE http://{base_url}/specialPowers/3
```
