# Tutorial: Updating or Removing Vampires in Postman

This tutorial covers the basic update (`PATCH`/`PUT`) and delete (`DELETE`) workflows for the `/vampires` resource using Postman. You'll edit an existing record, replace it entirely, and then remove it safely.

The goal of this tutorial is to show you how to:

* Reuse the `lastVampireId` (or any ID) when targeting specific records
* Send partial updates with `PATCH` and replace the resource with `PUT`
* Delete the record while running guardrail tests

Estimated time to complete: 5 minutes.

## Prerequisites

* Postman Desktop or Web app
* Vampy API collection and environment imported from the `postman` folder of this repository
* A valid vampire `id` (for example, the `lastVampireId` captured in [Creating a Vampire Profile in Postman](creating-vampire-postman.md))
* `json-server` running locally with the `vampy_db.json` database

## Procedure

### Part 1: PATCH partial updates

1. Open the **Update vampire (PATCH)** request or create a new one:
   * Method: `PATCH`
   * URL: `{{baseUrl}}/vampires/{{vampireId}}`

2. On the **Body** tab choose `raw` + `JSON` and supply only the fields you want to change:

   ```json
   {
     "canFly": false
   }
   ```

3. Click **Send** and confirm the response body shows the updated field while keeping other values intact.

### Part 2: PUT full replacements

4. Duplicate the PATCH request and rename it **Replace vampire (PUT)**.

5. Change the method to `PUT` and provide the complete resource representation:

   ```json
   {
     "name": "Suki Nightwind",
     "canFly": false,
     "batMode": true
   }
   ```

6. Click **Send**. The server replaces the entire record with the new data (missing fields are removed), so double-check the response payload.

### Part 3: DELETE the record

7. Create a request named **Delete vampire**:
   * Method: `DELETE`
   * URL: `{{baseUrl}}/vampires/{{lastVampireId}}`

8. Optional safety test: on the **Tests** tab add the following snippet to confirm the deletion:

   ```javascript
   pm.test("Vampire deleted", () => pm.response.to.have.status(200));
   ```

9. Click **Send**. The API returns the removed object as confirmation.

10. Run a follow-up `GET {{baseUrl}}/vampires/{{lastVampireId}}`. You should receive `404` or an empty response, indicating the record was successfully removed.

## Completion and validation

* Ensure both PATCH and PUT responses reflect the new values you supplied.
* Confirm the DELETE response contains the removed object and that subsequent GET calls fail.

## Next steps

* Re-create test data with [Creating a Vampire Profile in Postman](creating-vampire-postman.md).
* Practice more targeted queries with [Retrieving Vampires by Trait in Postman](retrieving-vampires-trait-postman.md).
* Consult the [Reference documentation](../reference/operations.md) for the full schema.

