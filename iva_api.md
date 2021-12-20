# Endpoints 

| Path | Description |
|------|-------------|
| [`GET` /iva/api/v1/jobs](#op-get-iva-jobs) | Return all iva jobs summary. |
| [`GET` /iva/api/v1/jobs/{service_id}/{channel_id}](#op-get-iva-jobs-sid-cid)  | Return iva job summary.|
| [`GET` /iva/api/v1/jobs/{service_id}/{channel_id}/status](#op-get-iva-jobs-sid-cid-status)  | Return iva job status.|
| [`POST` /iva/api/v1/jobs](#op-post-iva-jobs) | Start new iva job. |
| [`DELETE` /iva/api/v1/jobs/{service_id}/{channel_id}](#op-delete-iva-jobs-sid-cid) | Stop iva job. |
| [`GET` /iva/api/v1/logs/?s={start_timestamp}&e={end_timestamp}](#op-get-iva-logs-s-e) | Return logs between start and end timestamp. |
<br />

<a id="op-get-iva-jobs"></a>

## `GET` /iva/api/v1/jobs 
Return all iva jobs summary.

### Responses
* 200 - Success
  > application/json

### Example 
```json
[
    {
        "service":"lpr01",
        "jobs":[
            {
                "id": "1122334401",
                "service":"lpr01",
                "channel": 0,
                "instanceid": 1,
                "setting": {
                    "sourceid": "1122334401",                    
                    "uri": "rtsp://192.168.13.231:8554/h264",
                    "jpegquality": 60,
                    "padding": [30, 30, 30, 30],
                    "roi": [],
                    "starttime": 0,
                    "endtime": 0,
                    "vasrctype": 1,
                    "vatype": 1
                },
                "prop": {},
                "status": 201
            },
            {
                "id": "1122334402",
                "service":"lpr01",
                "channel": 1,
                "instanceid": 1,
                "setting": {
                    "sourceid": "1122334402",                    
                    "uri": "rtsp://192.168.13.232:8554/h264",
                    "jpegquality": 60,
                    "padding": [30, 30, 30, 30],
                    "roi": [],
                    "starttime": 0,
                    "endtime": 0,
                    "vasrctype": 1,
                    "vatype": 1
                },
                "prop": {},
                "status": 201
            }
        ]
    },
    {
        "service":"lpr02",
        "jobs":[
            {
                "id": "1122334403",
                "service":"lpr02",
                "channel": 0,
                "instanceid": 1,
                "setting": {
                    "sourceid": "1122334403",                    
                    "uri": "rtsp://192.168.13.233:8554/h264",
                    "jpegquality": 60,
                    "padding": [30, 30, 30, 30],
                    "roi": [],
                    "starttime": 0,
                    "endtime": 0,
                    "vasrctype": 1,
                    "vatype": 1
                },
                "prop": {},
                "status": 201
            },
        ]
    }
]
```

<br />

<a id="op-get-iva-jobs-sid-cid"></a>

## `GET` /iva/api/v1/jobs/{service_id}/{channel_id}
Return iva job summary.

### Path parameters
#### &#9655; service_id
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>In</th>
      <th>Accepted values</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>service_id <strong>(required)</strong></td>
      <td>String</td>
      <td>Path</td>
      <td><em>Any</em></td>
    </tr>
  </tbody>
</table>

#### &#9655; channel_id
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>In</th>
      <th>Accepted values</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>channel_id <strong>(required)</strong></td>
      <td>Number</td>
      <td>Path</td>
      <td><em>Any</em></td>
    </tr>
  </tbody>
</table>

### Responses
* 200 - Success
  > application/json
* 400 - Not Found
* 404 - Bad Request

### Example
```json
{
    "id": "1122334401",
    "service":"lpr01",
    "channel": 0,
    "instanceid": 1,
    "setting": {
        "sourceid": "1122334401",                    
        "uri": "rtsp://192.168.13.231:8554/h264",
        "jpegquality": 60,
        "padding": [30, 30, 30, 30],
        "roi": [],
        "starttime": 0,
        "endtime": 0,
        "vasrctype": 1,
        "vatype": 1
    },
    "prop": {},
    "status": 201
}
```

<br />

<a id="op-get-iva-jobs-sid-cid-status"></a>

## `GET` /iva/api/v1/jobs/{service_id}/{channel_id}/status
Return iva job status.

### Path parameters
#### &#9655; service_id
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>In</th>
      <th>Accepted values</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>service_id <strong>(required)</strong></td>
      <td>String</td>
      <td>Path</td>
      <td><em>Any</em></td>
    </tr>
  </tbody>
</table>

#### &#9655; channel_id
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>In</th>
      <th>Accepted values</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>channel_id <strong>(required)</strong></td>
      <td>Number</td>
      <td>Path</td>
      <td><em>Any</em></td>
    </tr>
  </tbody>
</table>

### Responses
* 200 - Running
* 400 - Not Found
* 404 - Bad Request

<br />

<a id="op-post-iva-jobs"></a>

## `POST` /api/v1/jobs
Start new iva job.

### Request body
> application/json

### Example
```json
{
    "id": "1122334401",
    "service":"auto",
    "channel": -1,
    "setting": {
        "sourceid": "1122334401",                    
        "uri": "rtsp://192.168.13.231:8554/h264",
        "jpegquality": 60,
        "padding": [30, 30, 30, 30],
        "roi": [],
        "starttime": 0,
        "endtime": 0,
        "vasrctype": 1,
        "vatype": 1
    },
    "prop": {}
}    
```

### Responses
* 200 - Success

<br />

<a id="op-delete-iva-jobs-sid-cid"></a>

## `DELETE` /iva/api/v1/jobs/{service_id}/{channel_id}
Stop iva job.

### Path parameters
#### &#9655; service_id
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>In</th>
      <th>Accepted values</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>service_id <strong>(required)</strong></td>
      <td>String</td>
      <td>Path</td>
      <td><em>Any</em></td>
    </tr>
  </tbody>
</table>

#### &#9655; channel_id
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>In</th>
      <th>Accepted values</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>channel_id <strong>(required)</strong></td>
      <td>Number</td>
      <td>Path</td>
      <td><em>Any</em></td>
    </tr>
  </tbody>
</table>

### Responses
* 200 - Success

<br />

<a id="op-get-iva-logs-s-e"></a>

## `GET` /iva/api/v1/logs/?s={start_timestamp}&e={end_timestamp}
Return logs between start and end timestamp.

### Query parameters
#### &#9655; s

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>In</th>
      <th>Accepted values</th>
    </tr>
  </thead>
  <tbody>
      <tr>
        <td>s  <strong>(required)</strong></td>
        <td>
          Number
        </td>
        <td>Query</td>
        <td><em>Unix timestamp</em></td>
      </tr>
  </tbody>
</table>

#### &#9655; e

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>In</th>
      <th>Accepted values</th>
    </tr>
  </thead>
  <tbody>
      <tr>
        <td>e  <strong>(required)</strong></td>
        <td>
          Number
        </td>
        <td>Query</td>
        <td><em>Unix timestamp</em></td>
      </tr>
  </tbody>
</table>

### Responses
* 200 - Success
  > application/json

### Example
```json
[
  {    
    "code":201,
    "message":"lpr start",
    "service":"lpr01",
    "channel":0,
    "timestamp":1620697435
  },
  {    
    "code":401,
    "message":"lpr stop",
    "service":"lpr01",
    "channel":0,
    "timestamp":1620697455
  },
]
```
<br />