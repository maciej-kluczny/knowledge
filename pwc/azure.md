# Authenticate to Azure
az login --service-principal --username appID --password PASSWORD --tenant tenantID

# Azure Storage

## list accounts
az storage account list
az storage account list | jq -r '.[].name'


az storage blob directory show -c MyContainer -d MyDirectoryPath --account-name MyStorageAccount

az storage account show -n staesgdecoddev37160


mkluczny@ubuntu  ~  az storage container list | jq
[
{
"deleted": null,
"encryptionScope": {
"defaultEncryptionScope": "$account-encryption-key",
"preventEncryptionScopeOverride": false
},
"immutableStorageWithVersioningEnabled": false,
"metadata": null,
"name": "exports",
"properties": {
"etag": "\"0x8DA10C26D1C4506\"",
"hasImmutabilityPolicy": false,
"hasLegalHold": false,
"lastModified": "2022-03-28T13:54:06+00:00",
"lease": {
"duration": null,
"state": "available",
"status": "unlocked"
},
"publicAccess": null
},
"version": null
}
]

# Azure KeyVault

## key vaults

    $ az keyvault list

    [
        {
        "id": "/subscriptions/beb34245-719d-45e8-9d85-805ad7563bd4/resourceGroups/rgdecoddev37160/providers/Microsoft.KeyVault/vaults/kv01decoddev37160",
        "location": "westeurope",
        "name": "kv01decoddev37160",
        "resourceGroup": "rgdecoddev37160",
        "tags": {},
        "type": "Microsoft.KeyVault/vaults"
        }
    ]

### List secrets of given vault-name 

    az keyvault secret list --vault-name kv01decoddev37160 | jq -r '.[].name'

    ...
    timescaledb-credentials
    timescaledb-postgres-credentials-secret
    trino-catalog-properties-test
    vault-recovery-0

```json
az keyvault secret list --vault-name kv01decoddev37160 | jq -r '.[] | select( .name == "esg-data-system-export-storage-account-sas")'
        
{
  "attributes": {
    "created": "2022-03-28T14:09:29+00:00",
    "enabled": true,
    "expires": null,
    "notBefore": null,
    "recoveryLevel": "Recoverable+Purgeable",
    "updated": "2022-03-28T14:09:29+00:00"
  },
  "contentType": "",
  "id": "https://kv01decoddev37160.vault.azure.net/secrets/esg-data-system-export-storage-account-sas",
  "managed": null,
  "name": "esg-data-system-export-storage-account-sas",
  "tags": {}
}
```
### Getting secret

```json
az keyvault secret show --vault-name kv01decoddev37160 --name esg-data-system-export-storage-account-sas

{
  "attributes": {
    "created": "2022-03-28T14:09:29+00:00",
    "enabled": true,
    "expires": null,
    "notBefore": null,
    "recoveryLevel": "Recoverable+Purgeable",
    "updated": "2022-03-28T14:09:29+00:00"
  },
  "contentType": "",
  "id": "https://kv01decoddev37160.vault.azure.net/secrets/esg-data-system-export-storage-account-sas/d3a0d74fd1924bb6ad5e5bda969a7e5d",
  "kid": null,
  "managed": null,
  "name": "esg-data-system-export-storage-account-sas",
  "tags": {},
  "value": "some secret value :)"}

```