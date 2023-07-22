---
type: docs
title: "DefaultVaultFactory"
linkTitle: "DefaultVaultFactory"
gitUrl: "https://github.com/pip-services4/pip-services4-node/tree/main/pip-services4-vault-node"
description: > 
    Creates .
---

### Description


private _connectionResolver: ConnectionResolver = new ConnectionResolver();
private _credentialResolver: CredentialResolver = new CredentialResolver();


### Examples

```typescript
let credentialStore = new VaultCredentialStore();
credentialStore.open();
let credential = await credentialStore.lookup("123", "key1");
// Result: user=jdoe; pass=pass123
```
