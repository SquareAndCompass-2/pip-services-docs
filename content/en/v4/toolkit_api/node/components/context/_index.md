---
type: docs
title: "Context"
linkTitle: "Context"
no_list: true
gitUrl: "https://github.com/pip-services4/pip-services4-node/tree/main/pip-services4-components-node"
description: >
    Contains a simple object that defines the context of execution. For various 
    logging functions we need to know what source we are logging from – what is 
    the processes name, what the process is/does. 
---
---

**Important information**
- This package is useful for various logging functions where it is necessary to know things like: what source we are logging from, what is 
    the process name, or what the process is/does.  


<div class="module-body"> 

<br>

### Interfaces


#### [IContext](iconfigurable)
Interface to specify execution context.

#### [IReconfigurable](ireconfigurable)
An interface to set configuration parameters to an object.  
It is similar to [IConfigurable](iconfigurable) interface, but emphasises the fact
that **configure()** method can be called more than once to change an object configuration
in runtime.

<br>

### Classes

#### [Context](configurable)
Basic implementation of an execution context.

#### [ContextInfo](context_info)
Context information component that provides detail information
about execution context: container or/and process.

Most often ContextInfo is used by logging and performance counters
to identify source of the collected logs and metrics.

#### [ContextResolver](context_resolver)
Context resolver that processes context and extracts values from there.

#### [DefaultInfoFactory](default_info_factory)
Creates information components by their descriptors.

</div>
