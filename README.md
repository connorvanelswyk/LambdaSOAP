# Jsoap-api

[![Build Status][ci-img]][ci]
[![Coverage Status][coveralls-img]][coveralls]

AWS Lambda (serverless) [Jsoap][jsoap] API implementation.

## Usage

### Sending a Request

### Returning a String
The most minimal request possible requires only two (2) parameters: *wsdl*, and *xml*. 
```cmd
curl \
-d '{
  "wsdl": "https://graphical.weather.gov/xml/SOAP_server/ndfdXMLserver.php",
  "body": "https://graphical.weather.gov/xml/docs/SOAP_Requests/LatLonListZipCode.xml",
}' \
-H 'Content-Type: application/json' \
https://dbc99ix1f1.execute-api.us-east-1.amazonaws.com/dev/jsoap
```

### Returning a Object
More complex requests can be defined with parameters and a nested result schema
```cmd
curl \
-d '{
  "wsdl": "https://graphical.weather.gov:443/xml/SOAP_server/ndfdXMLserver.php",
  "body": "https://graphical.weather.gov/xml/docs/SOAP_Requests/GmlLatLonList.xml",  
  "params": {
    "requestedTime": "2019-07-22T23:59:59"
  },
  "schema": {
    "gml:boundedBy": {
      "gml:coordinates": ""
    },
    "gml:featureMember": {
      "gml:coordinates": "",
      "app:validTime": "",
      "app:maximumTemperature": ""
    }
  }
}' \
-H 'Content-Type: application/json' \
https://dbc99ix1f1.execute-api.us-east-1.amazonaws.com/dev/jsoap
```

*note - aforementioned code snippets are dependent on the [weather.gov][wg] public SOAP web service*

[jsoap]: https://github.com/connorvanelswyk/jsoap
[wg]: https://www.weather.gov
[ci-img]: https://api.travis-ci.com/connorvanelswyk/LambdaSOAP.svg?branch=master
[ci]: https://travis-ci.com/connorvanelswyk/LambdaSOAP
[coveralls-img]: https://coveralls.io/repos/github/connorvanelswyk/LambdaSOAP/badge.svg?branch=master
[coveralls]: https://coveralls.io/github/connorvanelswyk/LambdaSOAP?branch=master   
[open-closed]: https://en.wikipedia.org/wiki/Open–closed_principle
[aws-lambda]: https://aws.amazon.com/lambda/
[rest]: https://en.wikipedia.org/wiki/Representational_state_transfer
[soap]: https://en.wikipedia.org/wiki/SOAP
