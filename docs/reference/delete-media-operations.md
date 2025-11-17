# DELETE /media references

Use the `DELETE` method to remove a media entry.

## DELETE /media/{id} {delete-media-parameters}

Delete one media resource by ID.

### Parameters {delete-media-parameters}

| Parameter | Description | Type |
|---------|------|---------------|
| **id** (_required_) | Unique ID of the media. | integer |

### Responses {delete-media-responses}

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Delete successful | {} |
| 404 | Media not found | ApiError |

### Example command {delete-media-example-command}

```bash
curl -X DELETE http://{base_url}/media/3
```
