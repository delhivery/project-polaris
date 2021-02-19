# Models

Data structure for payload. (Eg: FE model, Vehicle model)

## Overview

- TODO

## Supported Data Types

- `Boolean`: a boolean value of "true" or "false".
- `String`: a string of text. It may contain unicode characters
- `Integer`: .
- `Double`: .
- `Datetime`: ISO 8601 datetime format or utc timestamp.
- `null`: represents missing value. Accepts value as `null`.
- `Array`: list of ordered elements.
- `Object`: key value data. Value can be of any of the supported data types.

-  TODO: Datetime format, location, polygon etc

## Document Type Definition

Model attributes may have the following properties.

**Properties:**

- `type`: 
    description: Data Type
    required: true
    value: Refer supported data types
- `minLength`:
    description: minimum number of characters allowed
    required: false
    value: integer
- `maxLength`:
    description: maximum number of characters allowed
    required: false
    value: integer
- `pattern`:
    description: Regular expression to match a valid pattern
    required: false
    value: valid regex
- `enum`:
    description: Possible values of an attribute
    required: false
    value: Array<String>
- `required`:
    description: If the attribute is required for the model to be initialized
    required: true
    value: boolean

## Validate

  - TODO

## Deploy
  
  ```javascript
  Model.init(modelName: String, args)
  Model.deploy()
  ```

  Example;
  ```javascript
  Model.init("Vehicle", {
    "name": {
      "type": String,
      "required": true,
    }...
  })
  ```

  

## Registry

Model registry will provide a set of APIs for create data instances for the models declared (create, read, update, delete) operations on a particular model.

`uuid`: unique id
`args`: a valid model payload 


**Create**

```javascript
ModelName modelName = new Modelname()
modelName.create(uuid, args)
```

**Read**

```javascript
modelName.get(uuid)
```

**Set**

```javascript
modelName.set(model, data)
```

**Update**

```javascript
modelName.update(uuid, oldModel, newModel)
```
**Delete**

```javascript
modelName.delete(uuid)
```


