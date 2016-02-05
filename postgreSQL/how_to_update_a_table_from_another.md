# How to update a table from another

The following is a script that keeps updates the contents of the `images` table from the `media` table.

In order to figure out which records are missing in the `images` table we do a `LEFT OUTER JOIN ... WHERE <key> IS NULL`


```sql
INSERT INTO instagram_images
            (instagram_id,
             url,
             created_at,
             updated_at)
SELECT media.instagram_id,
       media.raw_data #>> '{images, standard_resolution, url}' AS url,
       CURRENT_TIMESTAMP                                       AS created_at,
       CURRENT_TIMESTAMP                                       AS updated_at
FROM   instagram_media AS media
       LEFT OUTER JOIN instagram_images AS images
                    ON media.instagram_id = images.instagram_id
WHERE  images.instagram_id IS NULL
ORDER  BY media.instagram_id;
```
