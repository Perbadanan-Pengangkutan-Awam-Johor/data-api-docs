# PAJ Data API Documentation
![Paj banner](/images/data-api-banner.png)

<p align="center">
<a title="version" href=""><img src="https://img.shields.io/badge/version-1.0.0-green"></a>
<a title="version" href=""><img src="https://img.shields.io/badge/Status-Release-green"></a>
<a title="version" href=""><img src="https://img.shields.io/badge/Copyright-PAJ-blue"></a>
<a title="version" href=""><img src="https://img.shields.io/badge/License-GNU v3.0-blue"></a>
<a title="version" href=""><img src="https://img.shields.io/badge/Server-Up-green"></a>

</p>

## Overview
The documentation to assist you with on how to use PAJ Data API to intergrate it with you apps. 

Perbadanan Pengangkutan Awam Johor provides an open API service to any third parties whose need it. These data can be used as tools such as data analysis, creating reporting and understanding vehicle workflow.

Most of available open API provided is related to Bas Muafakat Johor (BMJ) which is bus services working directly under Perbadanan Pengangkutan Awam Johor.

## Contact

If you have any questions regarding our guides or suggestion, please contact PAJ Support at official@paj.com.my.

## Available API

Below are available API options that available by public users

- [Bus Route](/netverify/netverify-web-v4.md)
- [Route GeoJson](/netverify/performNetverify.md)
- [Route Schedule](/netverify/performNetverify.md)
- [Operator List](/netverify/performNetverify.md)
- [Bus Live Data](/netverify/performNetverify.md)
- [Terminal, Stops and Pole](/netverify/performNetverify.md)
- [Bus List](/netverify/performNetverify.md)
- [Bus History](/netverify/performNetverify.md)
- [Bus Report Calendar](/netverify/performNetverify.md)


## Get Your API Key

You can get your key from [https://dataapi.paj.com.my](https://dataapi.paj.com.my/key). A valid account are needed to get the key.

## Using API Key

1. Get your API Key [here](https://dataapi.paj.com.my/key)

2. To get the response, you will need to pass 'api-key' header with the given key. Same key can be use to make consicutive request from the server.

Request example using Python:
```python
import requests

api_key = 'YOUR_API_KEY'
headers = {'api-key': api_key}
response = requests.get('https://dataapi.paj.com.my/api/v1/route/name/P101', headers=headers)
if response.status_code == 200:
    print(response.json())
else:
    print('Error:', response.status_code)
```

Example of success response:
```json
{
    "status": "success",
    "data": [
        {
            "name": "P101",
            "bus_vendor_id": 1,
            "distance": 21.5,
            "special_Line": 0,
            "total_trip": 33,
            "active": 1
        }
    ]
}
```

Example of error response:
```json
{
    "status": "error",
    "message": "Invalid API Key"
}
```

## Rate Limit
- There is a limit of 6 request per minute for a single key and IP address.

## Error Message

In case you get an error message, below is description why it is happening

| Error Message     | Description                                                  |
| ----------------  | ------------------------------------------------------------ |
| API Key Required  | No header with 'api-key' detected |
| Invalid API Key   | There is no such api-key exist in data api database        |
| Invalid parameter or endpoint | Make sure that your url endpoint is correct or make sure that url parameter is correct |
| Rate limit reach | Reach 1 minute request call. You will need to wait another 1 minute for a cooldown |

## Empty Valid Response
In the case of zero data available for particular reponse. The system will simply reply with an empty array like example below
```json
{
    "status": "success",
    "data": []
}
```
## Acknowledgement
<img src="/images/logo-paj-sm.png" height="50" />
Thanks for support from Perbadanan Pengangkutan Awam Johor for making this public API possible



