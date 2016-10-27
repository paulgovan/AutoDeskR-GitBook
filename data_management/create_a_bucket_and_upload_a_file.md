## Create a Bucket and Upload a File {#create-a-bucket-and-upload-a-file}

The Data Management API provides a way to store and access data on the platform. Model files are hosted in the cloud and organized into buckets. To create a bucket, first get a token with the `bucket:create`, `bucket:read`, and `data:write` scopes.

```
resp <- getToken(id = Sys.getenv("client_id"), secret = Sys.getenv("client_secret"), 
            scope = "bucket:create bucket:read data:write")
myToken <- resp$content$access_token
```

Then use the `makeBucket()` function to create a bucket, where `bucket` is a name for the bucket.

```
resp <- makeBucket(token = myToken, bucket = "mybucket")
```

To check the status of a bucket:

```
resp <- checkBucket(token = myToken, bucket = "mybucket")
resp
```

Finally, to upload a file to the bucket, use the `uploadFile()` function, which returns an object containing the `bucketKey`, `objectId` (i.e. urn), `objectKey` (i.e. file name), `size`, `contentType` (i.e. “application/octet-stream”), `location` and other content information. Note the unique urn of the file and store it in `.Renviron` for future use.

```
resp <- uploadFile(file = system.file("inst/samples/aerial.dwg", package = "AutoDeskR"),
            token = myToken, bucket = "mybucket")
myUrn <- resp$content$objectId
```