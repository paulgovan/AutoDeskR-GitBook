## Prepare a File for the Viewer {#prepare-a-file-for-the-viewer}

To prepare a file for the online viewer, first get an access token with the `data:read` and `data:write` scopes.

```
resp <- getToken(id = Sys.getenv("client_id"), secret = Sys.getenv("client_secret"), 
            scope = "data:read data:write")
myToken <- resp$content$access_token
```

Next, encode the urn using the `jsonlite::base64_enc()` function.

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
$content
$content$type
[1] "manifest"

$content$hasThumbnail
[1] "true"

$content$status
[1] "success"

$content$progress
[1] "complete"

$content$region
[1] "US"

$content$urn
[1] "dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6Y3JhenlidWNrZXQvYWVyaWFsLmR3Zw"

$content$version
[1] "1.0"

$content$derivatives
$content$derivatives[[1]]
$content$derivatives[[1]]$name
[1] "aerial.dwg"

$content$derivatives[[1]]$hasThumbnail
[1] "true"

$content$derivatives[[1]]$status
[1] "success"

$content$derivatives[[1]]$progress
[1] "complete"

$content$derivatives[[1]]$outputType
[1] "svf"

$content$derivatives[[1]]$children
$content$derivatives[[1]]$children[[1]]
$content$derivatives[[1]]$children[[1]]$guid
[1] "6882be48-6626-5238-d3df-94e9f0a0019d"

$content$derivatives[[1]]$children[[1]]$type
[1] "geometry"

$content$derivatives[[1]]$children[[1]]$role
[1] "2d"

$content$derivatives[[1]]$children[[1]]$name
[1] "2D View"

$content$derivatives[[1]]$children[[1]]$viewableID
[1] "Model"

$content$derivatives[[1]]$children[[1]]$status
[1] "success"

$content$derivatives[[1]]$children[[1]]$progress
[1] "complete"

$content$derivatives[[1]]$children[[1]]$hasThumbnail
[1] "true"

$content$derivatives[[1]]$children[[1]]$children
$content$derivatives[[1]]$children[[1]]$children[[1]]
$content$derivatives[[1]]$children[[1]]$children[[1]]$guid
[1] "02420873-d6c0-4317-c8c0-fac198f45a66"

$content$derivatives[[1]]$children[[1]]$children[[1]]$type
[1] "resource"

$content$derivatives[[1]]$children[[1]]$children[[1]]$mime
[1] "image/png"

$content$derivatives[[1]]$children[[1]]$children[[1]]$resolution
$content$derivatives[[1]]$children[[1]]$children[[1]]$resolution[[1]]
[1] 100

$content$derivatives[[1]]$children[[1]]$children[[1]]$resolution[[2]]
[1] 56


$content$derivatives[[1]]$children[[1]]$children[[1]]$role
[1] "thumbnail"

$content$derivatives[[1]]$children[[1]]$children[[1]]$status
[1] "success"

$content$derivatives[[1]]$children[[1]]$children[[1]]$urn
[1] "urn:adsk.viewing:fs.file:dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6Y3JhenlidWNrZXQvYWVyaWFsLmR3Zw/output/aerial-Model_100.png"


$content$derivatives[[1]]$children[[1]]$children[[2]]
$content$derivatives[[1]]$children[[1]]$children[[2]]$guid
[1] "718e990d-a609-2df2-477e-be2c09be8a65"

$content$derivatives[[1]]$children[[1]]$children[[2]]$type
[1] "resource"

$content$derivatives[[1]]$children[[1]]$children[[2]]$mime
[1] "image/png"

$content$derivatives[[1]]$children[[1]]$children[[2]]$resolution
$content$derivatives[[1]]$children[[1]]$children[[2]]$resolution[[1]]
[1] 200

$content$derivatives[[1]]$children[[1]]$children[[2]]$resolution[[2]]
[1] 113


$content$derivatives[[1]]$children[[1]]$children[[2]]$role
[1] "thumbnail"

