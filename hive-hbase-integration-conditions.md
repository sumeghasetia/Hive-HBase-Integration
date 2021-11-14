## What would happen if you disable the HBase table?

If we disable and drop the HBase table, the Hive table would still be present but the data won't be there in the table, the table will be empty and shows the HBase table is not found.

But if we only disable the HBase table, we won't be able to scan the HBase table. Also, if we try accessubg the Hive integration table it will show HBase table disabled error.

## What would happen if you drop the Hive integration table?

If we drop the hive integration table then the corresponding HBase table will also get dropped.
