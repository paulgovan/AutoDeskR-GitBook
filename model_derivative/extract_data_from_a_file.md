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
$content
$content$data
$content$data$type
[1] "objects"

$content$data$objects
$content$data$objects[[1]]
$content$data$objects[[1]]$objectid
[1] 24

$content$data$objects[[1]]$name
[1] "Model"

$content$data$objects[[1]]$objects
$content$data$objects[[1]]$objects[[1]]
$content$data$objects[[1]]$objects[[1]]$objectid
[1] 354

$content$data$objects[[1]]$objects[[1]]$name
[1] "3D Solids (5)"

$content$data$objects[[1]]$objects[[1]]$objects
$content$data$objects[[1]]$objects[[1]]$objects[[1]]
$content$data$objects[[1]]$objects[[1]]$objects[[1]]$objectid
[1] 351

$content$data$objects[[1]]$objects[[1]]$objects[[1]]$name
[1] "Box (4)"

$content$data$objects[[1]]$objects[[1]]$objects[[1]]$objects
$content$data$objects[[1]]$objects[[1]]$objects[[1]]$objects[[1]]
$content$data$objects[[1]]$objects[[1]]$objects[[1]]$objects[[1]]$objectid
[1] 117

$content$data$objects[[1]]$objects[[1]]$objects[[1]]$objects[[1]]$name
[1] "Solid [183]"


$content$data$objects[[1]]$objects[[1]]$objects[[1]]$objects[[2]]
$content$data$objects[[1]]$objects[[1]]$objects[[1]]$objects[[2]]$objectid
[1] 127

$content$data$objects[[1]]$objects[[1]]$objects[[1]]$objects[[2]]$name
[1] "Solid [191]"


$content$data$objects[[1]]$objects[[1]]$objects[[1]]$objects[[3]]
$content$data$objects[[1]]$objects[[1]]$objects[[1]]$objects[[3]]$objectid
[1] 131

$content$data$objects[[1]]$objects[[1]]$objects[[1]]$objects[[3]]$name
[1] "Solid [195]"


$content$data$objects[[1]]$objects[[1]]$objects[[1]]$objects[[4]]
$content$data$objects[[1]]$objects[[1]]$objects[[1]]$objects[[4]]$objectid
[1] 163

$content$data$objects[[1]]$objects[[1]]$objects[[1]]$objects[[4]]$name
[1] "Solid [20F]"


$content$data$objects[[1]]$objects[[1]]$objects[[2]]
$content$data$objects[[1]]$objects[[1]]$objects[[2]]$objectid
[1] 352

$content$data$objects[[1]]$objects[[1]]$objects[[2]]$name
[1] "Sphere (1)"

$content$data$objects[[1]]$objects[[1]]$objects[[2]]$objects
$content$data$objects[[1]]$objects[[1]]$objects[[2]]$objects[[1]]
$content$data$objects[[1]]$objects[[1]]$objects[[2]]$objects[[1]]$objectid
[1] 149

$content$data$objects[[1]]$objects[[1]]$objects[[2]]$objects[[1]]$name
[1] "Solid [1DA]"


$content$data$objects[[1]]$objects[[2]]
$content$data$objects[[1]]$objects[[2]]$objectid
[1] 355

$content$data$objects[[1]]$objects[[2]]$name
[1] "Surfaces (1)"

$content$data$objects[[1]]$objects[[2]]$objects
$content$data$objects[[1]]$objects[[2]]$objects[[1]]
$content$data$objects[[1]]$objects[[2]]$objects[[1]]$objectid
[1] 353

$content$data$objects[[1]]$objects[[2]]$objects[[1]]$name
[1] "Planar (1)"

$content$data$objects[[1]]$objects[[2]]$objects[[1]]$objects
$content$data$objects[[1]]$objects[[2]]$objects[[1]]$objects[[1]]
$content$data$objects[[1]]$objects[[2]]$objects[[1]]$objects[[1]]$objectid
[1] 142

$content$data$objects[[1]]$objects[[2]]$objects[[1]]$objects[[1]]$name
[1] "Surface [1C1]"


$path
[1] "https://developer.api.autodesk.com/modelderivative/v2/designdata/dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6Y3JhenlidWNrZXQvYWVyaWFsLmR3Zw==/metadata/e30bd031-d13a-a976-9153-78100829986a"

