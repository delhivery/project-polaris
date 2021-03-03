# Batching

## Definitions
 [Reference doc](https://docs.google.com/document/d/1nK2bXJrhQxhUIupDl_Y3pPaGmeH98mzDDnOrTrGR-fU)

## Objective
From a pool of load, resource and existing dispatches, combine containers into batches and recommend resource to serve that batch.

## Open Questions

- [ ] Define FE costing model
- [ ] How to reduce total distance travelled by FE?
- [ ] How to ensure FE can practically serve orders within slots?
- [ ] For HLD, should the pickup and delivery address both lie in FE servicable zone?
- [ ] How to consider existing dispatches while batching.
- [ ] Exhaustive list of triggers for batching?

## Input

- Resource
  - Costing
  - Capacity
  - Servicable zones
    - Green zones
    - Orange zones
  - Current Location
  - Available time slots
  - Capability

- Container
  - Pickup Location
    - Estimated location
    - Soft time slot
    - Hard time slot
  - Delivery Location
    - Estimated location
    - Soft time slot
    - Hard time slot
  - Capability

## Assumptions
- For a given batch and FE, inccured cost is known.
- FE's current location is not always known.
- FE can have multiple servicable zones.
- Estimated locations for container are below certain threshold.
- Capability is a hard constraint
- FE Max capacity is a hard constraint

## Optimization Priority
1. Minimize un-allocation with hard (preffered+buffer) slots 
2. Minimize cost
3. Maximize allocation within soft (preferred) slots
4. Maximum allocation of shipments in the green zone of an FE.
5. Minimize stem distance


## TODO
  - [ ] Define objectives for batching
  - [ ] use cases
  - [ ] Minimization
    - [ ] Maximize overall serviceability
    - [ ] Locations outside FE.PrefferedArea but inside FE.ServiceArea incur additional cost
    - [ ] Missing an order incurs cost basis Order.priority
    - [ ] Minimize overall cost
  - [ ] input arguments
  - [ ] Outcome