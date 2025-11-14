# GET /media references

Use the `GET` method to read one or more `/media` resources.

## GET /media

Retrieve all media entries.

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | A list of media entries | Media[] |
| 500 | Server error | ApiError |

### Example command

```bash
curl -X GET http://{base_url}/media
```

## GET /media/{id}

Retrieve a single media entry by ID.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| id (required) | The media ID | integer |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Media successfully retrieved| Media
| 404 | Media not found | ApiError |

### Example command

```bash
curl -X GET http://{base_url}/media/1
```

## GET /media?vampireId={id}

Retrieve all media appearances associated with a particular vampire.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| `vampireId` _(required)_ | Returns only media items linked to the specified vampire | integer |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | A filtered list of media entries | Media[] |
| 400 | Invalid query parameter | ApiError |

### Example command

```bash
curl -X GET "http://{base_url}/media?vampireId=3"
```