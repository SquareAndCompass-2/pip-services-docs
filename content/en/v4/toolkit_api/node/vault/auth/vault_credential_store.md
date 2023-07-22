---
type: docs
title: "VaultCredentialStore"
linkTitle: "VaultCredentialStore"
gitUrl: "https://github.com/pip-services4/pip-services4-node/tree/main/pip-services4-vault-node"
description: > 
    Credential store that keeps credentials in memory .
---

### Description
Credential store that keeps credentials in memory.
 * 
#### Configuration parameters
  
**connection(s):**                
**- discovery_key:**         (optional) a key to retrieve the connection from [[https://pip-services4-node.github.io/pip-services4-components-node/interfaces/connect.idiscovery.html IDiscovery]]     
**- host:**                  host name or IP address     
**- port:**                  port number     
**- uri:**                   resource URI or connection string with all parameters in it     
**- proxy_enable:**          enable proxy (default false)     
**- proxy_host:**            proxy host name     
**- proxy_port:**            proxy port number     
          
**credential(s):**     
**- store_key:**             key to retrieve parameters from credential store     
**- username:**              set user name for ldap and userpass auth type, role_id for approle and k8s auth type, cert_name for cert auth type     
**- password:**              user password for ldap and userpass auth type, secret_id for approle auth type, token for k8s and cert_name auth type     
**- auth_type:**             auth type (approle, ldap, userpass, k8s, cert) default - userpass     
**- file_cert:**             client certificate file for https mode     
**- file_key:**              client key file for https mode     
**- file_cacert:**           root CA cert path for https mode    
        
**options:**     
**- root_path:**             root path after the base URL     
**- timeout:**               default timeout in milliseconds (default: 5 sec)     
**- namespace:**             namespace (multi-tenancy) feature available on all Vault Enterprise versions          
  
 * @see [[ICredentialStore]]
 * @see [[CredentialParams]]
 * 
 * ### Example ###
 * 
 *     
 *     let credentialStore = new VaultCredentialStore();
 *     credentialStore.open();
 *     
 *     let credential = await credentialStore.lookup("123", "key1");
 *     // Result: user=jdoe; pass=pass123
 */
