## Translate a File into OBJ Format {#translate-a-file-into-obj-format}

To translate a supported file into OBJ format, first get an access token with the `data:read` and `data:write` scopes. Note that only certain types of files can be translated into OBJ format. To find out which types of files can be translated into what format, see the [Supported Translation Formats Table](https://developer.autodesk.com/en/docs/model-derivative/v2/overview/supported-translations/).

```
resp <- getToken(id = Sys.getenv("client_id"), secret = Sys.getenv("client_secret"), 
            scope = "data:read data:write")
myToken <- resp$content$access_token
```

The platform requires that the urn of the file be Base-64 encoded. Fortunately, the `jsonlite` package has a nifty function for encoding the urn.

```
# Here myUrn was generated from the 'uploadFile()' function
myEncodedUrn <- jsonlite::base64_enc(myUrn) 
```

Then, translate the file into OBJ format:

```
resp <- translateObj(urn = myEncodedUrn, token = myToken)
```

To check the status of the translation process:

```
resp <- checkFile(urn = myEncodedUrn, token = myToken)
resp
```

To download an OBJ file locally, we need the output `urn` of the translated file, which is different than the `urn` of the source file. In this case, use the `getOutputUrn()` function, which returns an object containing the `result`, output `urn` and other activity information.

```
resp <- getOutputUrn(urn = myUrn, token = Sys.getenv("token"))
resp
```

Depending on the type of file and translation process, the response may contain multiple output `urn`s for different file types (e.g. obj, svf, png). In order to find the correct OBJ file, look through the `resp` object for a `urn` than ends in “.obj” and assign this `urn` to `myOutputUrn`, which should look similar to the following:

```
myOutputUrn < "urn:adsk.viewing:fs.file:dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6bW9kZWxkZXJpdmF0aXZlL0E1LmlhbQ/output/geometry/bc3339b2-73cd-4fba-9cb3-15363703a354.obj"
```

Finally, to download the OBJ file locally:

```
myEncodedOutputUrn = jsonlite::base64_enc(myOutputUrn)
resp <- downloadFile(urn = myEncodedUrn, output_urn <- myEncodedOutputUrn, token = myToken)
```