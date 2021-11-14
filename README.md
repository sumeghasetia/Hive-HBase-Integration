# Hive-HBase-Integration

Step 1:  Create Hive table

'''
create table card_transaction (Id INT, Card_number String, Transaction string) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' TBLPROPERTIES("skip.header.line.count"="1");
'''

Step 2: Load the data using the local file path

```
load data local inpath '/home/cloudera/Desktop/shared_folder/card_transact.csv' OVERWRITE into table card_transaction;
```

Check the data in Hive:

```
select * from card_transaction limit 4;
```

Check the data in warehouse directory:

```
hadoop fs -ls /user/hive/warehouse/userdb.db
```
