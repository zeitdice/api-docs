---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript
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
curl "/api/v4/devices"
  -H "Authorization: meowmeowmeow"
```

```javascript
  $.getJSON( "/api/v4/devices", function(data) {
    console.log(data);
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