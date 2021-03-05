# Project Polaris

Specification for Dispatch Allocation Service

## Overview

Delhivery has multiple dispatch models used to service first-mile, mid-mile, carting, returns, last-mile and hyperlocal deliveries. While field operators, vehicles and infrastructure used to address this demand are common, the interfaces, operational practices and business logic to handle these is individually customized.

This adds to the burden of the operational staff where they have to manage multiple applications and workflows for each respective business product.

We try to simplify the above class of problems by reimaging dispatch as a point to point service, where shipments have to be delivered from a source location to a target destination within a stipulated SLAs/time window.

In the current systems, the in-field activities are tightly coupled with the field activities, there is an overlap of the ops / business functionality (fm, lm etc) with the in-field tasks. One of the key objectives is to decouple these dependencies and model field apps to manage tasks irrespective of how they are administered

This specification aims to have a formal definition for all building blocks.


## Table of Contents

  - [Introduction](#introduction)
  - [Models](models.md)
  - [Events](events.md)
  - Capabilities [TODO]
  - Model Lifecycle & Event [TODO]
  - [Batching](batching.md)

# Introduction

For a point to point dispatch system, the goal is have a event driven approach. This means that our systems continuously wait for the occurrence of some external or internal event such as a mouse click, a button press, a time tick or an arrival of a data packet (streams/api). After recognizing the event, our systems react by performing the appropriate computation which may in turn trigger events for other internal software.


Models form the building blocks and each model has a lifecycle. eg: FE model will have a lifecycle with a set of states(create, activate, punchin, punch out etc).

An event will cause state changes in the lifecycle of a model.

Each event can trigger lifecycles of models it is associated with and leads to execution of tasks required for that particular event.

This document lays down the specification of a bootstrap library which governs the workflows and capabilities of different parts of point to point dispatch system.