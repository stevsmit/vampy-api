# Tutorial: Working with Special Powers

This tutorial demonstrates how to work with the `/specialPowers` resource using `GET`, `POST`, and `PATCH` methods. You'll learn how to retrieve, create, and update special powers linked to vampires.

The goal of this tutorial is to show you how to:

* Retrieve special powers for a specific vampire
* Add new special powers to the database
* Update existing special power entries

This tutorial should take approximately 20 minutes.

## Prerequisites

* Confirm that the `json-server` app is running with the `vampy_db.json` database. For more information, see [Becoming _familiar_: Getting started with the Vampy API](../quickstart/getting-started.md).

* Basic familiarity with the `GET` method and query parameters.

## Procedure

### Part 1: Retrieving special powers

1. Open a terminal.

2. Retrieve all special powers in the database by running the following `GET` command:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/specialPowers
    </code></pre></div>

    The API returns a list of all special powers:

    ```json
    [
        {
            "id": 1,
            "power": "Day-walking",
            "vampireId": 7
        },
        {
            "id": 2,
            "power": "Enhanced Marksmanship",
            "vampireId": 1
        },
        {
            "id": 3,
            "power": "Being a vampire",
            "vampireId": 2
        },
        ...
    ]
    ```

3. Filter special powers by a specific vampire using the `vampireId` query parameter. Run the following command to get all powers for Blade (id: 7):

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/specialPowers?vampireId=7
    </code></pre></div>

    The API returns only powers linked to that vampire:

    ```json
    [
        {
            "id": 1,
            "power": "Day-walking",
            "vampireId": 7
        }
    ]
    ```

4. Retrieve a single special power by its ID:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/specialPowers/1
    </code></pre></div>

    The API returns the specific power entry:

    ```json
    {
        "id": 1,
        "power": "Day-walking",
        "vampireId": 7
    }
    ```

5. Retrieve a vampire profile with embedded special powers using the `_embed` parameter:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/vampires/7?_embed=specialPowers
    </code></pre></div>

    The API returns the vampire profile with all associated powers:

    ```json
    {
        "id": 7,
        "name": "Blade",
        "canFly": false,
        "batMode": false,
        "specialPowers": [
            {
                "id": 1,
                "power": "Day-walking",
                "vampireId": 7
            }
        ]
    }
    ```

### Part 2: Creating new special powers

6. Add a new special power using the `POST` method. Run the following command to add a power for Blade (vampireId: 7):

    <div class="highlight"><pre><code class="language-bash">
    curl -X POST \
    -H "Content-Type: application/json" \
    -d '{
        "power": "Vampire Slaying",
        "vampireId": 7
    }' \
    http://localhost:3000/specialPowers
    </code></pre></div>

    The API returns the new power entry with an auto-generated `id`:

    ```json
    {
        "power": "Vampire Slaying",
        "vampireId": 7,
        "id": 8
    }
    ```

7. Verify the new power was created by retrieving all powers for Blade:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/specialPowers?vampireId=7
    </code></pre></div>

    The response now includes both powers:

    ```json
    [
        {
            "id": 1,
            "power": "Day-walking",
            "vampireId": 7
        },
        {
            "id": 8,
            "power": "Vampire Slaying",
            "vampireId": 7
        }
    ]
    ```

### Part 3: Updating special powers

8. Update an existing special power using the `PATCH` method. Run the following command to update the power name:

    <div class="highlight"><pre><code class="language-bash">
    curl -X PATCH \
    -H "Content-Type: application/json" \
    -d '{
        "power": "Expert Vampire Slaying"
    }' \
    http://localhost:3000/specialPowers/8
    </code></pre></div>

    The API returns the updated power entry:

    ```json
    {
        "id": 8,
        "power": "Expert Vampire Slaying",
        "vampireId": 7
    }
    ```

9. Update the `vampireId` to reassign a power to a different vampire. Run the following command:

    <div class="highlight"><pre><code class="language-bash">
    curl -X PATCH \
    -H "Content-Type: application/json" \
    -d '{
        "vampireId": 1
    }' \
    http://localhost:3000/specialPowers/8
    </code></pre></div>

    The API returns the updated entry with the new `vampireId`:

    ```json
    {
        "id": 8,
        "power": "Expert Vampire Slaying",
        "vampireId": 1
    }
    ```

## Completion and validation

Verify your changes by retrieving the updated special power:

```bash
curl -X GET \
http://localhost:3000/specialPowers/8
```

You can also verify by checking which powers are now associated with the updated vampire:

```bash
curl -X GET \
http://localhost:3000/specialPowers?vampireId=1
```

## Next steps

Now that you understand how to work with special powers, you can:

* Learn how to remove resources in the [Removing Resources](removing-resources.md) tutorial
* Review the [Reference documentation](../reference/about-specialpowers.md) for complete details on the `/specialPowers` resource
* Learn how to update vampire profiles in the [Updating Vampire Information](updating-vampire-information.md) tutorial
