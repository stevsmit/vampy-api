# Postman assets for the Vampy API

This folder contains downloadable assets referenced throughout the Postman tutorials.

## Files

- `vampy-api-local.postman_environment.json` – Postman environment pre-populated with variables sourced from `api/vampy_db.json`. Import it into Postman before running the tutorials so the `baseUrl`, sample IDs, and helper variables are available.

## Import instructions

1. Open Postman and click the **Environments** icon.
2. Select **Import**, choose the JSON file from this folder, and click **Open**.
3. Activate the **Vampy API Local** environment before running any requests.

> Tip: The `lastVampireId` variable is intentionally blank. The tutorials include a Postman test script that sets this value automatically after you create a new vampire.

