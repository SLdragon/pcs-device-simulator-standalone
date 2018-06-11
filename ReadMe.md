# PCS-Device-Simulator-Standalone
This repository contains device simulation project which can be deploy standalone.

# How to deploy
1. Open Project in Visual Studio 2017

2. Publish pcs-storage-adapter and pcs-device-simulation to Azure App Service

3. Deploy IoTHub in Azure and record IoT Hub connection string

4. Deploy Document DB in Azure and record Document DB connection string

5. In pcs-storage-adapter Application settings, add environment variable:
    ```
    PCS_STORAGEADAPTER_DOCUMENTDB_CONNSTRING "Your document db connection string"
    ```

6. In pcs-device-simulation Applictaion settings, add environment variable:
    ```
    PCS_STORAGEADAPTER_WEBSERVICE_URL "Storage Adapter URL"
    PCS_IOTHUB_CONNSTRING "Your IoTHub connection string"
    ```


# Create and Start a simulation

1. Create a default simulation
```
    POST /v1/simulations?template=default
    Content-Type: application/json; charset=utf-8
```

2. Start a simulation
```
    PATCH /v1/simulations/1
    Content-Type: application/json; charset=utf-8
```

Full document about the Restful API can be found [here](https://github.com/Azure/device-simulation-dotnet/wiki/%5BAPI-Specifications%5D-Simulations)


# Simulated Device Message Format


### chiller

```
    [
        {
            "temperature":77.8597806285181,
            "temperature_unit":"F",
            "humidity":66.5906302524221,
            "humidity_unit":"%",
            "pressure":148.429367613713,
            "pressure_unit":"psig"
        }
    ]

    Properties:
    'iothub-message-schema': 'chiller-sensors;v1'
    'iothub-creation-time-utc': '2018-06-11T02:06:54.2016944Z'
    '$$CreationTimeUtc': '2018-06-11T02:06:54+00:00'
    '$$MessageSchema': 'chiller-sensors;v1'
    '$$ContentType': 'JSON'
```


### elevator
```
    [
        {
            "floor":1,
            "vibration":0,
            "vibration_unit":"mm",
            "temperature":75.7448166771768,
            "temperature_unit":"F"
        }
    ]
    Properties:
    'iothub-message-schema': 'elevator-sensors;v1'
    'iothub-creation-time-utc': '2018-06-11T02:09:33.5351856Z'
    '$$CreationTimeUtc': '2018-06-11T02:09:33+00:00'
    '$$MessageSchema': 'elevator-sensors;v1'
    '$$ContentType': 'JSON'
```

### engine
```
    [
        {
            "fuellevel":70,
            "fuellevel_unit":"Gal",
            "coolant":7646.04831266731,
            "coolant_unit":"ohm",
            "vibration":9.84239173556789,
            "vibration_unit":"mm"
        }
    ]
    Properties:
    'iothub-message-schema': 'engine-sensors;v1'
    'iothub-creation-time-utc': '2018-06-11T02:11:38.2901747Z'
    '$$CreationTimeUtc': '2018-06-11T02:11:38+00:00'
    '$$MessageSchema': 'engine-sensors;v1'
    '$$ContentType': 'JSON'
```

### prototype

```
    [
        {
            "temperature":56.1137891724889,
            "temperature_unit":"F",
            "pressure":147.129878322422,
            "pressure_unit":"psig",
            "latitude":47.612514,
            "longitude":-122.204184
        }
    ]
    Properties:
    'iothub-message-schema': 'prototype-sensors;v1'
    'iothub-creation-time-utc': '2018-06-11T02:12:52.6080173Z'
    '$$CreationTimeUtc': '2018-06-11T02:12:52+00:00'
    '$$MessageSchema': 'prototype-sensors;v1'
    '$$ContentType': 'JSON'
```


### truck

```
    [
        {
            "latitude":47.4467466983126,
            "longitude":-122.294169321976,
            "speed": 31.2636752281169,
            "speed_unit":"mph",
            "temperature":9.70585435366944,
            "temperature_unit":"F"
        }
    ]
    Properties:
    'iothub-message-schema': 'truck-sensors;v1'
    'iothub-creation-time-utc': '2018-06-11T02:14:11.4201078Z'
    '$$CreationTimeUtc': '2018-06-11T02:14:11+00:00'
    '$$MessageSchema': 'truck-sensors;v1'
    '$$ContentType': 'JSON'
```