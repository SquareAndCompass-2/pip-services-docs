---
type: docs
title: "AzureFunctionClient"
linkTitle: "AzureFunctionClient"
gitUrl: "https://github.com/pip-services4/pip-services4-go/tree/main/pip-services4-azure-go"
description: >
    Abstract client that calls Azure Functions.
---

### Description
When making calls "cmd" parameter determines which what action shall be called, while
other parameters are passed to the action itself.


#### Configuration parameters

- **connections**:                   
    - **uri**: (optional) full connection string or use protocol, app_name and function_name to build
    - **protocol**: (optional) connection protocol
    - **app_name**: (optional) Azure Function application name
    - **function_name**: (optional) Azure Function name
- **options**:
    - **retries**: number of retries (default: 3)
    - **connect_timeout**: connection timeout in milliseconds (default: 10 sec)
    - **timeout**: invocation timeout in milliseconds (default: 10 sec)
- **credentials**:
    - **auth_code**: Azure Function auth code if use custom authorization provide empty string

#### References
- **\*:logger:\*:\*:1.0** - (optional) [ILogger](../../../observability/log/ilogger) components to pass log messages.
- **\*:counters:\*:\*:1.0** - (optional) [ICounters](../../../observability/count/icounters) components to pass collected measurements.
- **\*:discovery:\*:\*:1.0** - (optional) [IDiscovery](../../../config/connect/idiscovery) services to resolve connections.
- **\*:credential-store:\*:\*:1.0** - (optional) Credential stores to resolve credentials.

### Contructors

#### NewAzureFunctionClient
Creates new instance of AzureFunctionClient

> NewAzureFunctionClient() [*AzureFunctionClient]()

### Fields

<span class="hide-title-link">

#### Client
The HTTP client.
> **Client**: *http.Client

### ConnectTimeout
The connection timeout in milliseconds.
> **ConnectTimeout**: int = 10000

### Connection
The Azure Function connection parameters
> **Connection**: [*AzureFunctionConnectionParams](../../connect/azure_function_connection_params)

### ConnectionResolver
The connection resolver.
> **ConnectionResolver**: [*AzureFunctionConnectionResolver](../../connect/azure_function_connection_resolver)

### Counters
Performance counters.
> **Counters**: [*CompositeCounters](../../../observability/count/composite_counters)

### DependencyResolver
Dependencies resolver.
> **DependencyResolver**: [*DependencyResolver](../../../components/refer/dependency_resolver)

### Headers
The default headers to be added to every request.
> **Headers**: [*cdata.StringValueMap](../../../commons/data/string_value_map)

### Logger
Logger.
> **Logger**: [*CompositeLogger](../../../observability/log/composite_logger)

### Timeout
The invocation timeout in milliseconds.
> **Timeout**: int = 10000

### Tracer
The tracer.
> **Tracer**: [*CompositeTracer](../../../observability/trace/composite_tracer)

### Uri
The remote service uri which is calculated on open.
> **Uri**: string


</span>


### Instance methods

#### AddFilterParams
AddFilterParams method are adds filter parameters (with the same name as they defined)
to invocation parameter map.

> (c [*AzureFunctionClient]()) AddFilterParams(params [*cdata.StringValueMap](../../../commons/data/string_value_map), filter [*cdata.FilterParams](../../../data/query/filter_params)) [*cdata.StringValueMap](../../../commons/data/string_value_map)

- **params**: [*cdata.StringValueMap](../../../commons/data/string_value_map) - invocation parameters.
- **filter**: [*cdata.FilterParams](../../../data/query/filter_params) - (optional) filter parameters
- **returns**: [*cdata.StringValueMap](../../../commons/data/string_value_map)

#### AddPagingParams
AddPagingParams method are adds paging parameters (skip, take, total) to invocation parameter map.

> (c [*AzureFunctionClient]()) AddPagingParams(params [*cdata.StringValueMap](../../../commons/data/string_value_map), paging [*cdata.PagingParams](../../../commons/data/paging_params)) [*cdata.StringValueMap](../../../commons/data/string_value_map)

