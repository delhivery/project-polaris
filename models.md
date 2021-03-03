# Models

Data structure for payload. (Eg: FE model, Vehicle model)

## Overview

Each model has a lifecycle. A lifecycle of a mdoel is collection of atomic workflows chained together. Individual model owners can register their models and difine it's lifecycle.

## Supported Data Types

- `Boolean`: a boolean value of "true" or "false".
- `String`: a string of text. It may contain unicode characters
- `Integer`: represents mathamatical integers
- `Double`: 64-bit precision floating point
- `Datetime`: ISO 8601 datetime format or utc timestamp.
- `Array`: list of ordered elements.
- `Object`: key value data. Value can be of any of the supported data types.

TODO: Datetime format, location, polygon etc

## Document Type Definition

Model attributes may have the following properties.

**Properties:**

Properties in addition to standard json-schema

- `nullable`:
  - `description`: Define if this property can be null
  - `required`: false
  - `valueType`: boolean
  - `default`: false

## Build & Deploy

```javascript
model = ModelRegistry.build(uniqueModelName, customJsonSchema);
model.deploy();
```

Example:

```javascript
vehicleModel = ModelRegistry.build("Vehicle", {
    ...customJsonSchema
  }
})
vehicleModel.deploy()

```

## Validate

```javascript
model = ModelRegistry.fetch(uniqueModelName);
model.validate(args);
```

Example:

```javascript
vehicleModel = ModelRegistry.fetch("Vehicle");
vehicleModel.validate(args);
```

## Instantiate Model

Set of APIs for create data instances for the models declared (create, read, update, delete) operations on a particular model.

`uuid`: unique id
`args`: a valid model payload

**Create**

```javascript
model = ModelRegistry.fetch(uniqueModelName);
instance = model.create(uuid, args);
```

Example:

```javascript
vehicleModel = ModelRegistry.fetch("Vehicle");
vehicle = vehicleModel.create(uuid, args);
```

**Read**

```javascript
model = ModelRegistry.fetch(uniqueModelName);
instance = model.get(uuid);
```

Example:

```javascript
vehicleModel = ModelRegistry.fetch("Vehicle");
vehicle = vehicleModel.get(uuid);
```

**Update**

```javascript
model = ModelRegistry.fetch(uniqueModelName);
instance = model.update(uuid, args);
```

Example:

```javascript
vehicleModel = ModelRegistry.fetch("Vehicle");
vehicle = vehicleModel.update(uuid, args);
```

**Create or Update**

```javascript
model = ModelRegistry.fetch(uniqueModelName);
instance = model.createOrUpdate(uuid, args);
```

Example:

```javascript
vehicleModel = ModelRegistry.fetch("Vehicle");
vehicle = vehicleModel.createOrUpdate(uuid, args);
```

**Delete**

```javascript
model = ModelRegistry.fetch(uniqueModelName);
model.delete(uuid);
```

Example:

```javascript
vehicleModel = ModelRegistry.fetch("Vehicle");
vehicleModel.delete(uuid);
```
