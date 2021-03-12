# Models

## Definition

Models are the building blocks of the system. (Eg: FE, Vehicle, Package Model).

Any object which has meta data can be declared as new model in the system. Model does not maintain any kind of relationship (one to one, one to many etc). Relationships are to be maintained at application level.

## Registration

Developers register their model schema in the system via model registration service. A model schema can be updated by adding new properties or removing old ones. Modifying data types of properties is not supported.

## Model Instance

Instance of a registered model commited to the database.

## Supported Data Types

- `Boolean`: a boolean value of "true" or "false".
- `String`: a string of text. It may contain unicode characters
- `Integer`: represents mathamatical integers
- `Double`: 64-bit precision floating point
- `Datetime`: ISO 8601 datetime format or utc timestamp.
- `Array`: list of ordered elements.
- `Object`: key value data. Value can be of any of the supported data types.
