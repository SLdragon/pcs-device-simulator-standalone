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