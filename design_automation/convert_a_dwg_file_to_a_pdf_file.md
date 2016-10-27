## Convert a DWG File to a PDF File {#convert-a-dwg-file-to-a-pdf-file}

The Design Automation API provides the ability to run automated scripts on design files. For example, to convert a DWG file to a PDF file, use the `makePdf` function, where `source` and `destination` are the publicly accessible source of the DWG file and destination for the PDF file, respectively.

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
```