# Lifecycle

## Overview

The lifecycle of any object can be thought of as a state machine such that each entity or each of its sub-entities is exactly always in one of a possible number of states and where there are well-defined conditional transitions between these states.

Business/Product can declare the lifecycle of each model in the system and events associated with each state of the lifecycle. The events can cause change in state of a model's lifecycle

## Registering a lifecycle

A lifecycle can be declared via a web UI. An example could be registering the lifecycle of a Field Executive. Each state can have event(s) associated with it.

![Lifecycle](https://user-images.githubusercontent.com/69619248/110305221-84c9e780-8022-11eb-8845-5a5465d9760c.jpeg)


## Capabilities

If a state or a series of states are put behind a flag, a new capability is created. And these states will be skipped if the model does not have capability set as true.


## Registering a capability

- TODO