---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - json

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to ZEITDice API reference, you can use out API to access ZEITDice API endpoints, which can get information about the devices, sources, heartbeats and more in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# /api/v4/devices

This GET endpoint will return a JSON with the information of the Devices of the current logged user, if the current user is admin will display all the devices in the database.

```shell
# With shell, you can just pass the correct header with each request
curl "http://localhost:3000/api/v4/devices"
  -H "Authorization: X"
```

```json
[
   {
      "id":1,
      "uuid":"TEST-UUID",
      "iccid":null,
      "hw_model":null,
      "hw_version":null,
      "comment":null,
      "user_id":2,
      "created_at":"2020-09-21T23:21:50.027Z",
      "updated_at":"2020-09-29T16:53:07.480Z",
      "last_image_url":"https://zeitings-dev.s3.amazonaws.com/stills/1/bb/202009121312.jpg",
      "battery_history":{
         "2020-09-21 23:21:00 UTC":85,
         "2020-09-21 23:33:00 UTC":86,
         "2020-09-21 23:38:00 UTC":87,
         "2020-09-21 23:43:00 UTC":87,
         "2020-09-21 23:48:00 UTC":88,
         "2020-09-21 23:53:00 UTC":89,
         "2020-09-21 23:58:00 UTC":90,
         "2020-09-22 00:03:00 UTC":90,
         "2020-09-22 00:15:00 UTC":91
      },
      "last_heartbeat":{
         "id":9,
         "device_id":1,
         "interval":300,
         "next_wakeup":null,
         "battery_level":91,
         "sdSizeMB":24076,
         "sdFreeMB":22828,
         "operator_version":"operator-20200908",
         "shield_fw_version":"V1.0.0",
         "timezone":"America/Toronto",
         "powersource":"Battery",
         "vbatt":4.08,
         "vsys":4.07,
         "mode":"CONFIG",
         "temperature":28,
         "shield_datetime":"2020-01-01T10:49:36.000Z",
         "rpi_datetime":"2020-09-21T19:21:28.519Z",
         "uptime_at_start":"2000-01-01T00:00:04.260Z",
         "uptime_at_upload":"2000-01-01T00:00:12.770Z",
         "payload":{
            "interval":"300",
            "battery_level":"91",
            "sdSizeMB":"24076.62109375",
            "sdFreeMB":"22828.61328125",
            "operator_version":"operator-20200908",
            "shield_fw_version":"V1.0.0",
            "timezone":"America/Toronto",
            "powersource":"Battery",
            "vbatt":"4.08V",
            "vsys":"4.07V",
            "mode":"CONFIG",
            "temperature":"28",
            "shield_datetime":"2020-01-01 10:49:36",
            "rpi_datetime":"2020-09-21 19:21:28.519000",
            "uptime_at_start":"0:00:04.260000",
            "uptime_at_upload":"0:00:12.770000"
         },
         "created_at":"2020-09-22T00:15:51.625Z",
         "updated_at":"2020-09-22T00:15:51.625Z"
      },
      "source":{
         "id":1,
         "name":"Device started 2020-09-21 18:57:44 UTC",
         "guid":"TEST-UUID",
         "push_settings":null,
         "url":null,
         "created_at":"2020-09-21T18:57:45.011Z",
         "updated_at":"2020-09-28T18:58:43.161Z",
         "website":null,
         "location":"unknown",
         "public":false,
         "source_type":null,
         "user_id":2,
         "token":null,
         "flip":null,
         "night_edge_bytes":null,
         "chart":null,
         "vendor_id":1,
         "utc":false,
         "analytics":false,
         "unlinked":false,
         "key":"a732d8349c6281fb997b",
         "autoclean":true,
         "ai_threshold":50,
         "ai_relevant_objects":"{'person': True, 'car': True, 'truck': True}"
      }
   }
]
```

# /api/v4/devices/:UUID/heartbeats/latest

This GET endpoint will return a JSON with the information of the last heartbeat of the device you specify with the UUID in the URL.

```shell
# With shell, you can just pass the correct header with each request
# Replace the :UUID with the UUID of the device that you want to get the last heartbeat from
curl "http://localhost:3000/api/v4/devices/:UUID/heartbeats/latest"
  -H "Authorization: X"
```

