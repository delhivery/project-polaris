# Lifecycle

## Overview

The lifecycle of any object can be thought of as a state machine such that each entity or each of its sub-entities is exactly always in one of a possible number of states and where there are well-defined conditional transitions between these states.

Business/Product can declare the lifecycle of each model in the system and events associated with each state of the lifecycle. The events may cause change in state of a model's lifecycle

A lifecycle has to be declared for every model. A model's lifecycle is created by chaining together atomic workflows.

## Event and Lifecycle

When an event is generated, the system figures out what's the current state of the model is and validates if the incoming event can be trigged in current state. If yes then the corresponding task for the event is executed which may cause a change in state of the model.

An event can be valid for multiple states of a lifecycle. For example:
'cancelOrder' event will have to be attached to all states of a lifecycle if cancellation if to be allowed at all times during the lifecycle of an order.

## Registering a lifecycle

A lifecycle can be declared via a web UI. An example could be registering the lifecycle of a Field Executive.

![Lifecycle](https://user-images.githubusercontent.com/69619248/110305221-84c9e780-8022-11eb-8845-5a5465d9760c.jpeg)


## Capabilities

If one or more atomic workflow in a model's lifecycle are put behind a flag, a new capability is created. And these states will be skipped if the model does not have capability set as true. So a lifecycle with no capabilities will execute all atomic workflows in it.

## Registering a capability

The lifecycle UI panel will allow product/biz to define capabilities.