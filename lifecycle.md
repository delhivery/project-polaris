# Lifecycle

## Overview

The lifecycle of any object can be thought of as a state machine such that each entity or each of its sub-entities is exactly always in one of a possible number of states and where there are well-defined conditional transitions between these states.

Business/Product can declare the lifecycle of each model in the system and events associated with each state of the lifecycle. The events may cause change in state of a model's lifecycle

## Definition

A lifecycle is a suquence of events, states and transitions which allows us to dicate what happens to a model from inception to termination in our system.

## Event and Lifecycle

An event causes the evaluation of lifecycle to validate if the said event is acceptable at the current state of the lifecycle or not. And if the event is acceptable, lifecycle will determine which function to invoke based on it's internal state

An event can be valid for multiple states of a lifecycle. For example:
'cancelOrder' event will have to be attached to all states of a lifecycle if cancellation if to be allowed at all times during the lifecycle of an order.

## Registering a lifecycle

A lifecycle can be declared via a web UI. An example could be registering the lifecycle of a Field Executive.

![Lifecycle](https://user-images.githubusercontent.com/69619248/110305221-84c9e780-8022-11eb-8845-5a5465d9760c.jpeg)


## Capabilities

If one or more atomic workflow in a model's lifecycle are put behind a flag, a new capability is created. And these states will be skipped if the model does not have capability set as true. So a lifecycle with no capabilities will execute all atomic workflows in it.

## Registering a capability

The lifecycle UI panel will allow product/biz to define capabilities.