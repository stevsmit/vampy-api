# PUT /media references

Use the `PUT` method to replace an existing `/media` resource with a new object.

## PUT /media/{id}

Replace an entire media entry.
All fields are required.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| id _(required)_ | The media ID | integer |
| title _(required)_ | New title of the media| string |
| year _(required)_ | Updated release year | integer |
| vampireId _(required)_ | Associated vampire ID | integer |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Replacement creation | Media |
| 400 | Missing or invalid fields | ApiError |
| 404 | Media not found | ApiError |

### Example command

```bash
curl -X PUT \
  -H "Content-Type: application/json" \
  -d '{"id": 1, "title": "Underworld (Director’s Cut)", "year": 2003, "vampireId": 1}' \
  http://{base_url}/media/1
```