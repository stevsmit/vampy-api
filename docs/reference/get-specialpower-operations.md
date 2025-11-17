# GET /specialPowers references

Use the GET method to retrieve one or more /specialPowers resources.

## GET /specialPowers {get-specialpowers}

Retrieve a list of all special powers.

### Parameters {get-specialpowers-parameters}

| Parameter | Description | Type |
|---------|------|---------------|
| `vampireId` _(optional)_ | Filter powers belonging to a specific vampire | integer |

### Responses {get-specialpowers-responses}

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Successful retrieval | Array of SpecialPower objects |

### Example command {get-specialpowers-example-command}

```bash
curl -X GET \
  -H "Content-Type: application/json" \
  http://{base_url}/specialPowers
```

## GET /specialPowers/{id} {get-specialpowersid}

Retrieve a single special power by its id.

### Parameters {get-specialpowersid-parameters}

| Parameter | Description | Type |
|---------|------|---------------|
| `id` | Unique identifier for the special power entry. | integer |

### Responses {get-specialpowersid-responses}

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Special power found | SpecialPower object |
| 404 | Special power not found | ApiError |

### Example command {get-specialpowersid-example-command}

```bash
curl -X GET \
  -H "Content-Type: application/json" \
  http://{base_url}/specialPowers/1
```

## GET /specialPowers?vampireId={id} {get-specialpowersid-vampireid-parameters}

Retrieve all powers assigned to a specific vampire.

### Parameters {get-specialpowersid-vampireid-parameters}

| Parameter | Description | Type |
|---------|------|---------------|
| `id` _(required)_ | Unique identifier for the special power entry. | integer |
| `vampireId` _(optional)_ | Filter powers belonging to a specific vampire | integer |

### Responses {get-specialpowersid-vampireid-responses}

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Special power found | SpecialPower object |
| 404 | Special power not found | ApiError |

### Example command {get-specialpowersid-vampireid-example-command}

```bash
curl -X GET \
  -H "Content-Type: application/json" \
  "http://{base_url}/specialPowers?vampireId=1"
```
