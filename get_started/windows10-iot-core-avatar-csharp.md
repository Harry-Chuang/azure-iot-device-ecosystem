---
platform: windows 10 iot core
device: avatar
language: csharp
---

Run a simple Csharp sample on Inventec Avatar device running Windows 10 IoT Core
===
---

# Table of Contents

-   [Introduction](#Introduction)
-   [Step 1: Prerequisites](#Prerequisites)
-   [Step 2: Prepare your Device](#PrepareDevice)
-   [Step 3: Build and Run the Sample](#Build)
-   [Next Steps](#NextSteps)

<a name="Introduction"></a>
# Introduction

**About this document**

This document describes how to connect Inventec Avatar device running Windows 10 IoT Core with Azure IoT SDK. This multi-step process includes:
-   Configuring Azure IoT Hub
-   Registering your IoT device
-   Build and deploy Azure IoT SDK on device

<a name="Prerequisites"></a>
# Step 1: Prerequisites

You should have the following items ready before beginning the process:

-   [Setup your IoT hub][lnk-setup-iot-hub]
-   [Provision your device and get its credentials][lnk-manage-iot-hub]
-   Inventec Avatar device.
-   [Azure SDK for .NET](https://www.microsoft.com/en-us/download/details.aspx?id=48178)
-   Windows 10 IoT Core Package
-   Virtual Ethernet

#### Install Visual Studio 2015 and Tools
-   To create Windows IoT Core solutions, you will need to install [Visual Studio 2015](https://www.visualstudio.com/en-us/products/vs-2015-product-editions.aspx). You can install any edition of Visual Studio, including the free Community edition.

    Make sure to select the **Universal Windows App Development Tools**, the component required for writing apps Windows 10:

<a name="PrepareDevice"></a>
# Step 2: Prepare your Device

-   Flash Windows 10 IoT Core image on to the device.

-   On the first boot of the device only, do the following:
    1. Plug the device into a USB port on your computer.
    2. Use `ffutool -list` to check if the device is enumerated correctly in the system. 
    3. Use `ffutool -massstorage` to put the device into mass storage mode.
    4. Configure BCD store using the following command to enable KDNet debugging (`<Host IP>` is the IP address of your PC, `E:` is the storage drive of your module):
        
        ```
        bcdedit /store E:\efiesp\efi\Microsoft\Boot\BCD /dbgsettings net HOSTIP:<Host IP> PORT:50000 KEY:1.2.3.4
        bcdedit /store E:\efiesp\efi\Microsoft\Boot\BCD -set {default} debug on
        bcdedit /store E:\efiesp\efi\Microsoft\Boot\BCD -set {dbgsettings} busparams 1
        bcdedit /store E:\efiesp\efi\Microsoft\Boot\BCD -set {globalsettings} forceffumode off
        ```

    5. Unplug the device.

- On your computer, run **Virutal Ethernet** (???VirtEth.exe??? ) as administrator.

- Plug the device into a USB port on your computer.

- Wait for a few minutes for the device to enumerate, open **WindowsIoTCoreWatcher** to find your device.

<a name="Build"></a>
# Step 3: Build and Run the Sample

<a name="Step_3_1:_Connect"/>
## 3.1 Connect the Device

-   On your computer, run Virtual Ethernet as administrator.
-   Plug the device into a USB port on your computer.

<a name="Step_3_2:_Build"/>
## 3.2  Build the Samples

-   Start a new instance of Visual Studio 2015. Open the **iothub_csharp_client.sln** solution (/azure-iot-sdk-csharp) from your local copy of the repository.

-   In Visual Studio, from **Solution Explorer**, navigate to the **UWPSample(Universal Windows)** project.

-   Locate the following code in the **ConnectionStrings.cs** file:

        public const string DeviceConnectionString = "<replace>";

-   Replace the above placeholder with device connection string you obtained in [Step 1](#Step-1:-Prerequisites) and save the changes.

-   Choose the right architecture (ARM) and set the debugging method to "Remote Machine":

-   To deploy the binaries on your device, right-click on the UWPSample project in the **Solution Explorer**, select **Properties** and navigate to the **Debug** tab:

    Type in the IP Address of your device. Make sure the "Use authentication" box is unchecked.

-   Build the solution.


<a name="Step_3_3:_Run"/>
## 3.3 Run and Validate the Samples


### 3.3.1 Send Device Events to IoT Hub
-   On Windows, refer "Monitor device-to-cloud events" in [DeviceExplorer Usage document][lnk-device-explorer] to see the data your device is sending.
-   If you are running other OS, please use the JavaScript tool [iot-hub explorer tool][lnk-iothub-explorer]
-   In Visual Studio, from **Solution Explorer**, right-click the **UWPSample(Universal Windows)** project, click **Debug &minus;&gt; Start new instance** to build and run the sample. 

-   You should be able to see the events received in the DeviceExplorer's data tab.


### 3.3.2 Receive messages from IoT Hub

-   On Windows, refer "Send cloud-to-device messages" in [DeviceExplorer Usage document][lnk-device-explorer] for instructions on sending messages to device.

-   If you are running other OS, please use the JavaScript tool [iot-hub explorer tool][lnk-iothub-explorer]

<a name="NextSteps"></a>
# Next Steps

You have now learned how to run a sample application that collects sensor data and sends it to your IoT hub. To explore how to store, analyze and visualize the data from this application in Azure using a variety of different services, please click on the following lessons:

-   [Manage cloud device messaging with iothub-explorer]
-   [Save IoT Hub messages to Azure data storage]
-   [Use Power BI to visualize real-time sensor data from Azure IoT Hub]
-   [Use Azure Web Apps to visualize real-time sensor data from Azure IoT Hub]
-   [Weather forecast using the sensor data from your IoT hub in Azure Machine Learning]
-   [Remote monitoring and notifications with Logic Apps]   

[Manage cloud device messaging with iothub-explorer]: https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-explorer-cloud-device-messaging
[Save IoT Hub messages to Azure data storage]: https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-store-data-in-azure-table-storage
[Use Power BI to visualize real-time sensor data from Azure IoT Hub]: https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-live-data-visualization-in-power-bi
[Use Azure Web Apps to visualize real-time sensor data from Azure IoT Hub]: https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-live-data-visualization-in-web-apps
[Weather forecast using the sensor data from your IoT hub in Azure Machine Learning]: https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-weather-forecast-machine-learning
[Remote monitoring and notifications with Logic Apps]: https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-monitoring-notifications-with-azure-logic-apps
[lnk-setup-iot-hub]: ../setup_iothub.md
[lnk-manage-iot-hub]: ../manage_iot_hub.md
[lnk-device-explorer]: ../../tools/DeviceExplorer/doc/how_to_use_device_explorer.md
[lnk-iothub-explorer]: ../../tools/iothub-explorer/readme.md

