# Tutorial: Filtering vampires by trait

This tutorial demonstrates how to use the `GET` method with multiple query parameters to filter the entire `/vampires` resource for profiles that match specific traits.

The goal of this tutorial is to show you how to:

* Filter vampires by a single trait using query parameters
* Combine multiple filters to find vampires matching specific criteria
* Find all "Classic Cinematic Vampires"—entities that can fly and can transform into a bat

This tutorial should take approximately 10 minutes.

## Prerequisites

* Confirm that the `json-server` app is running with the `vampy_db.json` database. For more information, see [Becoming _familiar_: Getting started with the Vampy API](../quickstart/getting-started.md).

* Basic familiarity with query parameters (e.g., ?key=value).

## Procedure

1. Open a terminal.

2. Use the `canFly` boolean to narrow down the list to only those vampires capable of flight by running the following `GET` command:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/vampires?canFly=true
    </code></pre></div>

    The API returns a JSON array containing only vampires where `canFly` is `true`. For example:

    ```json
    [
    {
        "id": 3,
        "name": "David",
        "canFly": true,
        "batMode": false
    },
    {
        "id": 4,
        "name": "Strigoi",
        "canFly": true,
        "batMode": true
    },
    {
        "id": 5,
        "name": "Count Dracula",
        "canFly": true,
        "batMode": true
    },
    {
        "id": 6,
        "name": "The Count",
        "canFly": true,
        "batMode": true
    }
    ]
    ```

3. To narrow the results, run the following `GET` command, which adds the `batMode` property to the query string and combines the filter with `canFly` parameter:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/vampires?canFly=true&batMode=true
    </code></pre></div>

    The API returns a smaller, more filtered list. This list contains only the "Classic Cinematic Vampires" who possess both traits (Strigoi, Count Dracula, and The Count).

    ```json
    [
    {
        "id": 4,
        "name": "Strigoi",
        "canFly": true,
        "batMode": true
    },
    {
        "id": 5,
        "name": "Count Dracula",
        "canFly": true,
        "batMode": true
    },
    {
        "id": 6,
        "name": "The Count",
        "canFly": true,
        "batMode": true
    }
    ]
    ```

4. Optional: Verify that filters work in reverse. For example, the following command queries `canFly=false` and `batMode=false` within the `GET` command:

    <div class="highlight"><pre><code class="language-bash">
    curl -X GET \
    http://localhost:3000/vampires?canFly=false&batMode=false
    </code></pre></div>

    The following vampires are returned:

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
    },
    {
        "id": 7,
        "name": "Blade",
        "canFly": false,
        "batMode": false
    }
    ]
    ```

## Next steps

Now that you understand how to filter vampires by traits, you can:

* Learn how to create a complete vampire profile in the [Creating a Complete Vampire Profile](adding-vampire-tutorial.md) tutorial
* Learn how to update vampire information in the [Updating Vampire Information](updating-vampire-information.md) tutorial
* Review the [Reference documentation](../reference/get-vampires-operations.md) for complete details on GET operations for the `/vampires` resource
