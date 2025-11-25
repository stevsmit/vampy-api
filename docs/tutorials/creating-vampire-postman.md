# Tutorial: Creating a Vampire Profile in Postman

This tutorial shows how to build a basic `POST /vampires` request in Postman. You'll add the request to the Vampy API collection, wire it to collection variables, and verify the response.

This tutorial should take approximately 5 minutes.

## Prerequisites

* Postman Desktop or Web app
* Vampy API collection and environment imported from the `postman` folder of this repository
* `json-server` running locally with the `vampy_db.json` database

## Procedure

1. Open Postman and select the `Vampy API` workspace or collection.

2. Make sure the `Vampy API Local` environment is active. Confirm it contains a `baseUrl` variable pointing to `http://localhost:3000`.

3. In the Vampy collection, duplicate the existing `POST /vampires` request or create a new request named **Create vampire**:
   * Set the method to `POST`.
   * Set the URL to `{baseUrl}/vampires`.

4. On the **Headers** tab, ensure `Content-Type` is set to `application/json`.

5. On the **Body** tab, choose `raw` + `JSON` and paste sample data:

   ```json
   {
     "name": "Suki Nightwind",
     "canFly": true,
     "batMode": false
   }
   ```

6. Click **Send**. Postman returns the newly created object, including its generated `id`. Copy that `id`.

## Completion and validation

1. In Postman, wwitch to a `GET {baseUrl}/vampires/{lastVampireId}` request.
2. Click **Send** to confirm the vampire you created now exists.
3. Check the response body to ensure `name`, `canFly`, and `batMode` match your input.

## Next steps

* Learn how to filter vampires by trait in [Retrieving Vampires by Trait in Postman](retrieving-vampires-trait-postman.md).
* Practice editing or deleting records in [Updating or Removing Vampires in Postman](updating-removing-vampires-postman.md).
* Explore the CLI equivalent in [Creating a Complete Vampire Profile](adding-vampire-tutorial.md).
