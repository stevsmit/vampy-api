# DELETE /media references

Use the `DELETE` method to remove a media entry.

## DELETE /media/{id}

Delete one media resource by ID.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| **id** (_required_) | Unique ID of the media. | integer |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Delete successful | {} |
| 404 | Media not found | ApiError |

### Example command

```bash
curl -X DELETE http://{base_url}/media/3
```
