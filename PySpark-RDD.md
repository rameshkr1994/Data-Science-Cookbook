> Written with [StackEdit](https://stackedit.io/).
## RRDs using Spark 2.0+

- RDDs are schema-less structures that can help you handle both structured and unstructured data.
- RDDs are schema-less distributed collection of immutable JVM objects. They were available from the very beginning, since Matei Zaharia started working on Spark. 
- Simplifying a little bit, similarly to how Hadoop works, RDDs chunk the data into partitions and each executor receives a portion of the data. 

## Creation RDDs

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMxODM4ODYyMV19
-->