# Tutorial: Creating a complete vampire profile

This tutorial shows you how to use the `POST` method to add
a new vampire entity to the database, along with their
media appearance and special power.

This tutorial should take approximately 20 minutes.

## Prerequisites

* Confirm that the `json-server` app is running with the `vampy_db.json` database. For more information, see [Becoming _familiar_: Getting started with the Vampy API](/docs/quickstart/getting-started.md).

## Procedure

1. Open a terminal.

2. Run the following `cURL` command using the `POST` method.
This command creates the core entry to the `/vampires` resource.

    <div class="highlight"><pre><code class="language-bash">
    curl -X POST -H "Content-Type: application/json" -d '{
        "name": "Edward Cullen",
        "canFly": false,
        "batMode": false
    }' http://localhost:3000/vampires
    </code></pre></div>

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
the movie *Twilight* to the `/media` resource. Include the `vampireId` generated from Step 2.

    <div class="highlight"><pre><code class="language-bash">
    curl -X POST \
    -H "Content-Type: application/json" \
    -d '{
        "type": "film", 
        "title": "Twilight",
        "year": 2008,
        "vampireId": 8
    }' \
    http://localhost:3000/media
    </code></pre></div>

    The API returns the new power object with its own unique `id`. For example:

    ```json
    {
    "type": "film",
    "title": "Twilight",
    "year": 2008,
    "vampireId": 8,
    "id": 5
    }
    ```

4. Run the following `cURL` command using the `POST` method to add
the power *Enhanced Speed* to the `/specialPowers` resource. Include the `vampireId` generated from Step 2.

    <div class="highlight"><pre><code class="language-bash">
    curl -X POST \
    -H "Content-Type: application/json" \
    -d '{
        "power": "Enhanced Speed", 
        "vampireId": 8
    }' \
    http://localhost:3000/specialPowers
    </code></pre></div>

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
