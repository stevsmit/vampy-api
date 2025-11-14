# POST /media references

Use the POST method to create a new /media resource.

## POST /media

Create a new media entry associated with a vampire.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| title _(required)_ | Title of the media work | string |
| year _(required)_ | Release year | integer |
| vampireId _(required)_ | ID of the vampire featured in the media| integer |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 201 | Successful creation | Media object |
| 400 | Bad request | ApiError |

### Example command

```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"title": "Let the Right One In", "year": 2008, "vampireId": 2}' \
  http://{base_url}/media
```
