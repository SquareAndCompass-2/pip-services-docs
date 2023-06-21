---
type: docs
title: "DataDogMetricsClient"
linkTitle: "DataDogMetricsClient"
gitUrl: "https://github.com/pip-services4/pip-services4-node/tree/main/pip-services4-datadog-node"
description: >
    REST client for DataDog metrics.


---

**Extends:** [RestClient](../../../http/clients/rest_client)

### Description

The DataDogMetricsClient class allows you to create a REST client for DataDog metrics.



### Constructors
Creates an instance of this class.

> `public` constructor(config?: [ConfigParams](../../../components/config/config_params))

- **config**: [ConfigParams](../../../components/config/config_params) - configuration parameters


### Instance methods

#### configure
Configures the component by passing its configuration parameters. 

> `public` configure(config: [ConfigParams](../../../components/config/config_params)): void

- **config**: [ConfigParams](../../../components/config/config_params) - configuration parameters to be set.

#### open
Opens the component.

> `public` open(context: [Context](../../../components/context/context)): Promise\<void\>

- **context**: [Context](../../../components/context/context) - (optional) transaction id used to trace execution through the call chain.

#### sendMetrics
Sends the given metrics.

> `public` sendMetrics(context: [Context](../../../components/context/context), metrics: [DataDogMetric[]](../datadog_metric)): Promise\<void\>

- **context**: [Context](../../../components/context/context) - (optional) Basic implementation of an execution context.
- **messages**: [DataDogMetric[]](../datadog_metric) - messages

#### setReferences
Sets references to dependent components.

> `public` setReferences(references: [IReferences](../../../components/refer/ireferences)): void

- **references**: [IReferences](../../../components/refer/ireferences) - references to locate the component's dependencies.
