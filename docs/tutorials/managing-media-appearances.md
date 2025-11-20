# Tutorial: Managing Media Appearances

This tutorial demonstrates how to work with the `/media` resource using `GET`, `POST`, and `PATCH` methods. You'll learn how to retrieve, create, and update media appearances linked to vampires.

The goal of this tutorial is to show you how to:

* Retrieve media appearances for a specific vampire
* Add new media appearances to the database
* Update existing media entries

This tutorial should take approximately 10 minutes.

## Prerequisites

* Confirm that the `json-server` app is running with the `vampy_db.json` database. For more information, see [Becoming _familiar_: Getting started with the Vampy API](../quickstart/getting-started.md).

* Basic familiarity with the `GET` method and query parameters.

## Procedure

### Part 1: Retrieving media appearances

1. Open a terminal.

2. Retrieve all media appearances in the database by running the following `GET` command:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/media
    </code></pre></div>

    The API returns a list of all media entries:

    ```json
    [
        {
            "id": 1,
            "type": "movie",
            "title": "Underworld",
            "year": 2003,
            "vampireId": 1
        },
        {
            "id": 2,
            "type": "television",
            "title": "Sesame Street",
            "year": 1972,
            "vampireId": 6
        },
        ...
    ]
    ```

3. Filter media by a specific vampire using the `vampireId` query parameter. Run the following command to get all media for Count Dracula (id: 5):

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/media?vampireId=5
    </code></pre></div>

    The API returns only media linked to that vampire:

    ```json
    [
        {
            "id": 3,
            "type": "book",
            "title": "Dracula",
            "year": 1897,
            "vampireId": 5
        }
    ]
    ```

4. Retrieve a single media entry by its ID:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/media/1
    </code></pre></div>

    The API returns the specific media entry:

    ```json
    {
        "id": 1,
        "type": "movie",
        "title": "Underworld",
        "year": 2003,
        "vampireId": 1
    }
    ```

### Part 2: Creating new media appearances

5. Add a new media appearance using the `POST` method. Run the following command to add a movie for Selene (vampireId: 1):

    <div class="highlight"><pre><code class="language-bash">
    curl -X POST \
    -H "Content-Type: application/json" \
    -d '{
        "type": "movie",
        "title": "Underworld: Evolution",
        "year": 2006,
        "vampireId": 1
    }' \
    http://localhost:3000/media
    </code></pre></div>

    The API returns the new media entry with an auto-generated `id`:

    ```json
    {
        "type": "movie",
        "title": "Underworld: Evolution",
        "year": 2006,
        "vampireId": 1,
        "id": 5
    }
    ```

6. Verify the new media entry was created by retrieving all media for Selene:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/media?vampireId=1
    </code></pre></div>

    The response now includes both media entries:

    ```json
    [
        {
            "id": 1,
            "type": "movie",
            "title": "Underworld",
            "year": 2003,
            "vampireId": 1
        },
        {
            "id": 5,
            "type": "movie",
            "title": "Underworld: Evolution",
            "year": 2006,
            "vampireId": 1
        }
    ]
    ```

### Part 3: Updating media appearances

7. Update an existing media entry using the `PATCH` method. Run the following command to correct the year for the media entry you just created:

    <div class="highlight"><pre><code class="language-bash">
    curl -X PATCH \
    -H "Content-Type: application/json" \
    -d '{
        "year": 2006
    }' \
    http://localhost:3000/media/5
    </code></pre></div>

    The API returns the updated media entry:

    ```json
    {
        "id": 5,
        "type": "movie",
        "title": "Underworld: Evolution",
        "year": 2006,
        "vampireId": 1
    }
    ```

8. Update multiple fields at once. Run the following command to update both the title and type:

    <div class="highlight"><pre><code class="language-bash">
    curl -X PATCH \
    -H "Content-Type: application/json" \
    -d '{
        "title": "Underworld: Evolution (Extended Cut)",
        "type": "film"
    }' \
    http://localhost:3000/media/5
    </code></pre></div>

    The API returns the updated entry:

    ```json
    {
        "id": 5,
        "type": "film",
        "title": "Underworld: Evolution (Extended Cut)",
        "year": 2006,
        "vampireId": 1
    }
    ```

## Completion and validation

Verify your changes by retrieving the updated media entry:

```bash
curl -X GET \
http://localhost:3000/media/5
```

## Next steps

Now that you understand how to manage media appearances, you can:

* Learn how to work with special powers in the [Working with Special Powers](working-with-special-powers.md) tutorial
* Learn how to remove resources in the [Removing Resources](removing-resources.md) tutorial
* Review the [Reference documentation](../reference/about-media.md) for complete details on the `/media` resource
