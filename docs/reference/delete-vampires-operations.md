# DELETE /vampires references

Use the `DELETE` method to delete a `/vampire` resource.

## DELETE /vampires/{id}

Delete a vampire by its ID.

### Parameters

| Parameter | Description | Type |
|---------|------|---------------|
| **id** (_required_) | Unique ID of the vampire | integer |

### Responses

| HTTP Code | Description | Schema |
|---------|------|---------------|
| 200 | Vampire profile successfully deleted | Vampire object |
| 404 | Vampire not found | ApiError |

### Example command

```bash
curl -X DELETE http://{base_url}/vampires/1
```
