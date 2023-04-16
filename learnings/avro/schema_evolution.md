# AVRO schema evolution concept

Schema evolution is the ability to modify an existing schema over time, allowing changes to the data structure without breaking compatibility between readers and writers using different schema versions. Avro is designed with schema evolution in mind, making it a popular choice for big data and streaming applications where the data schema might need to evolve as requirements change.

Avro achieves schema evolution by using two schemas when deserializing data:

* Writer's schema: The schema used by the writer when the data was serialized. It's stored along with the serialized data, typically in the header of the Avro data file or as part of the metadata in a streaming message.

* Reader's schema: The schema used by the reader when deserializing the data. It represents the schema that the reader expects or can understand.

During deserialization, Avro performs schema resolution by comparing the writer's schema with the reader's schema. The resolution process involves checking field-by-field compatibility between the two schemas, and it supports the following types of schema changes:

* Adding a field: You can add a new field to the reader's schema that wasn't present in the writer's schema. To ensure compatibility, the new field must have a default value specified, which will be used when deserializing data that doesn't include the new field.

* Removing a field: You can remove a field from the reader's schema that was present in the writer's schema. In this case, the reader will ignore the field during deserialization.

* Modifying a field: You can modify a field's data type in the reader's schema, but only if the new data type is compatible with the original data type. For example, you can change a field from an "int" to a "long" but not from an "int" to a "string". Avro also supports complex type changes using "union" types.

* Renaming a field: You can rename a field in the reader's schema using the "aliases" attribute, which allows the reader to map the old field name in the writer's schema to the new field name in the reader's schema.

To maintain compatibility during schema evolution, it's essential to follow Avro's guidelines for schema changes and ensure that both reader and writer are using the appropriate schema versions. By doing so, you can evolve your data schema over time without breaking existing applications or data pipelines.