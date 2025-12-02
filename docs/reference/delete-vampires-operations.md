# DELETE /vampires references

Use the `DELETE` method to delete a `/vampires` resource.

## DELETE /vampires/{id} {delete-vampireid}

Delete a vampire by its ID.

### Parameters {delete-vampireid-parameters}

| Parameter | Description | Type |
|---------|------|---------------|
| **id** (_required_) | Unique ID of the vampire | integer |

### Responses {delete-vampireid-responses}

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Vampire profile successfully deleted | Vampire object |
| 404 | Vampire not found | ApiError |

### Example command {delete-vampireid-example-command}

```bash
curl -X DELETE http://{base_url}/vampires/1
```