```json
{
   "id":9,
   "device_id":1,
   "interval":300,
   "next_wakeup":null,
   "battery_level":91,
   "sdSizeMB":24076,
   "sdFreeMB":22828,
   "operator_version":"operator-20200908",
   "shield_fw_version":"V1.0.0",
   "timezone":"America/Toronto",
   "powersource":"Battery",
   "vbatt":4.08,
   "vsys":4.07,
   "mode":"CONFIG",
   "temperature":28,
   "shield_datetime":"2020-01-01T10:49:36.000Z",
   "rpi_datetime":"2020-09-21T19:21:28.519Z",
   "uptime_at_start":"2000-01-01T00:00:04.260Z",
   "uptime_at_upload":"2000-01-01T00:00:12.770Z",
   "payload":{
      "interval":"300",
      "battery_level":"91",
      "sdSizeMB":"24076.62109375",
      "sdFreeMB":"22828.61328125",
      "operator_version":"operator-20200908",
      "shield_fw_version":"V1.0.0",
      "timezone":"America/Toronto",
      "powersource":"Battery",
      "vbatt":"4.08V",
      "vsys":"4.07V",
      "mode":"CONFIG",
      "temperature":"28",
      "shield_datetime":"2020-01-01 10:49:36",
      "rpi_datetime":"2020-09-21 19:21:28.519000",
      "uptime_at_start":"0:00:04.260000",
      "uptime_at_upload":"0:00:12.770000"
   },
   "created_at":"2020-09-22T00:15:51.625Z",
   "updated_at":"2020-09-22T00:15:51.625Z"
}
```

# /api/v4/devices/:UUID/settings

This POST endpoint will create a device settings entry in the database with the payload that you specify in the POST request, this will return a JSON with the information of the device settings just created of the device you specify with the UUID in the URL.

```shell
# Replace the :UUID with the UUID of the device that you want to post settings to

curl -X POST --data '{"operator": "true", "payload":{"interval": 3600}}' http://localhost:3000/api/v4/devices/:UUID/settings --header "Content-Type:application/json"

curl -X POST --data '{"operator": "true", "payload":{"upload_request": "/storage/op.log"}}' http://localhost:3000/api/v4/devices/:UUID/settings --header "Content-Type:application/json"

curl -X POST --data '{"operator": "false", "payload":{"new_settings": {"resolution":"4056x3040","rotation":"0","full_res_threshold":"0","image_effect":"denoise","sharpness":"50"}}}' http://localhost:3000/api/v4/devices/8de4c3f2-ce1e-21c6-ba33-1a2cbd9cfc19/settings --header "Content-Type:application/json"

curl -X POST --data '{"operator": "true", "payload":{"fw_url": "https://zd-firmware-releases.s3.amazonaws.com/zd-infinity/master-20200724-113545.tar.gz", "fw_checksum": "c2ba27a1d26695f52d6f7cfd1ee1a894c24c18bc93455ae2393fdf665fbc660a"}}' http://localhost:3000/api/v4/devices/:UUID/settings --header "Content-Type:application/json"

curl -X POST --data '{"operator": "true", "payload":{"fw_url": "https://zd-firmware-releases.s3.amazonaws.com/zd-infinity/master-20200725-181519.tar.gz", "fw_checksum": "75558c34bbce18d17be59bc84032692198c53f0bb6c2c80905f3a8c653d409e7"}}' http://localhost:3000/api/v4/devices/:UUID/settings --header "Content-Type:application/json"

curl -X POST --data '{"operator": "true", "payload":{"upload_request": "/storage/op.log"}}' http://localhost:3000/api/v4/devices/:UUID/settings --header "Content-Type:application/json"
```

```json
{
   "id":13,
   "source_id":null,
   "installed":false,
   "payload":{
      "interval":3600
   },
   "created_at":"2020-10-09T14:20:09.003Z",
   "updated_at":"2020-10-09T14:20:09.003Z",
   "operator":true,
   "device_id":1
}
```

# /api/v4/devices/:UUID (show)
This GET endpoint will return a JSON with the information of the last the device you specify with the UUID in the URL.

```shell
# Replace the :UUID with the UUID of the device that you want to get the last heartbeat from
curl "http://localhost:3000/api/v4/devices/:UUID"
  -H "Authorization: X"
```

```json
{
   "id":1,
   "uuid":"TEST-UUID",
   "iccid":null,
   "hw_model":null,
   "hw_version":null,
   "comment":null,
   "user_id":2,
   "created_at":"2020-09-21T23:21:50.027Z",
   "updated_at":"2020-09-29T16:53:07.480Z"
}
```

# /api/v4/devices/:UUID/heartbeats (index)
This GET endpoint will return a JSON array with each heartbeat of the device you specify with the UUID in the URL.