$content$derivatives[[1]]$children[[1]]$children[[2]]$status
[1] "success"

$content$derivatives[[1]]$children[[1]]$children[[2]]$urn
[1] "urn:adsk.viewing:fs.file:dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6Y3JhenlidWNrZXQvYWVyaWFsLmR3Zw/output/aerial-Model_200.png"


$content$derivatives[[1]]$children[[1]]$children[[3]]
$content$derivatives[[1]]$children[[1]]$children[[3]]$guid
[1] "dec8987f-2fda-609c-5318-05e40494b0aa"

$content$derivatives[[1]]$children[[1]]$children[[3]]$type
[1] "resource"

$content$derivatives[[1]]$children[[1]]$children[[3]]$mime
[1] "image/png"

$content$derivatives[[1]]$children[[1]]$children[[3]]$resolution
$content$derivatives[[1]]$children[[1]]$children[[3]]$resolution[[1]]
[1] 400

$content$derivatives[[1]]$children[[1]]$children[[3]]$resolution[[2]]
[1] 226


$content$derivatives[[1]]$children[[1]]$children[[3]]$role
[1] "thumbnail"

$content$derivatives[[1]]$children[[1]]$children[[3]]$status
[1] "success"

$content$derivatives[[1]]$children[[1]]$children[[3]]$urn
[1] "urn:adsk.viewing:fs.file:dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6Y3JhenlidWNrZXQvYWVyaWFsLmR3Zw/output/aerial-Model_400.png"


$content$derivatives[[1]]$children[[1]]$children[[4]]
$content$derivatives[[1]]$children[[1]]$children[[4]]$guid
[1] "01bd0431-8828-21c9-a0ec-36f50afb449a"

$content$derivatives[[1]]$children[[1]]$children[[4]]$type
[1] "resource"

$content$derivatives[[1]]$children[[1]]$children[[4]]$mime
[1] "application/autodesk-f2d"

$content$derivatives[[1]]$children[[1]]$children[[4]]$role
[1] "graphics"

$content$derivatives[[1]]$children[[1]]$children[[4]]$status
[1] "success"

$content$derivatives[[1]]$children[[1]]$children[[4]]$urn
[1] "urn:adsk.viewing:fs.file:dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6Y3JhenlidWNrZXQvYWVyaWFsLmR3Zw/output/5262c71a-bc16-086f-95be-f582ae8d2065_f2d/primaryGraphics.f2d"


$content$derivatives[[1]]$children[[2]]
$content$derivatives[[1]]$children[[2]]$guid
[1] "149d819a-f59a-9de3-b42d-15f1269b41df"

$content$derivatives[[1]]$children[[2]]$type
[1] "geometry"

$content$derivatives[[1]]$children[[2]]$role
[1] "3d"

$content$derivatives[[1]]$children[[2]]$name
[1] "3D Views"

$content$derivatives[[1]]$children[[2]]$status
[1] "success"

$content$derivatives[[1]]$children[[2]]$viewableID
[1] "Model-3D"

$content$derivatives[[1]]$children[[2]]$progress
[1] "complete"

$content$derivatives[[1]]$children[[2]]$hasThumbnail
[1] "true"

$content$derivatives[[1]]$children[[2]]$children
$content$derivatives[[1]]$children[[2]]$children[[1]]
$content$derivatives[[1]]$children[[2]]$children[[1]]$guid
[1] "e30bd031-d13a-a976-9153-78100829986a"

$content$derivatives[[1]]$children[[2]]$children[[1]]$type
[1] "resource"

$content$derivatives[[1]]$children[[2]]$children[[1]]$urn
[1] "urn:adsk.viewing:fs.file:dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6Y3JhenlidWNrZXQvYWVyaWFsLmR3Zw/output/dwg.svf"

$content$derivatives[[1]]$children[[2]]$children[[1]]$role
[1] "graphics"

$content$derivatives[[1]]$children[[2]]$children[[1]]$mime
[1] "application/autodesk-svf"

