---
platform: windows 10 iot enterprise ltsb
device: bnc-153t-d
language: c
---

Run a simple C sample on BNC-153T-D device running Windows 10 IoT Enterprise LTSB
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

This document describes how to connect BNC-153T-D device running Windows 10 IoT Enterprise LTSB with Azure IoT SDK. This multi-step process includes:
-   Configuring Azure IoT Hub
-   Registering your IoT device
-   Build and deploy Azure IoT SDK on device

<a name="Prerequisites"></a>
# Step 1: Prerequisites

You should have the following items ready before beginning the process:

-   Computer with GitHub installed and access to the [azure-iot-sdks GitHub](https://github.com/Azure/azure-iot-sdks) private repository.
-   Install any version of [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx). 
    Make sure you have following components selected:
    -   Programming Languages
        -   Visual C++
            -   Common Tools for Visual C++ 2017
            -   Microsoft Foundation Classes for C++
    -   Windows and Web Development
        -   Microsoft SQL server Data Tools
    -   Universal Windows App Development Tools
        -   Tools and Windows 10 SDK
        -   Windows 10 SDK
-   Install [Microsoft Azure SDK for .NET](http://www.microsoft.com/download/details.aspx?id=48178)
-   [Setup your IoT hub][lnk-setup-iot-hub]
-   [Provision your device and get its credentials][lnk-manage-iot-hub]
-   BNC-153T-D device.   

<a name="PrepareDevice"></a>
# Step 2: Prepare your Device

-   Install Windows 10 IoT Enterprise LTSB on <https://github.com/Azure/azure-iot-sdks>
-   Create a bootable USB Drive. Please follow this guide on [how to create a bootable drive](https://www.microsoft.com/en-us/download/windows-usb-dvd-download-tool).
-   Insert the bootable USB Drive from the previous step into your BNC-153T-D. Turn on your BNC-153T-D device and press the Delete key.
-   Change the BIOS Boot option filter to UEFI and Legacy.
-   Change the BIOS OS Selection to "Windows 10".
-   Change the Boot Option Priorities to boot from your USB Drive.
-   Save changes and restart your BNC-153T-D. Follow on screen instructions to install Windows Operating System on your BNC-153T-D.

<a name="Build"></a>
# Step 3: Build SDK and Run the sample

-   Start a new instance of Visual Studio 2017. Open the **iothub\_client\_sample\_http.sln** solution in the  **azureIotSDks\c\iothub\_client\samples\iothub\_client\_sample\_http\windows** folder in your local copy of the repository.

-   In Visual Studio, in **Solution Explorer**, navigate to **samples** folder.

-   In the **iothub\_client\_sample\_http** project, open the **iothub\_client\_sample\_http.c** file.

-   Locate the following code in the file:

        static const char* connectionString = "[device connection string]";

-   Replace the above placeholder with device connection string you obtained in [Step 1](#Step-1:-Prerequisites) and save the changes.

-   In visual Studio, under Solution Explorer, right-click the **iothub\_client\_sample\_http** project, click **Debug ???> Start new instance** to build and run the sample. The console displays messages as the application sends device-to-cloud messages to IoT Hub.

-   See [Manage IoT Hub][lnk-manage-iot-hub] to learn how to observe the messages IoT Hub receives from the application and how to send cloud-to-device messages to the application.

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
[setup-devbox-windows]: https://github.com/Azure/azure-iot-sdks/blob/master/c/doc/devbox_setup.md
[lnk-setup-iot-hub]: ../setup_iothub.md
[lnk-manage-iot-hub]: ../manage_iot_hub.md