```shell
   curl "http://localhost:3000/api/v4/devices/:UUID"
```

```json
[
   {
      "id":1,
      "device_id":1,
      "interval":300,
      "next_wakeup":null,
      "battery_level":85,
      "sdSizeMB":24076,
      "sdFreeMB":22835,
      "operator_version":"operator-20200908",
      "shield_fw_version":"V1.0.0",
      "timezone":"America/Toronto",
      "powersource":"Battery",
      "vbatt":4.06,
      "vsys":4.05,
      "mode":"CONFIG",
      "temperature":33,
      "shield_datetime":"2020-01-01T09:55:35.000Z",
      "rpi_datetime":"2020-09-21T19:21:28.708Z",
      "uptime_at_start":"2000-01-01T00:00:04.500Z",
      "uptime_at_upload":"2000-01-01T00:00:10.820Z",
      "payload":{
         "interval":"300",
         "battery_level":"85",
         "sdSizeMB":"24076.62109375",
         "sdFreeMB":"22835.265625",
         "operator_version":"operator-20200908",
         "shield_fw_version":"V1.0.0",
         "timezone":"America/Toronto",
         "powersource":"Battery",
         "vbatt":"4.06V",
         "vsys":"4.05V",
         "mode":"CONFIG",
         "temperature":"33",
         "shield_datetime":"2020-01-01 09:55:35",
         "rpi_datetime":"2020-09-21 19:21:28.708734",
         "uptime_at_start":"0:00:04.500000",
         "uptime_at_upload":"0:00:10.820000"
      },
      "created_at":"2020-09-21T23:21:52.014Z",
      "updated_at":"2020-09-21T23:21:52.014Z"
   },
   {
      "id":2,
      "device_id":1,
      "interval":300,
      "next_wakeup":null,
      "battery_level":86,
      "sdSizeMB":24076,
      "sdFreeMB":22835,
      "operator_version":"operator-20200908",
      "shield_fw_version":"V1.0.0",
      "timezone":"America/Toronto",
      "powersource":"Battery",
      "vbatt":4.06,
      "vsys":4.05,
      "mode":"RUN",
      "temperature":36,
      "shield_datetime":"2020-01-01T10:07:40.000Z",
      "rpi_datetime":"2020-09-21T19:21:28.529Z",
      "uptime_at_start":"2000-01-01T00:00:04.270Z",
      "uptime_at_upload":"2000-01-01T00:00:12.900Z",
      "payload":{
         "interval":"300",
         "battery_level":"86",
         "sdSizeMB":"24076.62109375",
         "sdFreeMB":"22835.26171875",
         "operator_version":"operator-20200908",
         "shield_fw_version":"V1.0.0",
         "timezone":"America/Toronto",
         "powersource":"Battery",
         "vbatt":"4.06V",
         "vsys":"4.05V",
         "mode":"RUN",
         "temperature":"36",
         "shield_datetime":"2020-01-01 10:07:40",
         "rpi_datetime":"2020-09-21 19:21:28.529990",
         "uptime_at_start":"0:00:04.270000",
         "uptime_at_upload":"0:00:12.900000"
      },
      "created_at":"2020-09-21T23:33:56.095Z",
      "updated_at":"2020-09-21T23:33:56.095Z"
   }
]
```
# /api/v4/devices/:UUID/heartbeats/:ID (show)
This GET endpoint will return a JSON with the heartbeat of the ID defined in the URL of the device you specify with the UUID in the URL.


```shell
   curl "http://localhost:3000/api/v4/devices/:UUID/heartbeats/:ID"
```
```json
{
   "id":1,
   "device_id":1,
   "interval":300,
   "next_wakeup":null,
   "battery_level":85,
   "sdSizeMB":24076,
   "sdFreeMB":22835,
   "operator_version":"operator-20200908",
   "shield_fw_version":"V1.0.0",
   "timezone":"America/Toronto",
   "powersource":"Battery",
   "vbatt":4.06,
   "vsys":4.05,
   "mode":"CONFIG",
   "temperature":33,
   "shield_datetime":"2020-01-01T09:55:35.000Z",
   "rpi_datetime":"2020-09-21T19:21:28.708Z",
   "uptime_at_start":"2000-01-01T00:00:04.500Z",
   "uptime_at_upload":"2000-01-01T00:00:10.820Z",
   "payload":{
      "interval":"300",
      "battery_level":"85",
      "sdSizeMB":"24076.62109375",
      "sdFreeMB":"22835.265625",
      "operator_version":"operator-20200908",
      "shield_fw_version":"V1.0.0",
      "timezone":"America/Toronto",
      "powersource":"Battery",
      "vbatt":"4.06V",
      "vsys":"4.05V",
      "mode":"CONFIG",
      "temperature":"33",
      "shield_datetime":"2020-01-01 09:55:35",
      "rpi_datetime":"2020-09-21 19:21:28.708734",
      "uptime_at_start":"0:00:04.500000",
      "uptime_at_upload":"0:00:10.820000"
   },
   "created_at":"2020-09-21T23:21:52.014Z",
   "updated_at":"2020-09-21T23:21:52.014Z"
}
```
# /api/v4/devices/:UUID/stills (index)
This GET endpoint will return the stills of a given device in a range date.

