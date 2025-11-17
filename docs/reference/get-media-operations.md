# GET /media references

Use the `GET` method to read one or more `/media` resources.

## GET /media {get-media}

Retrieve all media entries.

### Responses {get-media-responses}

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | A list of media entries | Media[] |
| 500 | Server error | ApiError |

### Example command {get-media-example-command}

```bash
curl -X GET http://{base_url}/media
```

## GET /media/{id} {get-mediaid}

Retrieve a single media entry by ID.

### Parameters {get-mediaid-parameters}

| Parameter | Description | Type |
|---------|------|---------------|
| id (required) | The media ID | integer |

### Responses {get-mediaid-parameters-responses}

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Media successfully retrieved| Media |
| 404 | Media not found | ApiError |

### Example command {get-mediaid-parameters-example-command}

```bash
curl -X GET http://{base_url}/media/1
```

## GET /media?vampireId={id} {get-media-vampireid}

Retrieve all media appearances associated with a particular vampire.

### Parameters {get-media-vampireid-parameters}

| Parameter | Description | Type |
|---------|------|---------------|
| `vampireId` _(required)_ | Returns only media items linked to the specified vampire | integer |

### Responses {get-media-vampireid-responses}

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | A filtered list of media entries | Media[] |
| 400 | Invalid query parameter | ApiError |

### Example command {get-media-vampireid-example-command}

```bash
curl -X GET "http://{base_url}/media?vampireId=3"
```
