---
type: docs
title: "Clients"
linkTitle: "Clients"
no_list: true
gitUrl: acure
description: >
    This package contains classes used to create different types of clients.
---
---

<div class="module-body"> 

### Classes

#### [DirectClient](direct_client)
Abstract client that calls a controller directly in the same memory space.

It is used when multiple microservices are deployed in a single container (monolyth)
and communication between them can be done by direct calls rather than through 
the network.


</div>
