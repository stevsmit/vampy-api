# Becoming _familiar_: Getting started with the Vampy API

This tutorial guides you through the essential steps required to run the Vampire Tracker API (Vampy API) locally using `json-server`, plus the optional setup for issuing requests through Postman. By the end you will have the REST API running at `http://localhost:3000` and, if desired, the Vampy Postman environment imported for GUI-based testing.

> Procedures throughout this documentation set use {base_url} as replaceable variable. If you follow the instructions in this guide, {base_url} will be replaced with `http://localhost:3000`.

> Procedures throughout this documentation set are intended for MacOS or Linux. CLI procedures for Windows OS might be different.

Expect this preparation to take about 20 minutes to complete.

## Prerequisites

Before starting, ensure that you meet the following prerequisites:

* [`Node.js`](https://nodejs.org/en/download), which is used for running JavaScript packages.
* [`json-server`](https://www.npmjs.com/package/json-server/v/0.17.4), which is used to host our API endpoints from the JSON database file.
* [`git` command line tool](https://docs.github.com/en/get-started/git-basics/set-up-git), which is used to clone the repository.

## Getting the project files

The following procedure shows you how to clone the Github repository.

1. Open a terminal. Ensure that you are in the `$HOME` directory by running the following command:

    <div class="highlight"><pre><code class="language-bash">
    cd $HOME
    </code></pre></div>

2. Clone the project by running the following command:

    <div class="highlight"><pre><code class="language-bash">
    git clone https://github.com/stevsmit/vampy-api.git
    </code></pre></div>

## Starting the Vampy API server

The following procedure shows you how to start the Vampy API data.

1. Navigate into the `vampy-api/api` directory by running the following command:

    <div class="highlight"><pre><code class="language-bash">
    cd vampy-api/api
    </code></pre></div>

2. Start the JSON server by running the following command:

    <div class="highlight"><pre><code class="language-bash">
    json-server vampy_db.json
    </code></pre></div>

    Your terminal will show confirmation messages that the server is running and the available resources:

    ```json
    \{^_^}/ hi!

    Loading vampy_db.json
    Done

    Resources
    http://localhost:3000/vampires
    http://localhost:3000/media
    http://localhost:3000/specialPowers

    Home
    http://localhost:3000

    Type s + enter at any time to create a snapshot of the database
    ```

## Making a test call to the Vampy API server

The following procedure shows you how to make a test call to the Vampy API server.

1. Open a different terminal window, or a new terminal.

2. Retrieve information for the `/vampires` resource by entering the following command. By default, running the `curl` command automatically retrieves resources with the `GET`.

    <div class="highlight"><pre><code class="language-bash">
    curl http://localhost:3000/vampires
    </code></pre></div>

    If the service is running, information about the `/vampires` resource is returned. For example:

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
    },
    {
        "id": 7,
        "name": "Blade",
        "canFly": false,
        "batMode": false
    },
    ]
    ```

## Importing the Postman environment

If you prefer to issue requests from Postman instead of `curl`, import the bundled environment so the tutorials can reference ready-made variables.

1. In your file explorer, locate the `postman` directory inside the cloned repository. It contains `vampy-api-local.postman_environment.json`.

2. Open Postman and click the **Environments** icon next to the workspace selector.

3. Click **Import**, select the `vampy-api-local.postman_environment.json` file, and confirm the import.

4. On the **Environment** tab, click **Set Active** to activate the Vampy API workspace.

5. Optional: Verify the environment by opening a new request tab and entering `{{baseUrl}}/vampires`. When you click **Send**, the request should resolve to `http://localhost:3000/vampires`.
