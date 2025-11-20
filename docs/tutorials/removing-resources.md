# Tutorial: Removing Resources

This tutorial demonstrates how to use the `DELETE` method to remove resources from all three Vampy API resources: `/vampires`, `/media`, and `/specialPowers`.

The goal of this tutorial is to show you how to:

* Delete vampire profiles
* Delete media appearances
* Delete special power entries
* Understand the implications of deleting resources

This tutorial should take approximately 10 minutes.

## Prerequisites

* Confirm that the `json-server` app is running with the `vampy_db.json` database. For more information, see [Becoming _familiar_: Getting started with the Vampy API](../quickstart/getting-started.md).

* Basic familiarity with the `GET` method to verify deletions.

## Important considerations

**Warning**: Deleting a resource is permanent. When you delete a vampire, consider whether you also want to delete associated media and special powers, as they will remain in the database but be orphaned (their `vampireId` will reference a non-existent vampire).

## Procedure

### Part 1: Deleting a special power

1. Open a terminal.

2. First, verify the special power exists by retrieving it:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/specialPowers/3
    </code></pre></div>

    The API returns the power entry:

    ```json
    {
        "id": 3,
        "power": "Being a vampire",
        "vampireId": 2
    }
    ```

3. Delete the special power using the `DELETE` method:

    <div class="highlight"><pre><code class="language-bash">
    curl -X DELETE \
    http://localhost:3000/specialPowers/3
    </code></pre></div>

    The API returns an empty response (HTTP 200) on successful deletion.

4. Verify the deletion by attempting to retrieve the deleted power:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/specialPowers/3
    </code></pre></div>

    The API returns a 404 Not Found error, confirming the resource has been deleted.

### Part 2: Deleting a media appearance

5. Verify the media entry exists:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/media/2
    </code></pre></div>

    The API returns the media entry:

    ```json
    {
        "id": 2,
        "type": "television",
        "title": "Sesame Street",
        "year": 1972,
        "vampireId": 6
    }
    ```

6. Delete the media appearance:

    <div class="highlight"><pre><code class="language-bash">
    curl -X DELETE \
    http://localhost:3000/media/2
    </code></pre></div>

    The API returns an empty response (HTTP 200) on successful deletion.

7. Verify the deletion:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/media/2
    </code></pre></div>

    The API returns a 404 Not Found error.

### Part 3: Deleting a vampire profile

8. Before deleting a vampire, check what media and powers are associated with it. Retrieve the vampire with embedded resources:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/vampires/2?_embed=media&_embed=specialPowers
    </code></pre></div>

    The API returns the vampire profile with associated resources:

    ```json
    {
        "id": 2,
        "name": "Peter Loew",
        "canFly": false,
        "batMode": false,
        "media": [
            {
                "id": 1,
                "type": "movie",
                "title": "Vampire's Kiss",
                "year": 1988,
                "vampireId": 2
            }
        ],
        "specialPowers": []
    }
    ```

9. Delete the vampire profile:

    <div class="highlight"><pre><code class="language-bash">
    curl -X DELETE \
    http://localhost:3000/vampires/2
    </code></pre></div>

    The API returns an empty response (HTTP 200) on successful deletion.

10. Verify the deletion:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/vampires/2
    </code></pre></div>

    The API returns a 404 Not Found error.

11. **Note**: The associated media entry still exists but is now orphaned (its `vampireId` references a deleted vampire). You can verify this:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/media/1
    </code></pre></div>

    The media entry still exists:

    ```json
    {
        "id": 1,
        "type": "movie",
        "title": "Vampire's Kiss",
        "year": 1988,
        "vampireId": 2
    }
    ```

    If you want to clean up orphaned resources, you would need to delete them separately or update their `vampireId` to reference a different vampire.

## Best practices

1. **Check dependencies first**: Before deleting a vampire, retrieve it with embedded resources to see what will be orphaned.

2. **Clean up orphaned resources**: Consider deleting or reassigning associated media and special powers when deleting a vampire.

3. **Use GET to verify**: Always verify deletions by attempting to retrieve the deleted resource.

4. **Be cautious**: Deletions are permanent. In a production environment, you might want to implement soft deletes or backup strategies.

## Completion and validation

Verify that all deletions were successful by listing the remaining resources:

```bash
# List remaining vampires
curl -X GET http://localhost:3000/vampires

# List remaining media
curl -X GET http://localhost:3000/media

# List remaining special powers
curl -X GET http://localhost:3000/specialPowers
```

## Next steps

Now that you understand how to remove resources, you have completed the full CRUD (Create, Read, Update, Delete) operations for all resources. You can:

* Review the [Reference documentation](../reference/operations.md) for a complete overview of all operations
* Explore the [Swagger documentation](../reference/vampy-api.md) for interactive API exploration
& Practice combining operations by creating, updating, and managing complete vampire profiles
