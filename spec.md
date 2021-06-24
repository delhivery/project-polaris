## Table of Contents

  - [Introduction](#introduction)
  - [Dispatcher Resource Names](address.md)
  - [Models](models.md)
  - [Events](events.md)
  - [Callbacks](callbacks.md)
  - [Lifecycle](lifecycle.md)

# Introduction

For a point to point dispatch system, the goal is have a event driven approach. This means that our systems continuously wait for the occurrence of some external or internal event such as a mouse click, a button press, a time tick or an arrival of a data packet (streams/api). After recognizing the event, our systems react by performing the appropriate computation which may in turn trigger events for other internal software.

Models form the building blocks and each model has a lifecycle. eg: FE model will have a lifecycle with a set of states(create, activate, punch-in, punch-out etc).

An event may cause state changes in the lifecycle in combination with a function/callback. In such a case, the function/callback with the event amounts to a state transition

Each event leads to evaluation of lifecycle for validation of event (is the incoming event acceptable at current state of the lifecycle). Additionally, the lifecycle determines given the internal state and the event as to what function/callback has to be invoked

This document lays down the specification of a bootstrap library which provides the ability to register models, events & lifecycle and deploy it to run in an isolated environment.