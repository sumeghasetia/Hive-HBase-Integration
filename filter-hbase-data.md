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
