## Prepare a File for the Viewer {#prepare-a-file-for-the-viewer}

To prepare a file for the online viewer, first get an access token with the `data:read` and `data:write` scopes.

```
resp <- getToken(id = Sys.getenv("client_id"), secret = Sys.getenv("client_secret"), 
            scope = "data:read data:write")
myToken <- resp$content$access_token
```

Nex, encode the urn using the `jsonlite::base64_enc()` function.

```
myEncodedUrn <- jsonlite::base64_enc(myUrn)
```

Then, translate the file into SVF format:

```
resp <- translateSvf(urn = myEncodedUrn, token = myToken)
```

To check the status of the translation process:

```
resp <- checkFile(urn = myEncodedUrn, token = myToken)
resp
```

Finally, embed the urn of the file in the viewer, which is described in the **Viewer** section.