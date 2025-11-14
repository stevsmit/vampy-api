# About the `/vampires` resource

The following endpoints allow you to retrieve vampire data in different ways using the `GET` method.

## Properties

| Property | Type | Description | Example |
|----------|------|-------------|---------|
|`id` |`integer` |Unique identifier for the vampire | `1` |
|`name` |`string` |The common name or title of the vampire. | "Selene" |
|`canFly` |`boolean` |Indicates whether the vampire is capable of flight in their base form. | `true` |
|`batMode` |`boolean` |Indicates whether the vampire can transform into a bat. | `false` |

## Related endpoints

| Path | Description |
|----------|---------|
|`GET /vampires` |Retrieve a list of all vampire profiles. |
|`GET /vampires/{id}` |Retrieve a single vampire profile by its `id`. |
|`GET /vampires?canFly={true/false}` |Retrieve all vampires that can or cannot fly. |
|`GET /vampires/{id}?_embed=specialPowers` |Retrieve a vampire profile along with its special powers. |
|`POST /vampires` |Create a new vampire profile. Requires `name`, `canFly`, and `batMode`. |
|`PATCH /vampires/{id}` |Update one or more fields on an existing vampire. |
|`PUT /vampires/{id}` |Replace an existing vampire with a new object (all fields required). |
|`DELETE /vampires/{id}` |Delete a vampire profile. |

## **Example requests**

* Get all vampires

    ```bash
    curl -X GET \
    -H "Content-Type: application/json" \
    http://localhost:3000/vampires
    ```

    Response

    ```json
    [
    {
        "id": 1,
        "name": "Selene",
        "canFly": false,
        "batMode": false
    },
    {
        "id": 2,
        "name": "Peter Loew",
        "canFly": false,
        "batMode": false
    }
    ]
    ```

* Get a vampire with embedded special powers

    ```bash
    curl -X GET \
    -H "Content-Type: application/json" \
    "http://localhost:3000/vampires/1?_embed=specialPowers"
    ```

    Response

    ```json
    {
    "id": 1,
    "name": "Selene",
    "canFly": false,
    "batMode": false,
    "specialPowers": [
        {
        "id": 2,
        "power": "Enhanced Marksmanship",
        "vampireId": 1
        }
    ]
    }
    ```

* Create a new vampire

    ```bash
    curl -X POST \
    -H "Content-Type: application/json" \
    -d '{"name": "Count Orlok", "canFly": false, "batMode": false}' \
    http://localhost:3000/vampires
    ```

    Response

    ```json
    {
    "id": 8,
    "name": "Count Orlok",
    "canFly": false,
    "batMode": false
    }
    ```