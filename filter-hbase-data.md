## Filtering the HBASE table 

```
-- importing the dependencies

import org.apache.hadoop.hbase.filter.SingleColumnValueFilter 
import org.apache.hadoop.hbase.filter.CompareFilter
import org.apache.hadoop.hbase.filter.BinaryComparator

```

```
--filtering logic

scan 'hbase_card_trans', { FILTER => SingleColumnValueFilter.new(Bytes.toBytes('a'), Bytes.toBytes('transaction'), CompareFilter::CompareOp.valueOf('EQUAL'),BinaryComparator.new(Bytes.toBytes('FRAUD')))}

```

![image](/images/filteration.png)

Output of the above query

![image](/images/filter-output.png)

If we run the same filtering logic in hive table:

![image](/images/hive-filter-output.png)

The query reponse time is much better in case of HBase. HBase Command took 0.7090 sec and Hive command took 67.078 which far more than former.
