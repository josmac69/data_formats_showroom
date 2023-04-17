# Schema evolution in ORC

GitHub CoPilot:

ORC format supports schema evolution, allowing users to add, delete, or modify columns without having to rewrite the entire dataset. This provides flexibility in adapting to changing data structures and schema requirements, allowing users to add, delete, or modify columns without having to rewrite the entire dataset.

This provides flexibility in adapting to changing data structures and schema requirements. For example, if you want to add a new column to the schema, you can do so without having to rewrite the entire dataset. Older data files that do not have the new column can still be read by new readers, which will fill in the missing values with nulls or the specified default values. New data files with the additional column can also be read by old readers, which will ignore the new column during deserialization.

The schema is stored in the footer of the ORC file. The footer contains metadata about the file, including the schema, compression codec, and statistics about the data in each column.

The footer is stored at the end of the file. It contains metadata about the file, including the schema, compression codec, and statistics about the data in each column. The size of the footer is typically small, as it only contains metadata about the file. The footer is stored in the file as a serialized protobuf message.
