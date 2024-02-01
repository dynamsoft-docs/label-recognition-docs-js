---
layout: default-layout
title: JavaScript User Guide - Dynamsoft Label Recognizer
description: This is the user guide page of Dynamsoft Label Recognizer for JavaScript Language.
keywords: javascript, user guide
needAutoGenerateSidebar: true
needGenerateH3Content: true
permalink: /programming/javascript/user-guide-v2.2.11.html
---

<!--The original doc is hosted here => https://github.com/dynamsoft-docs/label-recognition-docs/blob/master/programming/javascript/user-guide.md -->

# Dynamsoft Label Recognizer for Your Website

With Dynamsoft Label Recognizer JavaScript Edition, you can add the capability of reading passport MRZs, ID cards, VIN numbers, and various other fixed text fields in your web application with just a few lines of code.

![version](https://img.shields.io/npm/v/dynamsoft-label-recognizer.svg)
![downloads](https://img.shields.io/npm/dm/dynamsoft-label-recognizer.svg)
![jsdelivr](https://img.shields.io/jsdelivr/npm/hm/dynamsoft-label-recognizer.svg)
![vulnerabilities](https://img.shields.io/snyk/vulnerabilities/npm/dynamsoft-label-recognizer.svg)

Once integrated, your users can open your website in a browser, access their cameras, and read the intended text directly from the video input.

In this guide, you will learn step by step on how to integrate this SDK into your website.

<span style="font-size:20px">Table of Contents</span>

- [Dynamsoft Label Recognizer for Your Website](#dynamsoft-label-recognizer-for-your-website)
  - [\[TODO\]Example Usage - MRZ Reading](#todoexample-usage---mrz-reading)
    - [Understand the code](#understand-the-code)
      - [About the code](#about-the-code)
    - [Run the example](#run-the-example)
    - [Check out the official sample for MRZ reading](#check-out-the-official-sample-for-mrz-reading)
  - [Building your own page](#building-your-own-page)
    - [Include the SDK](#include-the-sdk)
      - [Use a public CDN](#use-a-public-cdn)
      - [Host the SDK yourself](#host-the-sdk-yourself)
    - [Prepare the SDK](#prepare-the-sdk)
      - [Specify the license](#specify-the-license)
      - [Specify the location of the "engine" files (optional)](#specify-the-location-of-the-engine-files-optional)
      - [\[TODO\] Add a visual cue about the loading of a .data file](#todo-add-a-visual-cue-about-the-loading-of-a-data-file)
    - [Set up and start image processing](#set-up-and-start-image-processing)
      - [Preload the module](#preload-the-module)
      - [Create a CaptureVisionRouter object](#create-a-capturevisionrouter-object)
      - [Connect an image source](#connect-an-image-source)
      - [\[TODO\]Register a result receiver](#todoregister-a-result-receiver)
      - [\[TODO\]Start the process](#todostart-the-process)
    - [\[TODO\]Customize the process](#todocustomize-the-process)
      - [Adjust the preset template settings](#adjust-the-preset-template-settings)
      - [Edit the preset templates directly](#edit-the-preset-templates-directly)
      - [Filter the results (Important)](#filter-the-results-important)
        - [Option 1: Verify results across multiple frames](#option-1-verify-results-across-multiple-frames)
        - [Option 2: Eliminate redundant results detected within a short time frame](#option-2-eliminate-redundant-results-detected-within-a-short-time-frame)
      - [Add feedback](#add-feedback)
    - [Customize the UI](#customize-the-ui)
  - [API Documentation](#api-documentation)
  - [System Requirements](#system-requirements)
  - [Release Notes](#release-notes)
  - [Next Steps](#next-steps)

## [TODO]Example Usage - MRZ Reading

Let's start by testing the "MRZ Reading" example of the SDK which demonstrates how to enable a web page to read the machine-readable zones (MRZ) found on passports, ID cards, VISAs, etc. from a live video stream.

**Basic Requirements**
  - Internet connection
  - [A supported browser](#system-requirements)
  - Camera access

### Understand the code

The complete code of the "MRZ Reading" example is shown below

```html
<!DOCTYPE html>
<html>

<head>
    <title>MRZ Reading</title>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-label-recognizer@2.2.11/dist/dlr.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@3.0.1/dist/dce.js"></script>
</head>

<body>
    <script>
        // The following line specifies a license good for 24 hours, you can visit https://www.dynamsoft.com/customer/license/trialLicense?utm_source=guide&product=dlr&package=js to get your own trial license good for 30 days.
        Dynamsoft.DLR.LabelRecognizer.license = 'DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9';
        // The following code initializes and uses the SDK.
        (async () => {
            Dynamsoft.DLR.LabelRecognizer.onResourcesLoadStarted = (resourcePath) => {
                // In this event handler, you can display a visual cue to show that the model file is being downloaded.
                console.log("Loading " + resourcePath);
            };
            Dynamsoft.DLR.LabelRecognizer.onResourcesLoaded = (resourcePath) => {
                // In this event handler, you can close the visual cue if it was displayed.
                console.log("Finished loading " + resourcePath);
            };
            let recognizer = await Dynamsoft.DLR.LabelRecognizer.createInstance();
            let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
            let options = {
                resultsHighlightBaseShapes: Dynamsoft.DCE.DrawingItem
            };
            await recognizer.setImageSource(cameraEnhancer, options);
            // The following line sets up the recognizer to read MRZ, which means the SDK will load a model file specifically designed for MRZ.
            await recognizer.updateRuntimeSettingsFromString("video-mrz");
            // onMRZRead is a callback specifically designed for MRZ.
            recognizer.onMRZRead = (txt, results) => {
                // Here we simply show the text in the browser console.
                console.log("Found and read a MRZ:")
                console.log(txt);
            };
            // Beginning of redundant code: just to demonstrate the use of onImageRead and onUniqueRead events
            recognizer.onImageRead = results => {
                console.log("Finished reading an image:")
                for (let result of results) {
                    for (let lineResult of result.lineResults) {
                        console.log(lineResult.text);
                    }
                }
            };
            recognizer.onUniqueRead = (txt, results) => {
                alert(txt);
            };
            // End of redundant code.
            await recognizer.startScanning(true);
        })();
    </script>
</body>

</html>
```

<p align="center" style="text-align:center; white-space: normal; ">
  <a target="_blank" href="https://jsfiddle.net/DynamsoftTeam/kc35htxd/" title="Run via JSFiddle">
    <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/jsfiddle.svg" alt="Run via JSFiddle" width="20" height="20" style="width:20px;height:20px;">
  </a>
</p>

-----

#### About the code

* `LabelRecognizer.createInstance()`: This method creates a `LabelRecognizer` object called `recognizer`.

* `CameraEnhancer.createInstance()`: this method creates a `CameraEnhancer` object called `cameraEnhancer`, which is used to control the camera as well as the default user interface. Once `cameraEnhancer` is bound to `recognizer` via `setImageSource()`, it can send video frames from the camera to `recognizer` for recognition as well as highlight the recognized text areas directly in the video feed.

* `updateRuntimeSettingsFromString("video-mrz")`: this sets up `recognizer` with a built-in template optimized for reading MRZ from continuous video frames. Note that all built-in templates starting with "video-" are only valid after `cameraEnhancer` has been bound to `recognizer`.

  > Built-in templates include
  >
  >| Name | Description |
  >|:-:|:-:|
  >| `number` | For pure number recognition. |
  >| `numberLetter` | For number and English letter recognition. |
  >| `numberUpperCase` | For number and uppercase English letter recognition. |
  >| `letter` | For pure English letter recognition. |
  >| `MRZ` | For MRZ (machine-readable zone) recognition. |
  >| `passportMRZ` | For passport MRZ recognition. |
  >| `visaMRZ` | For Visa (Country not Credit Card) MRZ recognition. |
  >| `VIN` | For VIN (vehicle identification number) recognition. |
  >| `VIN_NA` | For North American VIN (vehicle identification number) recognition. |
  >
  > When recognizing from video input, add the prefix "video-" for a slightly different template optimized for continuous frame recognition. For example, use `video-passportMRZ` to read the MRZ on passports with a camera.

* `onMRZRead`: This event is only used with one of the templates "MRZ", "passportMRZ" and "visaMRZ" (similarly, "onVINRead" is only used with either "VIN" or "VIN_NA"). It is triggered each time the SDK has identified and finished the recognition of a MRZ zone. The `results` object contains 2 or 3 lines of text results corresponding to the 2 or 3 lines in the MRZ. In this example, we simply print the results to the browser console.

> The events `onImageRead` and `onUniqueRead` are used in the code but they are not required. You can compare the results returned in the 3 events and see what the differences are.

* `onImageRead`: This event is triggered every time the SDK finishes scanning a video frame image. The `results` object contains all the text results that the SDK has found on this frame. In this example, we print the results to the browser console.

* `onUniqueRead`: This event is triggered when the SDK finds a new text, which is not a duplicate among multiple frames. `txt` holds the text value while `results` is an array of objects that hold details of the text. In this example, an alert will be displayed for this new text.

* `startScanning(true)`: Starts continuous video frame scanning. The return value is a Promise which resolves when the camera is opened, the video shows up on the page and the scanning begins (which means `cameraEnhancer` has started feeding `recognizer` with frames to recognize).

### Run the example

Create a text file with the name "readMRZ.html", fill it with the code above and save. After that, open the example page in a browser, allow the page to access your camera and the video will show up on the page. After that, you can point the camera at something with a simple line of text to read it.

> You can also just test it at [https://jsfiddle.net/DynamsoftTeam/kc35htxd/](https://jsfiddle.net/DynamsoftTeam/kc35htxd/)

Remember to open the browser console to check the resulting text. Also note that the found text will be highlighted on the UI.

*Note*:

* Although the page should work properly when opened directly as a file ("file:///"), it's recommended that you deploy it to a web server before accessing it. Also, most browsers require a secure connection (HTTPS) to access the cameras, so deploying the page to a HTTPS website is the best choice.
* On first use, you need to wait a few seconds for the SDK to initialize and download the necessary model file.
* The license "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9" used in this sample is an online license and requires network connection to work.

If the test doesn't go as expected, you can [contact us](https://www.dynamsoft.com/company/contact/?utm_source=guide).

### Check out the official sample for MRZ reading

You can also try the official sample for MRZ reading ([test in Github](https://dynamsoft.github.io/label-recognizer-javascript-samples/use-case/mrz-read-and-parse/) or [check the code](https://github.com/Dynamsoft/label-recognizer-javascript-samples/tree/main/use-case/mrz-read-and-parse)). This sample also demonstrates how to parse the MRZ text into meaningful fields.

## Building your own page

In this section, we'll break down and show all the steps required to build a web page that reads the machine readable zone (MRZ) on a passport.

### Include the SDK

To utilize the SDK, the initial step involves including the corresponding resource files:

* `core.js` encompasses common classes, interfaces, and enumerations that are shared across all Dynamsoft SDKs.
* `license.js` introduces the `LicenseManager` class, which manages the licensing for all Dynamsoft SDKs.
* `utility.js` encompasses auxiliary classes that are shared among all Dynamsoft SDKs.
* `dlr.js` defines interfaces and enumerations specifically tailored to the label recognizer module.
* `cvr.js` introduces the `CaptureVisionRouter` class, which governs the entire image processing workflow.
* `dce.js` comprises classes that offer camera support and basic user interface functionalities.

#### Use a public CDN

The simplest way to include the SDK is to use either the [jsDelivr](https://jsdelivr.com/) or [UNPKG](https://unpkg.com/) CDN. The "hello world" example above uses **jsDelivr**.

- jsDelivr

  ```html
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-core@3.0.20/dist/core.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-license@3.0.20/dist/license.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-utility@1.0.20/dist/utility.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-label-recognizer@3.0.20/dist/dlr.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-capture-vision-router@2.0.20/dist/cvr.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@4.0.1/dist/dce.js"></script>
  ```

- UNPKG  

  ```html
  <script src="https://unpkg.com/dynamsoft-core@3.0.20/dist/core.js"></script>
  <script src="https://unpkg.com/dynamsoft-license@3.0.20/dist/license.js"></script>
  <script src="https://unpkg.com/dynamsoft-utility@1.0.20/dist/utility.js"></script>
  <script src="https://unpkg.com/dynamsoft-label-recognizer@3.0.20/dist/dlr.js"></script>
  <script src="https://unpkg.com/dynamsoft-capture-vision-router@2.0.20/dist/cvr.js"></script>
  <script src="https://unpkg.com/dynamsoft-camera-enhancer@4.0.1/dist/dce.js"></script>
  ```

In some rare cases, you might not be able to access the CDN. If this happens, you can use the following files for the test. 

- [dynamsoft-core@3.0.20]()
- [dynamsoft-license@3.0.20]()
- [dynamsoft-utility@1.0.20]()
- [dynamsoft-label-recognizer@3.0.20]()
- [dynamsoft-capture-vision-router@2.0.20]()
- [dynamsoft-camera-enhancer@4.0.1]()

However, please **DO NOT** use the above files in a production application as they are for temporary testing purposes only.

#### Host the SDK yourself

Besides using the public CDN, you can also download the SDK and host its files on your own server or a commercial CDN before including it in your application.

Options to download the SDK:

- From the website

  [Download Dynamsoft Barcode Reader JavaScript Package](https://www.dynamsoft.com/barcode-reader/downloads/?ver=10.0.20&utm_source=guide" title="Download the JavaScript Package){:target="_blank"}

- yarn

  ```cmd
  yarn add dynamsoft-core@3.0.20 --save
  yarn add dynamsoft-license@3.0.20 --save
  yarn add dynamsoft-utility@1.0.20 --save
  yarn add dynamsoft-label-recognizer@3.0.20 --save
  yarn add dynamsoft-capture-vision-router@2.0.20 --save
  yarn add dynamsoft-camera-enhancer@4.0.1 --save
  ```

- npm

  ```cmd
  npm install dynamsoft-core@3.0.20 --save
  npm install dynamsoft-license@3.0.20 --save
  npm install dynamsoft-utility@1.0.20 --save
  npm install dynamsoft-label-recognizer@3.0.20 --save
  npm install dynamsoft-capture-vision-router@2.0.20 --save
  npm install dynamsoft-camera-enhancer@4.0.1 --save
  ```

Depending on how you downloaded the SDK and how you intend to use it, you can typically include it like this:

```html
<script src="./dynamsoft/distributables/dynamsoft-core@3.0.20/dist/core.js"></script>
<script src="./dynamsoft/distributables/dynamsoft-license@3.0.20/dist/license.js"></script>
<script src="./dynamsoft/distributables/dynamsoft-utility@1.0.20/dist/utility.js"></script>
<script src="./dynamsoft/distributables/dynamsoft-label-recognizer@3.0.20/dist/dlr.js"></script>
<script src="./dynamsoft/distributables/dynamsoft-capture-vision-router@2.0.20/dist/cvr.js"></script>
<script src="./dynamsoft/distributables/dynamsoft-camera-enhancer@4.0.1/dist/dce.js"></script>
```

or

```html
<script src="/node_modules/dynamsoft-core/dist/core.js">
<script src="/node_modules/dynamsoft-license/dist/license.js">
<script src="/node_modules/dynamsoft-utility/dist/utility.js"></script>
<script src="/node_modules/dynamsoft-label-recognizer/dist/dlr.js"></script>
<script src="/node_modules/dynamsoft-capture-vision-router/dist/cvr.js"></script>
<script src="/node_modules/dynamsoft-camera-enhancer/dist/dce.js"></script>
```

or

```typescript
import { EnumCapturedResultItemType, type DSImageData } from "dynamsoft-core";
import { LicenseManager } from "dynamsoft-license";
import { type TextLineResultItem } from "dynamsoft-label-recognizer";
import { CapturedResultReceiver, CaptureVisionRouter, type SimplifiedCaptureVisionSettings } from "dynamsoft-capture-vision-router";
import { CameraEnhancer, CameraView } from "dynamsoft-camera-enhancer";
```

*Note*:

* Certain legacy web application servers may lack support for the `application/wasm` mimetype for .wasm files. To address this, you have two options:
  1. Upgrade your web application server to one that supports the `application/wasm` mimetype.
  2. Manually define the mimetype on your server. You can refer to the following resources for guidance:
     1. [Apache](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Apache_Configuration_htaccess#media_types_and_character_encodings){:target="_blank"}
     2. [IIS](https://docs.microsoft.com/en-us/iis/configuration/system.webserver/staticcontent/mimemap){:target="_blank"}
     3. [Nginx](https://www.nginx.com/resources/wiki/start/topics/examples/full/#mime-types){:target="_blank"}

* To work properly, the SDK requires a few engine files, which are relatively large and may take quite a few seconds to download. We recommend that you set a longer cache time for these engine files, to maximize the performance of your web application.

  ```cmd
  Cache-Control: max-age=31536000
  ```

  Reference: [Cache-Control](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control){:target="_blank"}.

### Prepare the SDK

Before using the SDK, you need to configure a few things.

#### Specify the license

To enable the SDK's functionality, you must provide a valid license. Utilize the API function initLicense to set your license key.

```javascript
Dynamsoft.License.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");
```

As previously stated, the key "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9" serves as a test license valid for 24 hours, applicable to any newly authorized browser. To test the SDK further, you can request a 30-day free trial license via the [customer portal](https://www.dynamsoft.com/customer/license/trialLicense?ver=10.0.20&utm_source=guide&product=dlr&package=js).

> Upon registering a Dynamsoft account and obtaining the SDK package from the official website, Dynamsoft will automatically create a 30-day free trial license and embed the corresponding license key into all the provided SDK samples.

#### Specify the location of the "engine" files (optional)

This is usually only required with frameworks like Angular or React, etc. where the referenced JavaScript files such as `cvr.js`, `dlr.js` are compiled into another file.

The purpose is to tell the SDK where to find the engine files (\*.worker.js, \*.wasm.js and \*.wasm, etc.). The API is called `Dynamsoft.Core.CoreModule.engineResourcePaths`:

```javascript
//The following code uses the jsDelivr CDN, feel free to change it to your own location of these files
Dynamsoft.Core.CoreModule.engineResourcePaths.core = "https://cdn.jsdelivr.net/npm/dynamsoft-core@3.0.20/dist/";
Dynamsoft.Core.CoreModule.engineResourcePaths.license = "https://cdn.jsdelivr.net/npm/dynamsoft-license@3.0.20/dist/";
Dynamsoft.Core.CoreModule.engineResourcePaths.dlr = "https://cdn.jsdelivr.net/npm/dynamsoft-label-recognizer@3.0.20/dist/";
Dynamsoft.Core.CoreModule.engineResourcePaths.cvr = "https://cdn.jsdelivr.net/npm/dynamsoft-capture-vision-router@2.0.20/dist/";
Dynamsoft.Core.CoreModule.engineResourcePaths.dce = "https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@4.0.1/dist/";
```

#### [TODO] Add a visual cue about the loading of a .data file

The .data files are crucial for the recognition of certain types of text. For example, to read the MRZ zone on passports, the file MRZ.data must be loaded first. These .data files are loaded from the server on demand at runtime which could be time-consuming. To make the process user-friendly, it's recommended to show a visual cue about the loading process to the user with the help of the APIs `onResourcesLoadStarted` , `onResourcesLoadProgress` and `onResourcesLoaded` :

> These files are cached locally as soon as they are downloaded, so they load very quickly from the second time on.

```js
Dynamsoft.DLR.LabelRecognizer.onResourcesLoadStarted = (resourcePath) => {
    // In this event handler, you can display a visual cue to show that the model file is being downloaded.
    console.log("Loading " + resourcePath);
};
Dynamsoft.DLR.LabelRecognizer.onResourcesLoadProgress = (resourcePath, progress) => {
    // In this event handler, you can display the loading progress of the model file.
    console.log(resourcePath + "loading progress: " + progress.loaded + "/" + progress.total);
}
Dynamsoft.DLR.LabelRecognizer.onResourcesLoaded = (resourcePath) => {
    // In this event handler, you can close the visual cue if it was displayed.
    console.log("Finished loading " + resourcePath);
};
```

### Set up and start image processing

#### Preload the module

The image processing logic is encapsulated within .wasm library files, and these files may require some time for downloading. To enhance the speed, we advise utilizing the following method to preload the libraries.

```js
// Preload the .wasm files
await Dynamsoft.Core.CoreModule.loadWasm(["core", "license", "cvr", "dlr"]);
```

#### Create a CaptureVisionRouter object

To use the SDK, we first create a `CaptureVisionRouter` object.

```javascript
Dynamsoft.License.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");

let router = null;
try {
    router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
} catch (ex) {
    console.error(ex);
}
```

*Tip*:

When creating a `CaptureVisionRouter` object within a function which may be called more than once, it's best to use a "helper" variable to avoid double creation such as `hRouter` in the following code

```javascript
Dynamsoft.License.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");

let hRouter = null;
let router = null;

document.getElementById('btn-scan').addEventListener('click', async () => {
    try {
        router = await (hRouter = hRouter || Dynamsoft.CVR.CaptureVisionRouter.createInstance());
    } catch (ex) {
        console.error(ex);
    }
});
```

#### Connect an image source

The `CaptureVisionRouter` object, denoted as `router`, is responsible for handling images provided by an image source. In our scenario, we aim to detect barcodes directly from a live video stream. To facilitate this, we initialize a `CameraEnhancer` object, identified as `cameraEnhancer`, which is specifically designed to capture image frames from the video feed and subsequently forward them to `router`.

To enable video streaming on the webpage, we create a `CameraView` object referred to as `view`, which is then passed to `cameraEnhancer`, and its content is displayed on the webpage.

```html
<div id="cameraViewContainer" style="width: 100%; height: 100vh"></div>
```

```javascript
let view = await Dynamsoft.DCE.CameraView.createInstance();
let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(view);
document.querySelector("#cameraViewContainer").append(view.getUIElement());
router.setInput(cameraEnhancer);
```

#### [TODO]Register a result receiver

Once the image processing is complete, the results are sent to all the registered `CapturedResultReceiver` objects. Each `CapturedResultReceiver` object may encompass one or multiple callback functions associated with various result types. In our particular case, our focus is on identifying barcodes within the images, so it's sufficient to define the callback function `onDecodedBarcodesReceived`:

```javascript
const resultsContainer = document.querySelector("#results");
const resultReceiver = new Dynamsoft.CVR.CapturedResultReceiver();
resultReceiver.onDecodedBarcodesReceived = (result) => {
  if (result.barcodesResultItems.length > 0) {
    resultsContainer.innerHTML = "";
    for (let item of result.barcodesResultItems) {
      // In this example, the barcode result is shown on the page beneath the video
      resultsContainer.innerHTML += `${item.formatString}: ${item.text}<br><hr>`;
    }
  }
};
router.addResultReceiver(resultReceiver);
```

Check out [CapturedResultReceiver](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/captured-result-receiver.html) for more information.

#### [TODO]Start the process

With the setup now complete, we can proceed to process the images in two straightforward steps:

1. Initiate the image source to commence image acquisition. In our scenario, we invoke the `open()` method on `cameraEnhancer` to initiate video streaming and simultaneously initiate the collection of images. These collected images will be dispatched to `router` as per its request.
2. Define a preset template to commence image processing. In our case, we utilize the "ReadSingleBarcode" template, specifically tailored for processing images containing a single barcode.

```javascript
await cameraEnhancer.open();
await router.startCapturing("ReadSingleBarcode");
```

*Note*:

* `router` is engineered to consistently request images from the image source.
* Various preset templates are at your disposal for barcode reading:

| Template Name                  | Function                                               |
| ------------------------------ | ------------------------------------------------------ |
| **ReadBarcodes_Default**       | Try to find one barcode.                               |
| **ReadSingleBarcode**          | Try to find one barcode as fast as possible.           |
| **ReadBarcodes_SpeedFirst**    | Try to find barcodes as fast as possible.              |
| **ReadBarcodes_ReadRateFirst** | Try to find as many barcodes as possible.              |
| **ReadBarcodes_Balance**       | Try to find as many barcodes and as fast as possible.  |
| **ReadDenseBarcodes**          | Try to read barcodes that contain lots of information. |
| **ReadDistantBarcodes**        | Try to find barcodes from a distance.                  |

### [TODO]Customize the process

#### Adjust the preset template settings

* Change barcode settings

The preset templates can be updated to meet different requirements. For example, the following code limits the barcode format to QR code.

```javascript
let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
settings.barcodeSettings.barcodeFormatIds =
  Dynamsoft.DLR.EnumBarcodeFormat.BF_QR_CODE;
await router.updateSettings("ReadSingleBarcode", settings);
await router.startCapturing("ReadSingleBarcode");
```

For a list of adjustable barcode settings, check out [SimplifiedBarcodeReaderSettings](https://www.dynamsoft.com/barcode-reader/docs/web/programming/javascript/api-reference/interfaces/simplified-barcode-reader-settings.html){:target="_blank"}.

* Retrieve the original image

Additionally, we have the option to modify the template to retrieve the original image containing the barcode.

```javascript
let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
settings.capturedResultItemTypes += Dynamsoft.Core.EnumCapturedResultItemType.CRIT_ORIGINAL_IMAGE;
await router.updateSettings("ReadSingleBarcode", settings);
await router.startCapturing("ReadSingleBarcode");
```

Please be aware that it is necessary to update the `CapturedResultReceiver` object to obtain the original image. For instance:

```javascript
resultReceiver.onCapturedResultReceived = (result) => {
  let barcodes = result.items.filter(
    (item) =>
      item.type === Dynamsoft.Core.EnumCapturedResultItemType.CRIT_BARCODE
  );
  if (barcodes.length > 0) {
    let image = result.items.filter(
      (item) =>
        item.type ===
        Dynamsoft.Core.EnumCapturedResultItemType.CRIT_ORIGINAL_IMAGE
    )[0].imageData;
    // The image that we found the barcode(s) on.
  }
};
```

* Change reading frequency

The SDK is initially configured to process images sequentially without any breaks. Although this setup maximizes performance, it can lead to elevated power consumption, potentially causing the device to overheat. In many cases, it's possible to reduce the reading speed while still satisfying business requirements. The following code snippet illustrates how to adjust the SDK to process an image every 500 milliseconds:

> Please bear in mind that in the following code, if an image's processing time is shorter than 500 milliseconds, the SDK will wait for the full 500 milliseconds before proceeding to process the next image. Conversely, if an image's processing time exceeds 500 milliseconds, the subsequent image will be processed immediately upon completion.

```javascript
let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
settings.minImageCaptureInterval = 500;
await router.updateSettings("ReadSingleBarcode", settings);
await router.startCapturing("ReadSingleBarcode");
```

* Specify a scan region

You can use the parameter `roi` (region of interest) together with the parameter `roiMeasuredInPercentage` to configure the SDK to only read a specific region on the image frames. For example, the following code limits the reading in the center 25% of the image frames:

```javascript
let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
settings.roiMeasuredInPercentage = true;
settings.roi.points = [
  { x: 25, y: 25 },
  { x: 75, y: 25 },
  { x: 75, y: 75 },
  { x: 25, y: 75 },
];
await router.updateSettings("ReadSingleBarcode", settings);
await router.startCapturing("ReadSingleBarcode");
```

While the code above accomplishes the task, a more effective approach is to restrict the scan region directly at the image source, as demonstrated in the following code snippet.

> * With the region configured at the image source, the images are cropped right before they are gathered for processing, eliminating the necessity to modify the processing settings further.
> * `cameraEnhancer` elevates interactivity by overlaying a mask on the video, providing a clear delineation of the scanning region.

```javascript
cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(
  view
);
cameraEnhancer.setScanRegion({
  x: 25,
  y: 25,
  width: 50,
  height: 50,
  isMeasuredInPercentage: true,
});
```

* Specify the maximum time allowed for processing each image

You can set the maximum time allowed for processing a single image with the property `timeout`.

> Please be aware that the SDK will cease processing an image if its processing time exceeds the duration specified by the `timeout` parameter. It should not be confused with the previously discussed parameter, `minImageCaptureInterval`.

```javascript
let settings = await router.getSimplifiedSettings("ReadSingleBarcode");
settings.timeout = 500;
await router.updateSettings("ReadSingleBarcode", settings);
await router.startCapturing("ReadSingleBarcode");
```

#### Edit the preset templates directly

The preset templates have a lot more settings that can be customized to best suit your use case. If you [download the SDK from Dynamsoft website](https://www.dynamsoft.com/barcode-reader/downloads/1000003-confirmation/), you can find the templates under

* "/dynamsoft-barcode-reader-js-10.0.20/dynamsoft/resources/barcode-reader/templates/"

Upon completing the template editing, you can invoke the `initSettings` method and provide it with the template path as an argument.

```javascript
await router.initSettings("PATH-TO-THE-FILE"); //e.g. "https://your-website/ReadSingleBarcode.json")
await router.startCapturing("ReadSingleBarcode"); // Make sure the name matches one of the CaptureVisionTemplates in the
```

#### Filter the results (Important)

While processing video frames, it's common for the same barcode to be detected multiple times. To enhance the user experience, we have two options currently at our disposal:

##### Option 1: Verify results across multiple frames

```js
let filter = new Dynamsoft.Utility.MultiFrameResultCrossFilter();
filter.enableResultCrossVerification(
  Dynamsoft.Core.EnumCapturedResultItemType.CRIT_BARCODE,
  true
);
await router.addResultFilter(filter);
```

##### Option 2: Eliminate redundant results detected within a short time frame

```js
let filter = new Dynamsoft.Utility.MultiFrameResultCrossFilter();
filter.enableResultDeduplication(
  Dynamsoft.Core.EnumCapturedResultItemType.CRIT_BARCODE,
  true
);
await router.addResultFilter(filter);
```

You can also enable both options at the same time:

```js
let filter = new Dynamsoft.Utility.MultiFrameResultCrossFilter();
filter.enableResultCrossVerification(
  Dynamsoft.Core.EnumCapturedResultItemType.CRIT_BARCODE,
  true
);
filter.enableResultDeduplication(
  Dynamsoft.Core.EnumCapturedResultItemType.CRIT_BARCODE,
  true
);
await router.addResultFilter(filter);
```

#### Add feedback

When a barcode is detected within the video stream, its position is immediately displayed within the video. Furthermore, utilizing the "Dynamsoft Camera Enhancer" SDK, we can introduce feedback mechanisms, such as emitting a "beep" sound or triggering a "vibration".

The following code snippet adds a "beep" sound for when a barcode is found:

```js
const resultReceiver = new Dynamsoft.CVR.CapturedResultReceiver();
resultReceiver.onDecodedBarcodesReceived = (result) => {
  if (result.barcodesResultItems.length > 0) {
    Dynamsoft.DCE.Feedback.beep();
  }
};
router.addResultReceiver(resultReceiver);
```

### Customize the UI

The UI is part of the auxiliary SDK "Dynamsoft Camera Enhancer", read more on how to [customize the UI](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/user-guide/index.html#customize-the-ui).

## API Documentation

You can check out the detailed documentation about the APIs of the SDK at
[https://www.dynamsoft.com/label-recognition/docs/web/programming/javascript/api-reference/](https://www.dynamsoft.com/label-recognition/docs/web/programming/javascript/api-reference/?ver=3.0.20&utm_source=guide&product=dlr&package=js).

## System Requirements

DLR requires the following features to work:

- Secure context (HTTPS deployment)

  When deploying your application / website for production, make sure to serve it via a secure HTTPS connection. This is required for two reasons
  
  - Access to the camera video stream is only granted in a security context. Most browsers impose this restriction.
  > Some browsers like Chrome may grant the access for `http://127.0.0.1` and `http://localhost` or even for pages opened directly from the local disk (`file:///...`). This can be helpful for temporary development and test.
  
  - Dynamsoft License requires a secure context to work.

- `WebAssembly`, `Blob`, `URL`/`createObjectURL`, `Web Workers`

  The above four features are required for the SDK to work.

- `MediaDevices`/`getUserMedia`

  This API is required for in-browser video streaming.

- `getSettings`

  This API inspects the video input which is a `MediaStreamTrack` object about its constrainable properties.

The following table is a list of supported browsers based on the above requirements:

  | Browser Name |     Version      |
  | :----------: | :--------------: |
  |    Chrome    | v78+<sup>1</sup> |
  |   Firefox    | v62+<sup>1</sup> |
  |     Edge     |       v79+       |
  |    Safari    |       v14+       |

  <sup>1</sup> devices running iOS needs to be on iOS 14.3+ for camera video streaming to work in Chrome, Firefox or other Apps using webviews.

Apart from the browsers, the operating systems may impose some limitations of their own that could restrict the use of the SDK. Browser compatibility ultimately depends on whether the browser on that particular operating system supports the features listed above.

## Release Notes

Learn about what are included in each release at [https://www.dynamsoft.com/label-recognition/docs/web/programming/javascript/release-notes/index.html](https://www.dynamsoft.com/label-recognition/docs/web/programming/javascript/release-notes/index.html?ver=latest).

## Next Steps

Now that you have got the SDK integrated, you can choose to move forward in the following directions

1. Check out the [official samples](https://github.com/Dynamsoft/label-recognizer-javascript-samples).
2. Check out the official demos: [MRZ Scanner](https://demo.dynamsoft.com/label-recognizer-js/mrz-scanner.html), [VIN Scanner](https://demo.dynamsoft.com/label-recognizer-js/vin.html) and the [source code for the demo](https://github.com/Dynamsoft/label-recognizer-javascript-demo).
3. Learn about the available [APIs](https://www.dynamsoft.com/label-recognition/docs/web/programming/javascript/api-reference/?ver=latest).