- **params**: [*cdata.StringValueMap](../../../commons/data/string_value_map) - invocation parameters.
- **paging**: [*cdata.FilterParams](../../../commons/data/filter_params) - (optional) paging parameters.
- **returns**: [*cdata.StringValueMap](../../../commons/data/string_value_map) - invocation parameters with added paging parameters.

#### Call
Calls a Azure Function action.

> (c [*AzureFunctionClient]()) Call(ctx context.Context, cmd string, context [IContext](../../../components/context/icontext),
	args [*cdata.AnyValueMap](../../../commons/data/any_value_map)) (*http.Response, error)

- **ctx**: context.Context - operation context.
- **cmd**: string - an action name to be called.
- **context**: [IContext](../../../components/context/icontext) - (optional) a context to trace execution through a call chain.
- **args**: [*cdata.AnyValueMap](../../../commons/data/any_value_map) - (optional) action parameters.
- **returns**: (*http.Response, error) - action result.

#### Close
Closes component and frees used resources.

> (c [*AzureFunctionClient]()) Close(ctx context.Context, context [IContext](../../../components/context/icontext)) error 

- **ctx**: context.Context - operation context.
- **context**: [IContext](../../../components/context/icontext) - (optional) a context to trace execution through a call chain.
- **returns**: error - error if not closed.


#### Configure
Configures component by passing configuration parameters.

> (c [*AzureFunctionClient]()) Configure(ctx context.Context, config [*ConfigParams](../../../components/config/config_params))

- **ctx**: context.Context - operation context.
- **config**: [*ConfigParams](../../../components/config/config_params) - configuration parameters to be set.


#### Instrument
Adds instrumentation to log calls and measure call time.
It returns a CounterTiming object that is used to end the time measurement.

> (c [*AzureFunctionClient]()) Instrument(ctx context.Context, context [IContext](../../../components/context/icontext), name string) [*InstrumentTiming](../../../rpc/trace/instrument_timing)

- **ctx**: context.Context - operation context.
- **context**: [IContext](../../../components/context/icontext) - (optional) a context to trace execution through a call chain.
- **name**: string - a method name.
- **return**: [*InstrumentTiming](../../../rpc/trace/instrument_timing) - object to end the time measurement.


#### IsOpen
Checks if the component is opened.

> (c [*AzureFunctionClient]()) IsOpen() bool

- **returns**: bool - true if the component has been opened and false otherwise.

#### Open
Opens the component.

> (c [*AzureFunctionClient]()) Open(ctx context.Context, context [IContext](../../../components/context/icontext)) error

- **ctx**: context.Context - operation context.
- **context**: [IContext](../../../components/context/icontext) - (optional) a context to trace execution through a call chain.
- **returns**: error - error if not opened.

#### SetReferences
Sets references to dependent components.

> (c [*AzureFunctionClient]()) SetReferences(ctx context.Context, references [IReferences](../../../components/refer/ireferences))

- **ctx**: context.Context - operation context.
- **references**: [IReferences](../../../components/refer/ireferences) - references to locate the component dependencies. 



### Examples

```go
type MyAzureFunctionClient struct {
	*clients.AzureFunctionClient
}

func NewMyAzureFunctionClient() *MyAzureFunctionClient {
	return &MyAzureFunctionClient{
		AzureFunctionClient: azureclient.NewAzureFunctionClient(),
	}
}

func (c *MyAzureFunctionClient) GetData(ctx context.Context, context IContext, id string) MyData {
	timing := c.Instrument(ctx, context, "myclient.get_data")

	response, err := c.Call(ctx, "get_data", context, data.NewAnyValueMapFromTuples("id", dummyId))

	defer timing.EndTiming(ctx, err)
	return rpcclients.HandleHttpResponse[MyData](response, context)
}

...

client := NewMyAzureFunctionClient()
client.Configure(config.NewConfigParamsFromTuples(
	"connection.uri", "http://myapp.azurewebsites.net/api/myfunction",
	"connection.protocol", "http",
	"connection.app_name", "myapp",
	"connection.function_name", "myfunction"
	"credential.auth_code", "XXXX"
result := client.GetData("123", "1")
```


### See also
- #### [AzureFunction](../../containers/azure_function/)
- #### [CommandableAzureFunctionClient](../commandable_azure_function_client)
