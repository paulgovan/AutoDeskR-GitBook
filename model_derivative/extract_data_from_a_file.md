## Extract Data from a File {#extract-data-from-a-file}

To extract data from a file, follow the steps in the previous section for getting a token with the `data:read` and `data:write` scopes, encoding the `urn` of the file using the `jsonlite::base64_enc()` function, and translating the file into SVF format using the `translateSvf()` function. Next, retrieve metadata for a file using the `getMetadata()` function, which returns an object with the `type`, `name`, and `guid` of the file. Note the `guid` and store it in `.Renviron`.

```
resp <- getMetadata(urn = myEncodedUrn, token = myToken)
myGuid <- resp$content$data$metadata[[1]]$guid
```

To get the object tree of a model, use the `getObjectTree()` function.

```
resp <- getObjectTree(guid = myGuid, urn = myEncodedUrn, token = myToken)
resp
```

To extract data from the model, use the `getData()` function.

```
resp <- getData(guid = myGuid, urn = myEncodedUrn, token = myToken)
```