# Events

## Overview

An event is something that happens that can affect the system. An event refers to a type of occurrence rather than any concrete instance of that occurrence. For example,  a scan is an event on a container, but each individual scan (GI/Outbound) is not an event but a concrete instance of that occurrence.

An event can have associated parameters, allowing the event instance to convey not only the occurrence of an incidence of interest but also the quantitative information regarding that occurrence. For example, a scan event generated on scanning a barcode has associated parameters that convey the participants involved.

An event instance outlives the instantaneous occurrence that generated the event and might convey this occurrence to one or more state machines. Once generated, the event instance goes through a processing lifecycle that can consist of up to three stages. First the event instance is received when it is accepted and awaits processing (API Invocation, Queues), then the event is dispatched to the state machine, at which point it becomes the current event. Finally it is consumed when the state machine finishes processing the event. A consumed event instance is no longer available for processing.

## Definition

Events are objects which describe some action that has occured along with associated data. Events don't directly update models. Functions/Callbacks carry out operations in response to events which may or not may not produce a new version of the model.

The system generating events is decoupled from the system consuming the events.



