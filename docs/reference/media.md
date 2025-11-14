# About the `/media` resource

| Property | Type | Description | Example |
|----------|------|-------------|---------|
|`id` |`integer` |Unique identifier for this entry. | `1` |
|`type` |`string` |The medium where the vampire appears (for example, movie, television, book, etc.) | `movie` |
|`title` |`string` |The title of the work | "Underworld" |
|`vampireId` |`integer` |Links to the specific vampire in the `vampires` resource. | `1` |
|`year` |`integer` |The year of the media's release or publication. | `2003` |