$content$derivatives[[1]]$children[[2]]$children[[1]]$status
[1] "success"


$content$derivatives[[1]]$children[[2]]$children[[2]]
$content$derivatives[[1]]$children[[2]]$children[[2]]$guid
[1] "6dd2f8f5-1714-c783-86a9-a7bba161c2be"

$content$derivatives[[1]]$children[[2]]$children[[2]]$type
[1] "view"

$content$derivatives[[1]]$children[[2]]$children[[2]]$role
[1] "3d"

$content$derivatives[[1]]$children[[2]]$children[[2]]$name
[1] "Initial"

$content$derivatives[[1]]$children[[2]]$children[[2]]$camera
$content$derivatives[[1]]$children[[2]]$children[[2]]$camera[[1]]
[1] 133.5476

$content$derivatives[[1]]$children[[2]]$children[[2]]$camera[[2]]
[1] 35.41636

$content$derivatives[[1]]$children[[2]]$children[[2]]$camera[[3]]
[1] 12.06831

$content$derivatives[[1]]$children[[2]]$children[[2]]$camera[[4]]
[1] 2.10204

$content$derivatives[[1]]$children[[2]]$children[[2]]$camera[[5]]
[1] 26.13582

$content$derivatives[[1]]$children[[2]]$children[[2]]$camera[[6]]
[1] 1.631315

$content$derivatives[[1]]$children[[2]]$children[[2]]$camera[[7]]
[1] 0

$content$derivatives[[1]]$children[[2]]$children[[2]]$camera[[8]]
[1] 0

$content$derivatives[[1]]$children[[2]]$children[[2]]$camera[[9]]
[1] 1

$content$derivatives[[1]]$children[[2]]$children[[2]]$camera[[10]]
[1] 2.193931

$content$derivatives[[1]]$children[[2]]$children[[2]]$camera[[11]]
[1] 0.960293

$content$derivatives[[1]]$children[[2]]$children[[2]]$camera[[12]]
[1] 66.62182

$content$derivatives[[1]]$children[[2]]$children[[2]]$camera[[13]]
[1] 0


$content$derivatives[[1]]$children[[2]]$children[[3]]
$content$derivatives[[1]]$children[[2]]$children[[3]]$guid
[1] "3c9d59fb-3147-a570-4103-1a766ac78d9b"

$content$derivatives[[1]]$children[[2]]$children[[3]]$type
[1] "view"

$content$derivatives[[1]]$children[[2]]$children[[3]]$role
[1] "3d"

$content$derivatives[[1]]$children[[2]]$children[[3]]$name
[1] "RenderView"

$content$derivatives[[1]]$children[[2]]$children[[3]]$camera
$content$derivatives[[1]]$children[[2]]$children[[3]]$camera[[1]]
[1] 94.66933

$content$derivatives[[1]]$children[[2]]$children[[3]]$camera[[2]]
[1] 32.67141

$content$derivatives[[1]]$children[[2]]$children[[3]]$camera[[3]]
[1] 8.981309

$content$derivatives[[1]]$children[[2]]$children[[3]]$camera[[4]]
[1] 2.10204

$content$derivatives[[1]]$children[[2]]$children[[3]]$camera[[5]]
[1] 26.13582

$content$derivatives[[1]]$children[[2]]$children[[3]]$camera[[6]]
[1] 1.631315

$content$derivatives[[1]]$children[[2]]$children[[3]]$camera[[7]]
[1] 0

$content$derivatives[[1]]$children[[2]]$children[[3]]$camera[[8]]
[1] 0

$content$derivatives[[1]]$children[[2]]$children[[3]]$camera[[9]]
[1] 1

$content$derivatives[[1]]$children[[2]]$children[[3]]$camera[[10]]
[1] 1.372233

$content$derivatives[[1]]$children[[2]]$children[[3]]$camera[[11]]
[1] 0.960293

$content$derivatives[[1]]$children[[2]]$children[[3]]$camera[[12]]
[1] 66.62182

$content$derivatives[[1]]$children[[2]]$children[[3]]$camera[[13]]
[1] 0


