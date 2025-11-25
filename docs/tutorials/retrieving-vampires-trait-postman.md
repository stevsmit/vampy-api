# Tutorial: Retrieving Vampires by Trait in Postman

This tutorial walks through a simple `GET /vampires` request that filters results by trait. You'll configure query parameters inside Postman, inspect the returned data, and save an example for quick comparisons.

The goal of this tutorial is to show you how to:

* Add and manage query parameters in Postman
* Send a `GET` request to `/vampires` with filters such as `canFly=true`
* Save a successful response as an example for future reference

Estimated time to complete: 5 minutes.

## Prerequisites

* Postman Desktop or Web app
* Vampy API collection and environment imported from the `postman` folder of this repository
* `json-server` running locally with the `vampy_db.json` database

## Procedure

1. Open Postman and select the Vampy collection.

2. Create or open a request named **List vampires by trait**.
   * Set the method to `GET`.
   * Set the URL to `{{baseUrl}}/vampires`.

3. Switch to the **Params** tab and add query parameters:
   * `canFly` → `true`
   * Optional: Add additional filters such as `batMode=false` or `name=Selene`.

4. Click **Send**. Verify the response status is `200` and the body shows only vampires matching your filters.

   Save the request to keep the test.

6. To capture a baseline response, click **Save Response > Save as example**, give it a descriptive name such as `canFly=true`, and click **Save**.

## Completion and validation

1. Modify a parameter (for example, toggle `canFly` to `false`) and click **Send** to confirm the filters update dynamically.
2. Compare the new response with the saved example to understand output differences.

## Next steps

* Create new vampires to test different traits in [Creating a Vampire Profile in Postman](creating-vampire-postman.md).
* Learn to update or delete a record once you find it in [Updating or Removing Vampires in Postman](updating-removing-vampires-postman.md).

