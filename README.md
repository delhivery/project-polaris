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
  - [Lifecycle](lifecycle.md)
  - [Interaction & Flow](interaction.md)
  - [Batching](batching.md)

# Introduction

For a point to point dispatch system, the goal is have a event driven approach. This means that our systems continuously wait for the occurrence of some external or internal event such as a mouse click, a button press, a time tick or an arrival of a data packet (streams/api). After recognizing the event, our systems react by performing the appropriate computation which may in turn trigger events for other internal software.

Models form the building blocks and each model has a lifecycle. eg: FE model will have a lifecycle with a set of states(create, activate, punch-in, punch-out etc).

An event may cause state changes in the lifecycle in combination with a function/callback. In such a case, the function/callback with the event amounts to a state transition

Each event leads to evaluation of lifecyle for validation of event (is the incoming event acceptable at current state of the lifecycle). Additionally, the lifecycle determines given the internal state and the event as to what function/callback has to be invoked

This document lays down the specification of a bootstrap library which provides the ability to register models, events & lifecycle and deploy it to run in an isolated environment.