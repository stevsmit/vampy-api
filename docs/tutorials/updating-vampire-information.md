# Tutorial: Updating Vampire Information

This tutorial demonstrates how to use the `PATCH` and `PUT` methods to update vampire profiles in the `/vampires` resource. You'll learn when to use each method and how they differ.

The goal of this tutorial is to show you how to:

* Use `PATCH` to update specific fields on a vampire profile
* Use `PUT` to replace an entire vampire profile
* Understand the differences between these two update methods

This tutorial should take approximately 10 minutes.

## Prerequisites

* Confirm that the `json-server` app is running with the `vampy_db.json` database. For more information, see [Becoming _familiar_: Getting started with the Vampy API](/docs/quickstart/getting-started.md).

* Basic familiarity with the `GET` method to retrieve vampire profiles.

## Understanding PATCH vs PUT

- **PATCH**: Updates only the fields you specify, leaving other fields unchanged. Use this when you want to modify one or a few fields.
- **PUT**: Replaces the entire resource with the new object. All fields must be provided. Use this when you want to completely replace a resource.

## Procedure

### Part 1: Using PATCH to update specific fields

1. Open a terminal.

2. First, retrieve the current vampire profile to see its current state. Run the following `GET` command:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/vampires/7
    </code></pre></div>

    The API returns the current Blade profile:

    ```json
    {
        "id": 7,
        "name": "Blade",
        "canFly": false,
        "batMode": false
    }
    ```

3. Use `PATCH` to update only the `batMode` field. Run the following command:

    <div class="highlight"><pre><code class="language-bash">
    curl -X PATCH \
    -H "Content-Type: application/json" \
    -d '{
        "batMode": true
    }' \
    http://localhost:3000/vampires/7
    </code></pre></div>

    The API returns the updated vampire object. Notice that only `batMode` changed, while `name` and `canFly` remained unchanged:

    ```json
    {
        "id": 7,
        "name": "Blade",
        "canFly": false,
        "batMode": true
    }
    ```

4. Use `PATCH` again to update multiple fields at once. Run the following command to update both `canFly` and `batMode`:

    <div class="highlight"><pre><code class="language-bash">
    curl -X PATCH \
    -H "Content-Type: application/json" \
    -d '{
        "canFly": true,
        "batMode": true
    }' \
    http://localhost:3000/vampires/7
    </code></pre></div>

    The API returns the updated profile:

    ```json
    {
        "id": 7,
        "name": "Blade",
        "canFly": true,
        "batMode": true
    }
    ```

### Part 2: Using PUT to replace the entire resource

5. Use `PUT` to completely replace the vampire profile. **Important**: With `PUT`, you must provide all required fields. Run the following command:

    <div class="highlight"><pre><code class="language-bash">
    curl -X PUT \
    -H "Content-Type: application/json" \
    -d '{
        "name": "Blade",
        "canFly": false,
        "batMode": false
    }' \
    http://localhost:3000/vampires/7
    </code></pre></div>

    The API returns the replaced vampire object:

    ```json
    {
        "id": 7,
        "name": "Blade",
        "canFly": false,
        "batMode": false
    }
    ```

6. Verify the update by retrieving the profile again:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/vampires/7
    </code></pre></div>

## Key differences

| Method | Use case | Fields required | Behavior |
|--------|----------|----------------|----------|
| `PATCH` | Update one or more specific fields | Only fields you want to change | Partial update - other fields remain unchanged |
| `PUT` | Replace entire resource | All required fields (`name`, `canFly`, `batMode`) | Complete replacement - missing fields may be lost |

## Completion and validation

Run the following command to verify the final state of the vampire profile:

```bash
curl -X GET \
http://localhost:3000/vampires/7
```

## Next steps

Now that you understand how to update vampire profiles, you can:

* Learn how to update media appearances in the [Managing Media Appearances](/docs/tutorials/managing-media-appearances.md) tutorial
* Learn how to update special powers in the [Working with Special Powers](/tutorials/working-with-special-powers.md) tutorial
* Learn how to remove resources in the [Removing Resources](/docs/tutorials/removing-resources.md) tutorial
