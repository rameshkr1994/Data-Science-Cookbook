> Written with [StackEdit](https://stackedit.io/).
## RRDs using Spark 2.0+

- RDDs are schema-less structures that can help you handle both structured and unstructured data.
- RDDs are schema-less distributed collection of immutable JVM objects. They were available from the very beginning, since Matei Zaharia started working on Spark. 
- Simplifying a little bit, similarly to how Hadoop works, RDDs chunk the data into partitions and each executor receives a portion of the data. 

## Creation RDDs
In simple terms, there are two ways to create an RDD, you can either parallelize a collection such as a list of values of tuples or you can read the data from a file, we'll cover both ways.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0MDgxMDE1MTddfQ==
-->