This endpoints need the following querystrings:

QueryString | format
----------- | -------
date_range_start | YYYY-MM-DD
date_range_end | YYYY-MM-DD
time_range_start | hh:mm
time_range_end | hh:mm

```shell
   curl -i -H "Accept: application/json" -H "Content-Type: application/json" -X GET "http://localhost:3000/api/v2/sources/aa0505f5-5050-5137-6a70-a9c21eaf3a0e/stills?date_range_start=2014-12-12&date_range_end=2019-12-12&time_range_start=12:00&time_range_end=14:00"
```

```json
[
    {
        "id": 2550395,
        "thumb_url": "https://zeitings-live.s3.amazonaws.com/stills/1902/thumb/20201013120850.jpg",
        "file_name": "20201013120850.jpg",
        "image_url": "https://zeitings-live.s3.amazonaws.com/stills/1902/original/20201013120850.jpg",
        "captured_at_local_tz": "2020-10-13 12:08",
        "bb_image_url": "https://zeitings-live.s3.amazonaws.com/stills/1902/bb/20201013120850.jpg",
        "ai_threshold": 50,
        "ai_relevant_objects": "{'person': True, 'car': True, 'truck': True}",
        "brightness": 46.69
    },
    {
        "id": 2550432,
        "thumb_url": "https://zeitings-live.s3.amazonaws.com/stills/1902/thumb/20201013123850.jpg",
        "file_name": "20201013123850.jpg",
        "image_url": "https://zeitings-live.s3.amazonaws.com/stills/1902/original/20201013123850.jpg",
        "captured_at_local_tz": "2020-10-13 12:38",
        "bb_image_url": "https://zeitings-live.s3.amazonaws.com/stills/1902/bb/20201013123850.jpg",
        "ai_threshold": 50,
        "ai_relevant_objects": "{'person': True, 'car': True, 'truck': True}",
        "brightness": 47.22
    }
]
```

# /api/v4/devices/:UUID/stills/:ID (show)
This GET endpoint will return the still object with the given ID of a given device.

```shell
   curl "http://localhost:3000/api/v4/devices/:UUID/stills/:ID"
```

```json
{
    "id": 2550394,
    "created_at": "2020-10-13T16:08:58.497Z",
    "updated_at": "2020-10-13T16:09:06.553Z",
    "image_file_file_name": "20201013120848.jpg",
    "image_file_content_type": null,
    "image_file_file_size": 6647903,
    "image_file_updated_at": null,
    "captured_at": "2020-10-13T12:08:48.000Z",
    "source_id": 1895,
    "data": null,
    "imagemagick": null,
    "intel": null,
    "yolo": null,
    "scheduled_for_analytics": false,
    "uploaded_ok": true,
    "bb_image_uploaded": false,
    "brightness": 43.81,
    "processing_completed": true,
    "diff_to_previous": null,
    "height": 3040,
    "width": 4056,
    "deleted": false,
    "file_deleted": false,
    "image_url": "https://zeitings-live.s3.amazonaws.com/stills/1895/original/20201013120848.jpg",
    "bb_image_url": "https://zeitings-live.s3.amazonaws.com/stills/1895/bb/20201013120848.jpg",
    "thumb_url": "https://zeitings-live.s3.amazonaws.com/stills/1895/thumb/20201013120848.jpg",
    "ai_threshold": 50,
    "ai_relevant_objects": "{'person': True, 'car': True, 'truck': True}"
}
```


# /api/v4/devices/:UUID/stills/latest

This GET endpoint returns the latest still as an image.


```shell
   curl "http://localhost:3000/api/v4/devices/:UUID/stills/latest"
```

```json
   No JSON returned in this endpoint, only an image
```