$content$derivatives[[1]]$children[[2]]$children[[4]]
$content$derivatives[[1]]$children[[2]]$children[[4]]$guid
[1] "4611ad76-727c-4b97-838e-8a89377bb8ab"

$content$derivatives[[1]]$children[[2]]$children[[4]]$type
[1] "resource"

$content$derivatives[[1]]$children[[2]]$children[[4]]$urn
[1] "urn:adsk.viewing:fs.file:dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6Y3JhenlidWNrZXQvYWVyaWFsLmR3Zw/output/dwg.svf.png01_thumb_400x400.png"

$content$derivatives[[1]]$children[[2]]$children[[4]]$resolution
$content$derivatives[[1]]$children[[2]]$children[[4]]$resolution[[1]]
[1] 400

$content$derivatives[[1]]$children[[2]]$children[[4]]$resolution[[2]]
[1] 400


$content$derivatives[[1]]$children[[2]]$children[[4]]$mime
[1] "image/png"

$content$derivatives[[1]]$children[[2]]$children[[4]]$role
[1] "thumbnail"


$content$derivatives[[1]]$children[[2]]$children[[5]]
$content$derivatives[[1]]$children[[2]]$children[[5]]$guid
[1] "b44bb91a-9640-4ba4-8d66-9b4c00232b44"

$content$derivatives[[1]]$children[[2]]$children[[5]]$type
[1] "resource"

$content$derivatives[[1]]$children[[2]]$children[[5]]$urn
[1] "urn:adsk.viewing:fs.file:dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6Y3JhenlidWNrZXQvYWVyaWFsLmR3Zw/output/dwg.svf.png01_thumb_200x200.png"

$content$derivatives[[1]]$children[[2]]$children[[5]]$resolution
$content$derivatives[[1]]$children[[2]]$children[[5]]$resolution[[1]]
[1] 200

$content$derivatives[[1]]$children[[2]]$children[[5]]$resolution[[2]]
[1] 200


$content$derivatives[[1]]$children[[2]]$children[[5]]$mime
[1] "image/png"

$content$derivatives[[1]]$children[[2]]$children[[5]]$role
[1] "thumbnail"


$content$derivatives[[1]]$children[[2]]$children[[6]]
$content$derivatives[[1]]$children[[2]]$children[[6]]$guid
[1] "7118b62f-e6a6-4cda-845d-37ff0d4cec71"

$content$derivatives[[1]]$children[[2]]$children[[6]]$type
[1] "resource"

$content$derivatives[[1]]$children[[2]]$children[[6]]$urn
[1] "urn:adsk.viewing:fs.file:dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6Y3JhenlidWNrZXQvYWVyaWFsLmR3Zw/output/dwg.svf.png01_thumb_100x100.png"

$content$derivatives[[1]]$children[[2]]$children[[6]]$resolution
$content$derivatives[[1]]$children[[2]]$children[[6]]$resolution[[1]]
[1] 100

$content$derivatives[[1]]$children[[2]]$children[[6]]$resolution[[2]]
[1] 100


$content$derivatives[[1]]$children[[2]]$children[[6]]$mime
[1] "image/png"

$content$derivatives[[1]]$children[[2]]$children[[6]]$role
[1] "thumbnail"


$path
[1] "https://developer.api.autodesk.com/modelderivative/v2/designdata/dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6Y3JhenlidWNrZXQvYWVyaWFsLmR3Zw==/manifest"

$response
Response [https://developer.api.autodesk.com/modelderivative/v2/designdata/dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6Y3JhenlidWNrZXQvYWVyaWFsLmR3Zw==/manifest]
  Date: 2016-11-14 01:37
  Status: 200
  Content-Type: application/json; charset=utf-8
  Size: 3.29 kB


attr(,"class")
[1] "checkFile"
```

Finally, embed the urn of the file in the viewer, which is described in the [Viewer](https://paulgovan.gitbooks.io/autodeskr/content/viewer.html) section.