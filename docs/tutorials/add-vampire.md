# Tutorial: Creating a complete vampire profile

This tutorial shows you how to use the `POST` method to create 
a new vampire entity to the database.

## Description and goal 

The following procedure shows you how to add the profile for Edward Cullen and assign him the power of *Enhanced Speed*.

## Prerequisites

* Confirm that the `json-server` app is running with the `vampy_db.json` database.

## Procedure

1. Open a terminal.

2. Run the following `cURL` command using the `POST` method.
This command creates the core entry to the `/vampires` resource.

    ```bash
    curl -X POST \
    -H "Content-Type: application/json" \
    -d '{
        "name": "Edward Cullen", 
        "canFly": false, 
        "batMode": false
    }' \
    http://localhost:3000/vampires
    ```

    The API returns the new vampire object, which includes a unique `id` assigned by the server. For example:

    ```json
    {
    "name": "Edward Cullen",
    "canFly": false,
    "batMode": false,
    "id": 8
    }
    ```

3. Run the following `cURL` command using the `POST` method to add 
the power *Enhanced Speed* to the `/specialPowers`. Include the `vampireId` generated from Step 2.

    ```bash
    curl -X POST \
    -H "Content-Type: application/json" \
    -d '{
        "power": "Enhanced Speed", 
        "vampireId": 8
    }' \
    http://localhost:3000/specialPowers
    ```

    The API returns the new power object with its own unique `id`. For example:

    ```json
    {
    "power": "Enhanced Speed",
    "vampireId": 9,
    "id": 8
    }
    ```

## Completion and validation

1. Run the following `cURL` command using the `GET` method to confirm the changes:

    ```bash
    curl -X GET \
    http://localhost:3000/vampires/8?_embed=specialPowers
    ```

    The response includes the base vampire object with an array of powers:

    ```json
    {
    "name": "Edward Cullen",
    "canFly": false,
    "batMode": false,
    "id": 9,
    "specialPowers": [
        {
        "power": "Enhanced Speed",
        "vampireId": 9,
        "id": 8
        }
    ]
    }
    ```

## Next steps

