# GET /vampires references

Use the `GET` method to retrieve information about the `/vampires` resource.

## **GET /vampires** {get-vampire}

Retrieve a list of all vampire profiles.

### Parameters {get-vampire-parameters}

| Parameter | Description | Type |
|---------|------|---------------|
| None | Retrieve all vampires| - |

### Responses {get-vampire-responses}

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | List of all vampire profiles | `array` of Vampires |

### Example command {get-vampire-example-command}

```bash
curl -X GET -H "Content-Type: application/json" http://{base_url}/vampires
```

## **GET /vampires/{id}** {get-vampireid}

Retrieve a single vampire profile by its unique id.

### Parameters {get-vampireid-parameters}

| Parameter | Description | Type |
|---------|------|---------------|
|id | Unique ID of the vampire | integer |

### Responses {get-vampireid-responses}

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Vampire profile | Vampire object |
| 404 | Vampire not found | ApiError |

### Example command {get-vampireid-example-command}

```bash
curl -X GET -H "Content-Type: application/json" http://{base_url}/vampires/1
```

## **GET /vampires?canFly={true/false}** {get-vampire-canfly}

Retrieve all vampires that are, or are not, capable of flight.

### Parameters {get-vampire-canfly-parameters}

| Parameter | Description | Type |
|---------|------|---------------|
| canFly | Filter vampires by flight capability | boolean |

### Responses {get-vampire-canfly-responses}

| HTTP Code | Description | Schema |
|---------|------|---------------|
|200 | List of vampires that can fly | array of Vampire objects |

### Example command {get-vampire-canfly-example-command}

```bash
curl -X GET -H "Content-Type: application/json" http://{base_url}/vampires?canFly=true
```

## **GET /vampires/{id}?_embed=specialPowers** {get-vampire-specialpowers}

Retrieve a single vampire profile with its special powers.

### Parameters {get-vampire-specialpowers-parameters}

| Parameter | Description | Type |
|---------|------|---------------|
| `id` | Unique ID of the vampire | integer |

### Responses {get-vampire-specialpowers-responses}

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Vampire profile with embedded special powers |Vampire object with `specialPowers` array |
| 404 | Vampire not found | ApiError |

### Example command {get-vampire-specialpowers-example-command}

```bash
curl -X GET -H "Content-Type: application/json" http://{base_url}/vampires/1?_embed=specialPowers
```

## GET /vampires/{id}?_embed=media {get-vampire-media}

Retrieve a single vampire profile and embed all associated media appearances in the response.

### Parameters {get-vampire-media-parameters}

| Parameter | Description | Type |
|---------|------|---------------|
| `id` _(required)_ | Unique ID of the vampire | integer |

### Responses {get-vampire-media-responses}

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Vampire profile with embedded media |Vampire object with `media` array |
| 404 | Vampire not found | ApiError |

### Example command {get-vampire-media-example-command}

```bash
curl -X GET \
  -H "Content-Type: application/json" \
  "http://{base_url}/vampires/1?_embed=media"
```