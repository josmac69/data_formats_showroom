# Protobuf - schema evolution

Yes, Protocol Buffers (Protobuf) supports schema evolution, allowing you to modify the schema over time without breaking compatibility between readers and writers using different schema versions. To ensure compatibility during schema evolution, you should follow these best practices:

* Field numbering: Protobuf fields are assigned unique field numbers. When you evolve your schema, never reuse or modify the field numbers for existing fields. Changing field numbers would break compatibility with existing serialized data and lead to incorrect deserialization.

* Adding fields: You can add new fields with new unique field numbers to the schema. Older readers will ignore these fields during deserialization, while newer readers will use the default values for these fields if they are not present in the serialized data.

* Removing fields: You can remove fields from the schema, but you should not reuse the field numbers of the removed fields. Instead, mark them as "reserved" to prevent accidental reuse. Older serialized data containing the removed fields can still be read by newer readers, but the removed fields will be ignored during deserialization.

* Modifying fields: Changing the data type of a field is generally not recommended, as it can break compatibility. However, you can change a field's type between compatible types, such as "int32", "int64", "uint32", "uint64", "sint32", "sint64", "fixed32", "fixed64", "sfixed32", and "sfixed64". For other types, you should introduce a new field with a new field number and a different type, and deprecate the old field.

* Deprecating fields: If you want to deprecate a field, avoid removing it from the schema entirely. Instead, you can mark it as deprecated using the [deprecated=true] option. This will generate a warning in the code during compilation, discouraging its use.

* Using optional fields: Protobuf fields are optional by default. This allows for more flexibility when evolving the schema, as you can add or remove fields without causing issues with existing serialized data.

* Using oneof: If you want to change a field's type to a completely different type or provide multiple mutually exclusive options, you can use the "oneof" construct. This allows you to define a set of alternative fields, of which only one can be set at a time. This can help maintain compatibility when evolving the schema, but requires more careful handling in the application code.

By following these best practices, you can evolve your Protobuf schema over time without breaking compatibility between different versions of your applications or data. However, it's essential to thoroughly test the changes to ensure that both new and old readers and writers can handle the evolved schema correctly.