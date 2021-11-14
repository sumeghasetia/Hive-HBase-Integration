# Hive-HBase-Integration

Step 1:  Create Hive table

```
create table card_transaction (Id INT, Card_number String, Transaction string) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' TBLPROPERTIES("skip.header.line.count"="1");
```

Step 2: Load the data using the local file path

```
load data local inpath '/home/cloudera/Desktop/shared_folder/card_transact.csv' OVERWRITE into table card_transaction;
```

![image](/images/create-load-table-hive.png)

Check the data in Hive:

```
select * from card_transaction limit 4;
```

Check the data in warehouse directory:

```
hadoop fs -ls /user/hive/warehouse/userdb.db
```

![image](/images/check-warehouse-files.png)

Step 3: HBase-Hive Integration

```
create table hive_card_transact_tbl2 (id INT, card_number String, transaction String) STORED BY 'org.apache.hadoop.hive.hbase.HBaseStorageHandler' WITH SERDEPROPERTIES("hbase.columns.mapping" = ":key,a:card_number,a:transaction") TBLPROPERTIES ("hbase.table.name" = "hbase_card_trans");
```

![image](/images/integration-2.png)

Step 4: Now inserting data into hive staging table we created:

```
insert overwrite table hive_card_transact_tbl2 select * from card_transaction;
```

![image](/images/insert-data.png)

This command will automatically push the data in Hbase as well

Check data in both Hive and Hbase tables, data will be there.
