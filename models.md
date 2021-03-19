# Models

## Definition

The dispatcher system operates over data sets, events and states. These data sets can be classified into discrete categories, each of which can be represented as a model. Common properties for models are:
- Each model supports CRUD operations over instances of the model
- Each model stores corresponding metadata defining the attributes of the model
- Each valid model has a unique name and address drn:model:<tenant>:<model_name>
- Each valid model instance has a unique address arn:model:<tenant>:<model_name>/<model_id>


## Structure

Each model is represented via a JSONSchema. Additionally, each model has two reserved fields always associated with it, namely `id` and `version`. These are used by the dispatcher internally to manage operations over model instances.

Each model can be defined as class which implements the following interface
```
interface Model {
	id: string;
	version: datetime;
	[key: string]: ValueType;
};
```


#### Minimal Schema
[minimal-schema]: 
```json
{
	"$id": "drn:model:<model_name>",
	"title": "<model_name>",
	"description": "Model description",
	"type": "object",
	"required": ["id", "version"],
	"additionalProperties": true,
	"properties": {
		"id": {
			"type": "string",
			"description": "Unique identifier for a model instance. An id is of the form <model_name>:<uuid>",
			"pattern": "^([\\w\\.]+)::([\\dA-Fa-f]{8}-[\\dA-Fa-f]{4}-[\\dA-Fa-f]{4}-[\\dA-Fa-f]{4}-[\\dA-Fa-f]{12})?$",
			"example": "delhivery.transportation.package::19176a5b-8361-42a2-9f32-b368fb3b46ce"
		},
		"version": {
			"type": "number",
			"description": "Version of the document - timestamp of last update, resolution microseconds",
		}
	},
	"id": "string",
	"version": "string"
}
```


## Supported [data-types]:

```
enum ValueType {
	string,
	number,
	datetime,
	geopoly,
	geopoint,
	currency,
	boolean,
	list,
	map,
};
```