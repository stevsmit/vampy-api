# PATCH /media references

Use the PATCH method to update one or more fields of an existing media entry.

## PATCH /media/{id}

Update partial fields on an existing media object.

### Parameters

At least one field must be provided.

| Parameter | Description | Type |
|---------|------|---------------|
| id _(required)_ | The media ID | integer |
| title _(optional)_ | New title of the media| string |
| year _(optional)_| Updated release year | integer |
| vampireId _(optional)_ | Associated vampire ID | integer |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Update successful | Media |
| 400 | Invalid update payload | ApiError |
| 404 | Media not found | ApiError |

### Example command

```bash
curl -X PATCH \
  -H "Content-Type: application/json" \
  -d '{"year": 2010}' \
  http://{base_url}/media/1
```
