# GET /specialPowers references

Use the GET method to retrieve one or more /specialPowers resources.

## GET /specialPowers

Retrieve a list of all special powers.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| `vampireId` _(optional)_ | Filter powers belonging to a specific vampire | integer |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Successful retrieval | Array of SpecialPower objects |

### Example command (GET all)

```bash
curl -X GET \
  -H "Content-Type: application/json" \
  http://{base_url}/specialPowers
```

## GET /specialPowers/{id}

Retrieve a single special power by its id.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| `id` | Unique identifier for the special power entry. | integer |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Special power found | SpecialPower object |
| 404 | Special power not found | ApiError |

### Example command

```bash
curl -X GET \
  -H "Content-Type: application/json" \
  http://{base_url}/specialPowers/1
```

## GET /specialPowers?vampireId={id}

Retrieve all powers assigned to a specific vampire.

Example command (filter by vampire)
curl -X GET \
  -H "Content-Type: application/json" \
  "http://{base_url}/specialPowers?vampireId=1"
