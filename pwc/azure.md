az login --service-principal --username appID --password PASSWORD --tenant tenantID


az login --service-principal --username "8506c53d-7643-4ddc-8974-fc57eef01412" --password "t01esgO9lnQkY7gygVVD9OJodiDByTGs" --tenant "977dc802-db6d-4932-866e-f7b91483cf32"

az storage account list

az storage account list | jq -r '.[].name'


az storage blob directory show -c MyContainer -d MyDirectoryPath --account-name MyStorageAccount

az storage account show -n staesgdecoddev37160



export AZURE_STORAGE_ACCOUNT=staesgdecoddev37160
export AZURE_STORAGE_KEY=inQOHhYFetbrvDKqWSISFF6+lP3atYheKw3vbGk7RkUQdKvbYvvrIM2pqfZPW6zfu7cfOMd4JT1BFzNNsmrGzA==

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