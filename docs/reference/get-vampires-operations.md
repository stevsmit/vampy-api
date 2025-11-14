# GET /vampires references

Use the `GET` method to retrieve information about the `/vampire` resource.

## **GET /vampires**

Retrieve a list of all vampire profiles.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| None | Retrieve all vampires| - |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | List of all vampire profiles | `array` of Vampires |

### Example command

```bash
curl -X GET -H "Content-Type: application/json" http://{base_url}/vampires
```

## **GET /vampires/{id}**

Retrieve a single vampire profile by its unique id.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
|id | Unique ID of the vampire | integer |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Vampire profile | Vampire object |
| 404 | Vampire not found | ApiError |

### Example command

```bash
curl -X GET -H "Content-Type: application/json" http://{base_url}/vampires/1
```

## **GET /vampires?canFly={true/false}**

Retrieve all vampires that are, or are not, capable of flight.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| canFly | Filter vampires by flight capability | boolean |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
|200 | List of vampires that can fly | array of Vampire objects |

### Example command

```bash
curl -X GET -H "Content-Type: application/json" http://{base_url}/vampires?canFly=true
```

## **GET /vampires/{id}?_embed=specialPowers**

Retrieve a single vampire profile with its special powers.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| `id` | Unique ID of the vampire | integer |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Vampire profile with embedded special powers |Vampire object with `specialPowers` array |
| 404 | Vampire not found | ApiError |

### Example command

```bash
curl -X GET -H "Content-Type: application/json" http://{base_url}/vampires/1?_embed=specialPowers
```

## GET /vampires/{id}?_embed=media

Retrieve a single vampire profile and embed all associated media appearances in the response.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| `id` _(required)_ | Unique ID of the vampire | integer |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Vampire profile with embedded special powers |Vampire object with `specialPowers` array |
| 404 | Vampire not found | ApiError |

### Example command

```bash
curl -X GET \
  -H "Content-Type: application/json" \
  "http://{base_url}/vampires/1?_embed=media"
```