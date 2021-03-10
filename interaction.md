# Interaction Flow

## Setup

- Register Models
- Register Events and associate models with it
- Register Event callback and obtain stubs for execution tasks
- Declare lifecycle of all models
- Define capabilities in the lifecycle
- Execution Tasks are implmented and deployed

## Execution

- Generate one of the registered events
- The systems fetches lifecycles of all the models associated with the event and figures out the current state of these lifecycles
- If the event is associated with the current state of the lifecycles, then corresponding tasks are executed.
- Tasks produces new image of the respective models
- A database transaction is created for the above and commited to DB.
- Updated model values are pushed to a stream for all applications to consume
