# Project Polaris

Specification for event driven dispatcher

## Overview

Delhivery has multiple dispatch models used to service first-mile, mid-mile, carting, returns, last-mile and hyperlocal deliveries. While field operators, vehicles and infrastructure used to address this demand are common, the interfaces, operational practices and business logic to handle these is individually customized.

This adds to the burden of the operational staff where they have to manage multiple applications and workflows for each respective business product.

We try to simplify the above class of problems by reimagining dispatch as a point to point service, where shipments have to be delivered from a source location to a target destination within a stipulated SLAs/time window.

In the current systems, the in-field activities are tightly coupled with the field activities, there is an overlap of the ops / business functionality (fm, lm etc) with the in-field tasks. One of the key objectives is to decouple these dependencies and model field apps to manage tasks irrespective of how they are administered

This specification aims to have a formal definition for all building blocks.


## Project Polaris Specification

  Spec can be found here:

||Latest Release|
|:---|:-----:|
| Core Specification |[master](https://github.com/delhivery/project-polaris/blob/main/spec.md)|

## Contribution guide

We would love to get feedback and improvements on this project. Please read how to [contribute](https://github.com/delhivery/project-polaris/blob/main/CONTRIBUTING.md) via issues and pull requests.

## Code of Conduct

This project adheres to a [code of conduct](https://github.com/delhivery/project-polaris/blob/main/CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code.

## License

[Apache 2.0](https://opensource.org/licenses/Apache-2.0)

Copyright (c) 2021-present, Delhivery Pvt Ltd


