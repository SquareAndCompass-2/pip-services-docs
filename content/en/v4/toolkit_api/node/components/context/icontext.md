---
type: docs
title: "IContext"
linkTitle: "IContext"
gitUrl: "https://github.com/pip-services4/pip-services4-node/tree/main/pip-services4-components-node"
description: > 
 Interface to specify execution context.

  
---

### Description
TODO: add description

### Instance Methods  

#### get
Adds parameters into this ConfigParams under a specified section.
Keys for the new parameters are appended with section dot prefix.

> `public` get(key: string): any

- **key**: string - a key of the element to get.
- **returns**: any - the value of the map element.


#### getTraceId
Gets a trace (correlation) id.

> `public` getTraceId(): string

- **returns**: string - a trace id or <code>null</code> if it is not defined.

#### getClient
Gets a client name.

> `public` getClient(): string

- **returns**: string - a client name or <code>null</code> if it is not defined.

#### getUser
Gets a reference to user object.

> `public` getUser(configParams: [ConfigParams](../../config/config_params)): [ConfigParams](../../config/config_params)

- **returns**: [ConfigParams](../../config/config_params) - a user reference or <code>null</code> if it is not defined.

### See also
- #### [Context](../context)