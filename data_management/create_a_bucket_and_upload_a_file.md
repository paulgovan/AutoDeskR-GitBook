## Create a Bucket and Upload a File {#create-a-bucket-and-upload-a-file}

To create a bucket, first get a token with the `bucket:create, bucket:read, and data:write scopes.`

```
resp <- getToken(id = Sys.getenv("client_id"), secret = Sys.getenv("client_secret"), 
            scope = "bucket:create bucket:read data:write")
myToken <- resp$content$access_token
myToken
[1] "422vSsW9XMizreWsq0OQX8tgwCpC"
```

Then use the `makeBucket() function to create a bucket, where bucket is a name for the bucket.`

```
resp <- makeBucket(token = myToken, bucket = "mybucket")
```

To check the status of a bucket:

```
resp <- checkBucket(token = myToken, bucket = "mybucket")
resp
$content
$content$access_token
[1] "br22Mq9H5B2WTWQ1a0DljmzXSndk"

$content$token_type
[1] "Bearer"

$content$expires_in
[1] 86399


$path
[1] "https://developer.api.autodesk.com/authentication/v1/authenticate"

$response
Response [https://developer.api.autodesk.com/authentication/v1/authenticate]
  Date: 2016-11-14 01:12
  Status: 200
  Content-Type: application/json;charset=utf-8
  Size: 90 B
{"access_token":"br22Mq9H5B2WTWQ1a0DljmzXSndk","token_type":"Bearer","expires_in":86399}

attr(,"class")
[1] "getToken"
```

Finally, to upload a file to the bucket, use the `uploadFile() function, which returns an object containing the bucketKey, objectId (i.e. urn), objectKey (i.e. file name), size, contentType (i.e. “application/octet-stream”), location and other content information. Note the unique urn of the file and store it in .Renviron for future use.`

```
resp <- uploadFile(file = system.file("samples/aerial.dwg", package = "AutoDeskR"),
            token = myToken, bucket = "mybucket")
myUrn <- resp$content$objectId
myUrn
[1] "urn:adsk.objects:os.object:crazybucket/aerial.dwg"
```



