# Models

## Definition

The dispatcher system operates over data sets, events and states. These data sets can be classified into discrete categories, each of which can be represented as a model. Common properties for models are:
- Each model supports CRUD operations over instances of the model
- Each model stores corresponding metadata defining the attributes of the model
- Each valid model has a unique name and address drn::model::<tenant>::<model_name>
- Each valid model instance has a unique address drn::model::<tenant>::<model_name>//<model_id>


## Structure

Each model is represented via a JSONSchema. Additionally, each model has two reserved fields always associated with it, namely `id` and `version`. These are used by the dispatcher internally to manage operations over model instances.

Each model can be defined as class which implements the following interface
```ts
interface Model {
	id: string;
	version: datetime;
	props: JsonSchema;
};
```


#### Sample Schema
```json
{
	"id": "drn::model::<tenant>::<model_name>",
	"version": 1234,
	"props": {
		"title": "<model_name>",
		"description": "Model description",
		"type": "object",
		"required": ["oid", "client"],
		"additionalProperties": true,
		"properties": {
			"oid": {
				"type": "string",
				"description": "Unique order id",
				"pattern": "^([\\w\\.]+)::([\\dA-Fa-f]{8}-[\\dA-Fa-f]{4}-[\\dA-Fa-f]{4}-[\\dA-Fa-f]{4}-[\\dA-Fa-f]{12})?$"
			},
			"client": {
				"type": "string",
				"description": "Client name",
			}
		}
	}
}
```


## Supported [data-types]:

```ts
enum ValueType {
	string,
	number,
	geopoint,
	currency,
	boolean,
	array,
	object,
};
```

## Custom Definitions:

- curreny
```json
{
	type: "object",
	properties: {
		code: {
			type: "string",
			description: "Currency code",
			minLength: 3,
			maxLength: 3,
			pattern: "^\\w{3}$",
		},
		amt: {
			type: "number",
			description: "Amount of currency",
			minimum: 0,
		},
		den: {
			type: "number",
			description: "Denomination of amount",
			minimum: 0,
			maximum: 2,
		},
	},
};
```

- geopoint

```json
{
	type: "object",
	properties: {
		lat: {
			type: "number",
			description: "Latitude",
			minimum: -90,
			maximum: 90,
		},
		lon: {
			type: "number",
			description: "Longitude",
			minimum: -180,
			maximum: 180,
		},
		acc: {
			type: "number",
			description: "Accuracy in meter",
			minimum: 0,
		},
	},
};
```