# Columnar storage

Columnar storage is a data storage architecture that stores data in a column-wise format rather than row-wise format. In traditional row-based storage, all the columns of a row are stored together, whereas in columnar storage, all the values of a column are stored together. This storage approach has several advantages over row-based storage, including faster query performance, better compression, and improved data processing.

Parquet is a columnar storage format that is designed to optimize the storage and processing of large-scale data analytics workloads. It is an open-source file format that is widely used in big data processing frameworks such as Apache Hadoop and Apache Spark.

In Parquet, data is stored in a columnar format, meaning that all the values of a single column are stored together. This design allows for efficient compression and encoding of the data, resulting in a smaller file size and faster data access.

Parquet uses a technique called predicate pushdown, which allows filtering and aggregation operations to be performed at the storage level. This means that only the relevant data is loaded into memory for processing, reducing the amount of I/O required and improving query performance.

Another advantage of Parquet's columnar storage architecture is that it supports schema evolution. This means that as the schema of the data changes over time, new columns can be added or removed without affecting the existing data.

Overall, Parquet's columnar storage architecture provides several benefits over traditional row-based storage, including faster query performance, better compression, improved data processing, and support for schema evolution. These features make it a popular choice for storing and processing large-scale data analytics workloads.
