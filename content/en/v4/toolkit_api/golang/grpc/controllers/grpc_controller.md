---
type: docs
title: "GrpcService"
linkTitle: "GrpcService"
gitUrl: "https://github.com/pip-services4/pip-services4-go/tree/main/pip-services4-grpc-go"
description: > 
    Abstract service that receives remote calls via the GRPC protocol.

---

### Description

The GrpcService class allows you to create services that receive remote calls via the GRPC protocol.

#### Configuration parameters
- **dependencies**:   
    - **endpoint**: override for GRPC Endpoint dependency    
    - **controller**: override for Controller dependency    
- **connection(s)**:    
    - **discovery_key**: (optional) key to retrieve the connection from [IDiscovery](../../../config/connect/idiscovery)    
    - **protocol**: connection protocol: http or https    
    - **host**: host name or IP address    
    - **port**: port number   
    - **uri**: resource URI or connection string with all parameters in it    
- **credentials**:   
    - **ssl_key_file**: SSL private key in PEM    
    - **ssl_crt_file**: SSL certificate in PEM    
    - **ssl_ca_file**: certificate authorities (root cerfiticates) in PEM    
 
#### References

- **\*:discovery:\*:\*:1.0** - (optional) [IDiscovery](../../../config/connect/idiscovery) services
- **\*:logger:\*:\*:1.0** - (optional) [ILogger](../../../observability/log/ilogger) components to pass log messages
- **\*:counters:\*:\*:1.0** - (optional) [ICounters](../../../observability/count/icounters) components to pass collected measurementsand as specified by the counter's source.
 


### Constructors

InheritGrpcService methods are creates new instance NewGrpcService

> InheritGrpcService(overrides IGrpcServiceOverrides, serviceName string) [*GrpcService]()

- **overrides**: IGrpcServiceOverrides - a reference to child class that overrides virtual methods
- **serviceName**: string - service name from XYZ.pb.go, set "" for use default gRPC commandable protobuf


### Fields

<span class="hide-title-link">

#### Endpoint
The GRPC endpoint that exposes this service.
> **Endpoint**: [*GrpcEndpoint](../grpc_endpoint)

#### DependencyResolver
The dependency resolver.
> **DependencyResolver**: [*DependencyResolver](../../../refer/dependency_resolver)

#### Logger
The logger.
> **Logger**: [*CompositeLogger](../../../observability/log/composite_logger)

#### Counters
The Counters counters.
> **Counters**: [*CompositeCounters](../../../components/count/composite_counters)

#### Tracer
The tracer.
> **Tracer**: [*CompositeTracer](../../../observability/trace/composite_tracer)

</span>



### Methods


#### Close
Closes the component and frees used resources.

> (c [*GrpcService]()) Close(context [IContext](../../../components/context/icontext)) (err error)

- **context**: [IContext](../../../components/context/icontext) - (optional) a context to trace execution through a call chain.
- **returns**: (err error) - error or nil no errors occured.


#### Configure
Configures component by passing configuration parameters.

> (c [*GrpcService]()) Configure(ctx context.Context, config [*cconf.ConfigParams](../../../components/config/config_params))

- **ctx**: context.Context - operation context.
- **config**: [*cconf.ConfigParams](../../../components/config/config_params) - configuration parameters to be set.


#### IsOpen
Checks if the component is open.

> (c [*GrpcService]()) IsOpen() bool

- **returns**: bool -True if the endpoint is open with an actively listening GRPC server.


#### Instrument
Adds instrumentation to log calls and measures call time. 
It returns a CounterTiming object that is used to end the time measurement.

> (c [*GrpcService]()) Instrument(ctx context.Context, context [IContext](../../../components/context/icontext), name string) [*rpcserv.InstrumentTiming](../../../rpc/trace/instrument_timing)

- **ctx**: context.Context - operation context.
- **context**: [IContext](../../../components/context/icontext) - (optional) a context to trace execution through a call chain.
- **name**: string - method name.
- **returns**: [*rpcserv.InstrumentTiming](../../../rpc/trace/instrument_timing) -Timing object to end the time measurement.


#### Open
Opens the component.

> (c [*GrpcService]()) Open(ctx context.Context, context [IContext](../../../components/context/icontext)) (err error)

- **ctx**: context.Context - operation context.
- **context**: [IContext](../../../components/context/icontext) - (optional) a context to trace execution through a call chain.
- **returns**: (err error) - error or nil no errors occured.

#### Register
Register method are registers all service routes in HTTP endpoint.

> (c [*GrpcService]()) Register()


#### RegisterUnaryInterceptor
Registers a middleware for methods in GRPC endpoint.

> (c [*GrpcService]()) RegisterUnaryInterceptor(action func(ctx context.Context, req any, info *grpc.UnaryServerInfo, handler grpc.UnaryHandler) (any, error) )

- **action**: func(ctx context.Context, req any, info *grpc.UnaryServerInfo, handler grpc.UnaryHandler) (any, error) - an action function that is called when middleware is invoked.


#### RegisterCommandableMethod

RegisterCommandableMethod method are registers a commandable method in c objects GRPC server (service) by the given name.

> (c [*GrpcService]()) RegisterCommandableMethod(method string, schema [*cvalid.Schema](../../../data/validate/schema), action func(ctx context.Context, context [IContext](../../../components/context/icontext), data [*crun.Parameters](../../../components/exec/parameters)) (result any, err error))

- **method**: string - the GRPC method name.
- **schema**: [*cvalid.Schema](../../../data/validate/schema) - validation schema to validate received parameters.
- **action**: func(ctx context.Context, context [IContext](../../../components/context/icontext), data [*crun.Parameters](../../../components/exec/parameters)) (result any, err error) - action function that is called when operation is invoked.


#### SetReferences
Sets references to dependent components.

> (c [*GrpcService]()) SetReferences(ctx context.Context, references [cref.IReferences](../../../components/refer/ireferences))

- **ctx**: context.Context - operation context.
- **references**: [cref.IReferences](../../../components/refer/ireferences) - references to locate the component dependencies.


#### UnsetReferences
Unsets (clears) previously set references to dependent components.

> (c [*GrpcService]()) UnsetReferences()


### Examples

```go
type MyGrpcService struct {
   *GrpcService
   controller IMyController
}
...

func NewMyGrpcService() *MyGrpcService {
	c := NewMyGrpcService{}
	c.GrpcService = grpcservices.NewGrpcService("Mydata.Mydatas")
	c.GrpcService.IRegisterable = &c
	c.numberOfCalls = 0
	c.DependencyResolver.Put(context.Context(), "controller", cref.NewDescriptor("mygroup", "controller", "*", "*", "*"))
	return &c
}

func (c*MyGrpcService) SetReferences(ctx context.Context, references: IReferences) {
	c.GrpcService.SetReferences(references);
	resolv, err := c.DependencyResolver.GetOneRequired("controller")
	if err == nil && resolv != nil {
	    c.controller = resolv.(grpctest.IMyController)
	    return
	}
	panic("Can't resolve 'controller' reference")
}

func (c*MyGrpcService) Register() {
	protos.RegisterMyDataServer(c.Endpoint.GetServer(), c)
	...
}

service := NewMyGrpcService();
service.Configure(ctx, cconf.NewConfigParamsFromTuples(
    "connection.protocol", "http",
    "connection.host", "localhost",
    "connection.port", 8080,
))
service.SetReferences(ctx, cref.NewReferencesFromTuples(
   cref.NewDescriptor("mygroup","controller","default","default","1.0"), controller
))

err := service.Open(ctx, "123")
if  err == nil {
   fmt.Println("The GRPC service is running on port 8080");
}
```



