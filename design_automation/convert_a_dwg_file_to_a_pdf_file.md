## Convert a DWG File to a PDF File {#convert-a-dwg-file-to-a-pdf-file}

To convert a DWG file to a PDF file, use the `makePdf` function, where `source` and `destination` are the publicly accessible source of the DWG file and destination for the PDF file, respectively.

```
mySource <- "http://download.autodesk.com/us/samplefiles/acad/visualization_-_aerial.dwg"
myDestination <- "https://drive.google.com/folderview?id=0BygncDVHf60mTDZVNDltLThLNmM&usp=sharing"
resp <- makePdf(source = mySource, destination = myDestination, token = myToken)
```

Note that in this example, the `token` must be generated with the `code:all` scope.

To check the status of the conversion process:

```
resp <- checkPdf(source = mySource, destination = myDestination, token = myToken)
resp
$content
$content$`@odata.context`
[1] "https://developer.api.autodesk.com/autocad.io/us-east/v2/$metadata#WorkItems"

$content$value
$content$value[[1]]
$content$value[[1]]$ActivityId
[1] "PlotToPDF"

$content$value[[1]]$Arguments
$content$value[[1]]$Arguments$InputArguments
$content$value[[1]]$Arguments$InputArguments[[1]]
$content$value[[1]]$Arguments$InputArguments[[1]]$Resource
[1] "http://download.autodesk.com/us/samplefiles/acad/visualization_-_aerial.dwg"

$content$value[[1]]$Arguments$InputArguments[[1]]$Name
[1] "HostDwg"

$content$value[[1]]$Arguments$InputArguments[[1]]$Headers
list()

$content$value[[1]]$Arguments$InputArguments[[1]]$ResourceKind
NULL

$content$value[[1]]$Arguments$InputArguments[[1]]$StorageProvider
[1] "Generic"

$content$value[[1]]$Arguments$InputArguments[[1]]$HttpVerb
NULL



$content$value[[1]]$Arguments$OutputArguments
$content$value[[1]]$Arguments$OutputArguments[[1]]
$content$value[[1]]$Arguments$OutputArguments[[1]]$Resource
[1] "https://drive.google.com/folderview?id=0BygncDVHf60mTDZVNDltLThLNmM&usp=sharing"

$content$value[[1]]$Arguments$OutputArguments[[1]]$Name
[1] "Result"

$content$value[[1]]$Arguments$OutputArguments[[1]]$Headers
list()

$content$value[[1]]$Arguments$OutputArguments[[1]]$ResourceKind
NULL

$content$value[[1]]$Arguments$OutputArguments[[1]]$StorageProvider
[1] "Generic"

$content$value[[1]]$Arguments$OutputArguments[[1]]$HttpVerb
[1] "POST"




$content$value[[1]]$Status
[1] "FailedMissingOutput"

$content$value[[1]]$StatusDetails
$content$value[[1]]$StatusDetails$Report
[1] "https://acadio.s3.amazonaws.com/aces-workitem-reports/a81d8a7f2e2646f6bd66dd116b3f42a2/report.log?AWSAccessKeyId=ASIAINV2DWFHKOPZH4LA&Expires=1479173001&x-amz-security-token=FQoDYXdzELH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDCqgDyFcPfMwEt1zcyKcA%2BYWaTBjF9LhMIf6VfYzHNjSRPq1RvX7RHLGtSZO3y1f87Q3XaTjA6hhcuMrNbIb5oc1mBX38wW8cW6d%2BF%2BvQwBV8fTGUSwTnZZcVVXyj%2Frh%2Bw2f0Hf1%2B2RV8iChX9gw9FTL%2B2q89GrYF%2BP3t89XSaHLwPIzyAzQ9t%2BP8jq2eLTD11dBykn1OBPYqyOcQDWjNJ9l7RGmDtfNY%2Bmku3I64Qq77Dz1dZHsvp8f5saIGXdogM92LcAOteWsiu3FMRn7DWOAuIAEhL8thepnglXaGByD7ZZ01GKThnlmSdlvjR3QFyJFuCU1uLuuzGbBPrrNE9xrHv6I58qmxbaCdtoIrrvy9%2FLAqMC%2FE72fSSDht9PD6Zrh8SPAAXn0DiLM8kF%2FA42dKzKnj7PitsY%2FhIX%2Bb%2BxLNwKVlNUS81lRICO%2Ft1ALgeHiC76%2Fg2F8Hn8WNZcC%2B4xZACz3%2FCRRXuGaelxPYtkhZnL4csaRGVfeEAMFHA9lah8mavj2aYUQKv0L%2FdoDqpAb6BVjRRFatybbwJSMloUe0zH7PxwYQhxy2zQo7PGjwQU%3D&Signature=7nOnYzcWYZcpxHZJ7joiBFK735I%3D"


$content$value[[1]]$AvailabilityZone
NULL

$content$value[[1]]$TimeQueued
[1] "2016-11-14T01:23:07.37Z"

$content$value[[1]]$TimeInputTransferStarted
[1] "2016-11-14T01:23:07.314Z"

$content$value[[1]]$TimeScriptStarted
[1] "2016-11-14T01:23:08.814Z"

$content$value[[1]]$TimeScriptEnded
[1] "2016-11-14T01:23:14.095Z"

$content$value[[1]]$TimeOutputTransferEnded
[1] "2016-11-14T01:23:14.188Z"

$content$value[[1]]$BytesTranferredIn
[1] 733036

$content$value[[1]]$BytesTranferredOut
NULL

$content$value[[1]]$Timestamp
[1] "2016-11-14T01:23:14.188Z"

$content$value[[1]]$Id
[1] "a81d8a7f2e2646f6bd66dd116b3f42a2"




$path
[1] "https://developer.api.autodesk.com/autocad.io/us-east/v2/WorkItems"

$response
Response [https://developer.api.autodesk.com/autocad.io/us-east/v2/WorkItems]
  Date: 2016-11-14 01:23
  Status: 200
  Content-Type: application/json; odata.metadata=minimal
  Size: 2.12 kB
{
  "@odata.context":"https://developer.api.autodesk.com/autocad.io/us-east/v2/$metadata#Work...
    {
      "ActivityId":"PlotToPDF","Arguments":{
        "InputArguments":[
          {
            "Resource":"http://download.autodesk.com/us/samplefiles/acad/visualization_-_ae...
              
            ],"ResourceKind":null,"StorageProvider":"Generic","HttpVerb":null
          }
...

attr(,"class")
[1] "checkPdf"
```