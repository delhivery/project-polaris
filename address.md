# Dispatcher Resource Names (DRNs)

## Overview

Dispatcher resource names uniquely identify dispatcher resources. All activities require DRN to unambiguously determine resources or their instances across all of dispatcher.

## Format

The following is the general format of a DRN

```
drn::<service>::<tenant>::<resource_type>
drn::<service>::<tenant>::<resource_type>//<resource_id>
drn::<service>::<tenant>::<resource_type>//<resource_id>::<json_path>
```

### Service

The service in which the resource is located. Can be one of:

-   model
-   event
-   callback
-   lifecycle

### Tenant

The tenant in which the resource is located. Same as tenant_id provided by User Management System. Currently supported tenant:

-   delhivery

### Resource Type

The service namespace that identifies the Dispatcher component. For example, Package for Model, CollectCod for Event.

### Resource Id

A unique identifier for the instance of a given resource type. For example, waybill 2250112664712

## Samples

```
drn::model::delhivery::package
drn::event::delhivery::CollectCoD
drn::lifecycle::delhivery::B2CLifecycle
drn::model::delhivery::package//2250112664712
```

## Path in DRNs

Some DRNs support JSONPath to access additional metadata for a resource. For example, models support accessing specific metadata using JSONPath. Similarly, lifecycles support accessing guard conditions using JSONPath as well.

##### Package Model

```JSON
{
	"wbn": "2250112664712",
	"name": "Ambasta",
	"address": {
		"streetAddress": "892, Sector 40",
		"city": "Gurgaon",
		"zip": "122003"
	}
}
```

##### JSONPath accessor

```
drn::model::delhivery::package//2250112664712::address.streetAddress
```
