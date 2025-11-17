# DELETE /specialPowers references

Use the DELETE method to remove a special power entry.

## DELETE /specialPowers/{id} {delete-specialpowers}

Delete one special power resource by ID.

### Parameters {delete-specialpowers-parameters}

| Parameter | Description | Type |
|---------|------|---------------|
| id (required) | Unique ID of the special power. | integer |

### Responses {delete-specialpowers-responses}

| HTTP Code | Description | Schema |
| 200 | Delete successful | {} |
| 404 | Special power not found | ApiError |

### Example command {delete-specialpowers-example-command}

```bash
curl -X DELETE http://{base_url}/specialPowers/3
```
