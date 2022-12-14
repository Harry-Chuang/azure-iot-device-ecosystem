---
platform: windows 10
device: mpos
language: csharp
---

Run a simple C-Sharp sample on mPOS device running Windows 10 Enterprise
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

This document describes how to connect mPOS device running Windows 10 Pro with Azure IoT SDK. This multi-step process includes:
-   Configuring Azure IoT Hub
-   Registering your IoT device
-   Build and deploy Azure IoT SDK on device

<a name="Prerequisites"></a>
# Step 1: Prerequisites

You should have the following items ready before beginning the process:

-   [Prepare your development enviornment][setup-devbox-windows]
-   [Setup your IoT hub][lnk-setup-iot-hub]
-   [Provision your device and get its credentials][lnk-manage-iot-hub]
-   mPOS device.
-  	Monitor, VGA Cable, USB Keyboard/Mouse, and the Internet connection.
   

<a name="PrepareDevice"></a>
# Step 2: Prepare your Device

-   Connect Ethernet cable to the WAN port on mPOS device and connect the other end to your switch/hub/router.

-   Connect a USB Keyboard and Mouse to the back USB ports of your mPOS device. Using an HDMI cable (The maximum supported screen resolution is 1280 x 1024 or 1920 x 1080 (depends on models)), also connect a monitor to the device.

-   Connect power cord & power on.

-   Wait until the operating system is ready.


<a name="Build"></a>
# Step 3: Build SDK and Run the sample

## 3.1 Connect the Device
- Connect the board to your network using an Ethernet cable. This step is required, as the sample depends on internet access.

## 3.2 Build the Samples
-  Start a new instance of Visual Studio 2015. Open the **iothub_csharp_client.sln** solution (/azure-iot-sdk-csharp) from your local copy of the repository.

-  In Visual Studio, from **Solution Explorer**, navigate to the **UWPSample(Universal Windows)** project.
 
-  Locate the following code in the **ConnectionStrings.cs** file:

		public const string DeviceConnectionString = "<replace>";	

-  Replace the above placeholder with device connection string you obtained in Step 1 and save the changes.

-  Choose the right architecture (x86 or ARM, depending on your device) and set the debugging method to "Remote Machine":

-  To deploy the binaries on your device, right-click on the **UWPSample** project in the **Solution Explorer**, select **Properties** and navigate to the **Debug** tab:???

-  Type in the name of your device. Make sure the "Use authentication" box is unchecked.

-  Build the solution.


## 3.3 Run and Validate the Samples

###  3.3.1 Send Device Events to IoT Hub
-	In Visual Studio, from **Solution Explorer**, right-click the **UWPSample(Universal Windows)** project, click **Debug ???> Start new instance** to build and run the sample.
 
-	See [Manage IoT Hub][lnk-manage-iot-hub] to learn how to observe the messages IoT Hub receives from the application.

### 3.3.2 Receive messages from IoT Hub
???	See [Manage IoT Hub][lnk-manage-iot-hub] to learn how to send cloud-to-device messages to the application.


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
[setup-devbox-windows]: https://github.com/Azure/azure-iot-sdk-c/blob/master/doc/devbox_setup.md
[lnk-setup-iot-hub]: ../setup_iothub.md
[lnk-manage-iot-hub]: ../manage_iot_hub.md
