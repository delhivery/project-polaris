# Callbacks

## Overview

Callbacks are fully stateless functions that can be invoked by events. Each callback is a function that is not bound to any identifier (class/model). They are akin to lambda or anonymous functions in any programming langauge.

Each callback function specifies event(s) that it can be invoked on.

## Definition

A callback is defined as a function that accepts an event E, and for each model of E, specializes itself to a function which accepts as arguments the model in E, E itself and returns a new object of the model type.

```ts
interface callbackReturn<Model M> {
	model: M;
	event?: Event;
};

const callbackFunction = <Model M, Event E>(const m: M, const e: E): callbackReturn<M> => {
	// user code here
};

type callback<M, E> = M extends Model ? callbackFunction<M, E> : () => {};

type Models<E> = {
	[M in keyof E]: callback<Event[M], Event>
}
```

## Usage

Since callbacks can mutate models, callbacks are the primary mechanism by which developers specify what operations have to occur for a given model and event.

##### Example
```ts
interface CoDCollectedEvent {
	models: [Package, FieldExecutive];
	amount: currency;
};

interface FELimitExceededEvent {
	models: [FieldExecutive];
};

const CoDCollectedCallbackPackage: callbackFunction<Package, CoDCollectedEvent> = (const pkg: Package, const event: CoDCollectedEvent) : callbackReturn<Package> {
	let updatedPackage: Package = pkg;

	if (pkg.field_executive === event.field_executive) {
		const excess = event.amount - pkg.cod_amount;

		if (excess >= 0) {
			updatedPackage.cod_excess = excess;
		}

		throw InsufficientCoDAmount();
	}

	return {model: updatedPacakge};
};

const CoDCollectedCallbackFieldExecutive: callbackFunction<Package, CoDCollectedEvent> = (const fe: FieldExecutive, const event: CoDCollectedEvent): callbackReturn<FieldExecutive> {
	let updatedExecutive: FieldExecutive = fe;
	fe.cod_collected += event.amout;

	if (fe.cod_collected > 10000)
		return {model: fe, event: FELimitExceededEvent(fe)};
	return {model: fe};
}
```