$response
Response [https://developer.api.autodesk.com/modelderivative/v2/designdata/dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6Y3JhenlidWNrZXQvYWVyaWFsLmR3Zw==/metadata/e30bd031-d13a-a976-9153-78100829986a]
  Date: 2016-11-14 01:49
  Status: 200
  Content-Type: application/json; charset=utf-8
  Size: 559 B


attr(,"class")
[1] "getObjectTree"
```

To extract data from the model, use the `getData()` function.

```
resp <- getData(guid = myGuid, urn = myEncodedUrn, token = myToken)
resp
$content
$content$data
$content$data$type
[1] "properties"

$content$data$collection
$content$data$collection[[1]]
$content$data$collection[[1]]$objectid
[1] 24

$content$data$collection[[1]]$name
[1] "Model"

$content$data$collection[[1]]$properties
$content$data$collection[[1]]$properties$Name
[1] "*Model_Space"

$content$data$collection[[1]]$properties$Usage
[1] 1

$content$data$collection[[1]]$properties$elementId
[1] "1F"

$content$data$collection[[1]]$properties$type
[1] "AcDbBlockTableRecord"


$content$data$collection[[2]]
$content$data$collection[[2]]$objectid
[1] 354

$content$data$collection[[2]]$name
[1] "3D Solids (5)"

$content$data$collection[[2]]$properties
$content$data$collection[[2]]$properties$elementId
[1] "3D Solids"

$content$data$collection[[2]]$properties$type
[1] "3D Solids"


$content$data$collection[[3]]
$content$data$collection[[3]]$objectid
[1] 351

$content$data$collection[[3]]$name
[1] "Box (4)"

$content$data$collection[[3]]$properties
$content$data$collection[[3]]$properties$elementId
[1] "Box"

$content$data$collection[[3]]$properties$type
[1] "Box"


$content$data$collection[[4]]
$content$data$collection[[4]]$objectid
[1] 117

$content$data$collection[[4]]$name
[1] "Solid [183]"

$content$data$collection[[4]]$properties
$content$data$collection[[4]]$properties$elementId
[1] "183"

$content$data$collection[[4]]$properties$type
[1] "AcDb3dSolid"

$content$data$collection[[4]]$properties$`3D Visualization`
$content$data$collection[[4]]$properties$`3D Visualization`$Material
[1] "Bronze - Satin 1"

$content$data$collection[[4]]$properties$`3D Visualization`$`Shadow Display`
[1] "Casts and Receives shadows"


$content$data$collection[[4]]$properties$General
$content$data$collection[[4]]$properties$General$Color
[1] "ByLayer"

$content$data$collection[[4]]$properties$General$Layer
[1] "0"

$content$data$collection[[4]]$properties$General$Linetype
[1] "ByLayer"

$content$data$collection[[4]]$properties$General$`Linetype scale`
[1] 1

$content$data$collection[[4]]$properties$General$Lineweight
[1] "ByLayer"

$content$data$collection[[4]]$properties$General$`Plot style`
[1] "ByColor"

$content$data$collection[[4]]$properties$General$Transparency
[1] "ByLayer"


$content$data$collection[[4]]$properties$Geometry
$content$data$collection[[4]]$properties$Geometry$Height
[1] 7.69588

$content$data$collection[[4]]$properties$Geometry$Length
[1] 9.161039

$content$data$collection[[4]]$properties$Geometry$Rotation
[1] 0

$content$data$collection[[4]]$properties$Geometry$`Solid type`
[1] "Box"

$content$data$collection[[4]]$properties$Geometry$Width
[1] 11.15553


$content$data$collection[[4]]$properties$`Solid History`
$content$data$collection[[4]]$properties$`Solid History`$`Record History`
[1] 1

$content$data$collection[[4]]$properties$`Solid History`$`Show History`
[1] 0


$content$data$collection[[4]]$properties$`__viewable_in__`
$content$data$collection[[4]]$properties$`__viewable_in__`$viewable_in
$content$data$collection[[4]]$properties$`__viewable_in__`$viewable_in[[1]]
[1] "Model-3D"

$content$data$collection[[4]]$properties$`__viewable_in__`$viewable_in[[2]]
[1] "Model"


$content$data$collection[[5]]
$content$data$collection[[5]]$objectid
[1] 127

$content$data$collection[[5]]$name
[1] "Solid [191]"

$content$data$collection[[5]]$properties
$content$data$collection[[5]]$properties$elementId
[1] "191"

$content$data$collection[[5]]$properties$type
[1] "AcDb3dSolid"

$content$data$collection[[5]]$properties$`3D Visualization`
$content$data$collection[[5]]$properties$`3D Visualization`$Material
[1] "Plate - Blue"

$content$data$collection[[5]]$properties$`3D Visualization`$`Shadow Display`
[1] "Casts and Receives shadows"


$content$data$collection[[5]]$properties$General
$content$data$collection[[5]]$properties$General$Color
[1] "ByLayer"

$content$data$collection[[5]]$properties$General$Layer
[1] "0"

$content$data$collection[[5]]$properties$General$Linetype
[1] "ByLayer"

$content$data$collection[[5]]$properties$General$`Linetype scale`
[1] 1

$content$data$collection[[5]]$properties$General$Lineweight
[1] "ByLayer"

$content$data$collection[[5]]$properties$General$`Plot style`
[1] "ByColor"

$content$data$collection[[5]]$properties$General$Transparency
[1] "ByLayer"


$content$data$collection[[5]]$properties$Geometry
$content$data$collection[[5]]$properties$Geometry$Height
[1] 7.69588

$content$data$collection[[5]]$properties$Geometry$Length
[1] 9.161039

$content$data$collection[[5]]$properties$Geometry$Rotation
[1] 0

$content$data$collection[[5]]$properties$Geometry$`Solid type`
[1] "Box"

$content$data$collection[[5]]$properties$Geometry$Width
[1] 11.15553


$content$data$collection[[5]]$properties$`Solid History`
$content$data$collection[[5]]$properties$`Solid History`$`Record History`
[1] 1

$content$data$collection[[5]]$properties$`Solid History`$`Show History`
[1] 0


$content$data$collection[[5]]$properties$`__viewable_in__`
$content$data$collection[[5]]$properties$`__viewable_in__`$viewable_in
$content$data$collection[[5]]$properties$`__viewable_in__`$viewable_in[[1]]
[1] "Model-3D"

$content$data$collection[[5]]$properties$`__viewable_in__`$viewable_in[[2]]
[1] "Model"


$content$data$collection[[6]]
$content$data$collection[[6]]$objectid
[1] 131

$content$data$collection[[6]]$name
[1] "Solid [195]"

$content$data$collection[[6]]$properties
$content$data$collection[[6]]$properties$elementId
[1] "195"

$content$data$collection[[6]]$properties$type
[1] "AcDb3dSolid"

$content$data$collection[[6]]$properties$`3D Visualization`
$content$data$collection[[6]]$properties$`3D Visualization`$Material
[1] "Plate - Riveted Flat Gray"

$content$data$collection[[6]]$properties$`3D Visualization`$`Shadow Display`
[1] "Casts and Receives shadows"


$content$data$collection[[6]]$properties$General
$content$data$collection[[6]]$properties$General$Color
[1] "ByLayer"

$content$data$collection[[6]]$properties$General$Layer
[1] "0"

$content$data$collection[[6]]$properties$General$Linetype
[1] "ByLayer"

$content$data$collection[[6]]$properties$General$`Linetype scale`
[1] 1

$content$data$collection[[6]]$properties$General$Lineweight
[1] "ByLayer"

$content$data$collection[[6]]$properties$General$`Plot style`
[1] "ByColor"

$content$data$collection[[6]]$properties$General$Transparency
[1] "ByLayer"


$content$data$collection[[6]]$properties$Geometry
$content$data$collection[[6]]$properties$Geometry$Height
[1] 35.35707

$content$data$collection[[6]]$properties$Geometry$Length
[1] 9.161039

$content$data$collection[[6]]$properties$Geometry$Rotation
[1] 0

$content$data$collection[[6]]$properties$Geometry$`Solid type`
[1] "Box"

$content$data$collection[[6]]$properties$Geometry$Width
[1] 11.15553


$content$data$collection[[6]]$properties$`Solid History`
$content$data$collection[[6]]$properties$`Solid History`$`Record History`
[1] 1

$content$data$collection[[6]]$properties$`Solid History`$`Show History`
[1] 0


$content$data$collection[[6]]$properties$`__viewable_in__`
$content$data$collection[[6]]$properties$`__viewable_in__`$viewable_in
$content$data$collection[[6]]$properties$`__viewable_in__`$viewable_in[[1]]
[1] "Model-3D"

$content$data$collection[[6]]$properties$`__viewable_in__`$viewable_in[[2]]
[1] "Model"


$content$data$collection[[7]]
$content$data$collection[[7]]$objectid
[1] 163

$content$data$collection[[7]]$name
[1] "Solid [20F]"

$content$data$collection[[7]]$properties
$content$data$collection[[7]]$properties$elementId
[1] "20F"

$content$data$collection[[7]]$properties$type
[1] "AcDb3dSolid"

$content$data$collection[[7]]$properties$`3D Visualization`
$content$data$collection[[7]]$properties$`3D Visualization`$Material
[1] "Brass - Satin 1"

$content$data$collection[[7]]$properties$`3D Visualization`$`Shadow Display`
[1] "Casts and Receives shadows"


$content$data$collection[[7]]$properties$General
$content$data$collection[[7]]$properties$General$Color
[1] "ByLayer"

$content$data$collection[[7]]$properties$General$Layer
[1] "0"

$content$data$collection[[7]]$properties$General$Linetype
[1] "ByLayer"

$content$data$collection[[7]]$properties$General$`Linetype scale`
[1] 1

$content$data$collection[[7]]$properties$General$Lineweight
[1] "ByLayer"

$content$data$collection[[7]]$properties$General$`Plot style`
[1] "ByColor"

$content$data$collection[[7]]$properties$General$Transparency
[1] "ByLayer"


$content$data$collection[[7]]$properties$Geometry
$content$data$collection[[7]]$properties$Geometry$Height
[1] 7.69588

$content$data$collection[[7]]$properties$Geometry$Length
[1] 9.161039

$content$data$collection[[7]]$properties$Geometry$Rotation
[1] 0

$content$data$collection[[7]]$properties$Geometry$`Solid type`
[1] "Box"

$content$data$collection[[7]]$properties$Geometry$Width
[1] 11.15553


$content$data$collection[[7]]$properties$`Solid History`
$content$data$collection[[7]]$properties$`Solid History`$`Record History`
[1] 1

$content$data$collection[[7]]$properties$`Solid History`$`Show History`
[1] 0


$content$data$collection[[7]]$properties$`__viewable_in__`
$content$data$collection[[7]]$properties$`__viewable_in__`$viewable_in
$content$data$collection[[7]]$properties$`__viewable_in__`$viewable_in[[1]]
[1] "Model-3D"

$content$data$collection[[7]]$properties$`__viewable_in__`$viewable_in[[2]]
[1] "Model"


$content$data$collection[[8]]
$content$data$collection[[8]]$objectid
[1] 352

$content$data$collection[[8]]$name
[1] "Sphere (1)"

$content$data$collection[[8]]$properties
$content$data$collection[[8]]$properties$elementId
[1] "Sphere"

$content$data$collection[[8]]$properties$type
[1] "Sphere"


$content$data$collection[[9]]
$content$data$collection[[9]]$objectid
[1] 149

$content$data$collection[[9]]$name
[1] "Solid [1DA]"

$content$data$collection[[9]]$properties
$content$data$collection[[9]]$properties$elementId
[1] "1DA"

$content$data$collection[[9]]$properties$type
[1] "AcDb3dSolid"

$content$data$collection[[9]]$properties$`3D Visualization`
$content$data$collection[[9]]$properties$`3D Visualization`$Material
[1] "Rust - Heavy"

$content$data$collection[[9]]$properties$`3D Visualization`$`Shadow Display`
[1] "Casts and Receives shadows"


$content$data$collection[[9]]$properties$General
$content$data$collection[[9]]$properties$General$Color
[1] "ByLayer"

$content$data$collection[[9]]$properties$General$Layer
[1] "0"

$content$data$collection[[9]]$properties$General$Linetype
[1] "ByLayer"

$content$data$collection[[9]]$properties$General$`Linetype scale`
[1] 1

$content$data$collection[[9]]$properties$General$Lineweight
[1] "ByLayer"

$content$data$collection[[9]]$properties$General$`Plot style`
[1] "ByColor"

$content$data$collection[[9]]$properties$General$Transparency
[1] "ByLayer"


$content$data$collection[[9]]$properties$Geometry
$content$data$collection[[9]]$properties$Geometry$Diameter
[1] 13.37091

$content$data$collection[[9]]$properties$Geometry$Radius
[1] 6.685454

$content$data$collection[[9]]$properties$Geometry$`Solid type`
[1] "Sphere"


$content$data$collection[[9]]$properties$`Solid History`
$content$data$collection[[9]]$properties$`Solid History`$`Record History`
[1] 1

$content$data$collection[[9]]$properties$`Solid History`$`Show History`
[1] 0


$content$data$collection[[9]]$properties$`__viewable_in__`
$content$data$collection[[9]]$properties$`__viewable_in__`$viewable_in
$content$data$collection[[9]]$properties$`__viewable_in__`$viewable_in[[1]]
[1] "Model-3D"

$content$data$collection[[9]]$properties$`__viewable_in__`$viewable_in[[2]]
[1] "Model"


$content$data$collection[[10]]
$content$data$collection[[10]]$objectid
[1] 355

$content$data$collection[[10]]$name
[1] "Surfaces (1)"

$content$data$collection[[10]]$properties
$content$data$collection[[10]]$properties$elementId
[1] "Surfaces"

$content$data$collection[[10]]$properties$type
[1] "Surfaces"


$content$data$collection[[11]]
$content$data$collection[[11]]$objectid
[1] 353

$content$data$collection[[11]]$name
[1] "Planar (1)"

$content$data$collection[[11]]$properties
$content$data$collection[[11]]$properties$elementId
[1] "Planar"

$content$data$collection[[11]]$properties$type
[1] "Planar"


$content$data$collection[[12]]
$content$data$collection[[12]]$objectid
[1] 142

$content$data$collection[[12]]$name
[1] "Surface [1C1]"

$content$data$collection[[12]]$properties
$content$data$collection[[12]]$properties$elementId
[1] "1C1"

$content$data$collection[[12]]$properties$type
[1] "AcDbPlaneSurface"

$content$data$collection[[12]]$properties$`3D Visualization`
$content$data$collection[[12]]$properties$`3D Visualization`$Material
[1] "Indoor Pool"

$content$data$collection[[12]]$properties$`3D Visualization`$`Shadow Display`
[1] "Casts and Receives shadows"


$content$data$collection[[12]]$properties$General
$content$data$collection[[12]]$properties$General$Color
[1] "ByLayer"

$content$data$collection[[12]]$properties$General$Layer
[1] "0"

$content$data$collection[[12]]$properties$General$Linetype
[1] "ByLayer"

$content$data$collection[[12]]$properties$General$`Linetype scale`
[1] 1

$content$data$collection[[12]]$properties$General$Lineweight
[1] "ByLayer"

$content$data$collection[[12]]$properties$General$`Plot style`
[1] "ByColor"

$content$data$collection[[12]]$properties$General$Transparency
[1] "ByLayer"


$content$data$collection[[12]]$properties$Geometry
$content$data$collection[[12]]$properties$Geometry$`Surface Type`
[1] "Planar"

$content$data$collection[[12]]$properties$Geometry$`U isolines`
[1] 6

$content$data$collection[[12]]$properties$Geometry$`V isolines`
[1] 6

$content$data$collection[[12]]$properties$Geometry$`Wireframe display`
[1] "Isolines"


$content$data$collection[[12]]$properties$`Surface Associativity`
$content$data$collection[[12]]$properties$`Surface Associativity`$`Maintain associativity`
[1] "None"


$content$data$collection[[12]]$properties$Trims
$content$data$collection[[12]]$properties$Trims$`Trimmed surface`
[1] 0

$content$data$collection[[12]]$properties$Trims$`Trimming edges`
[1] 0


$content$data$collection[[12]]$properties$`__viewable_in__`
$content$data$collection[[12]]$properties$`__viewable_in__`$viewable_in
$content$data$collection[[12]]$properties$`__viewable_in__`$viewable_in[[1]]
[1] "Model-3D"

$content$data$collection[[12]]$properties$`__viewable_in__`$viewable_in[[2]]
[1] "Model"


$path
[1] "https://developer.api.autodesk.com/modelderivative/v2/designdata/dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6Y3JhenlidWNrZXQvYWVyaWFsLmR3Zw==/metadata/e30bd031-d13a-a976-9153-78100829986a/properties"

$response
Response [https://developer.api.autodesk.com/modelderivative/v2/designdata/dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6Y3JhenlidWNrZXQvYWVyaWFsLmR3Zw==/metadata/e30bd031-d13a-a976-9153-78100829986a/properties]
  Date: 2016-11-14 01:50
  Status: 200
  Content-Type: application/json; charset=utf-8
  Size: 3.95 kB


attr(,"class")
[1] "getData"
```