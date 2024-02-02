---
layout: default-layout
title: Main Page - Dynamsoft Label Recognizer JavaScript API
description: This is the main page of Dynamsoft Label Recognizer JavaScript SDK API Reference.
keywords: LabelRecognizer, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: API Reference
permalink: /programming/javascript/api-reference/index-v2.2.31.html
---

# JavaScript API Reference

The primary class of the library is `LabelRecognizer` . The following code snippets shows the basic usage.

* Recognize a still image

```js
let labelRecognizer = await Dynamsoft.DLR.LabelRecognizer.createInstance();
let results = await labelRecognizer.recognize(imagePath);
for (let result of results) {
    for (let lineResult of result.lineResults) {
        console.log(lineResult.text);
    }
}
```

* Recognize continuous video frames

```js
let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
await cameraEnhancer.setUIElement(document.getElementById('div-ui-container'));
let recognizer = await Dynamsoft.DLR.LabelRecognizer.createInstance();
recognizer.setImageSource(cameraEnhancer);
await recognizer.updateRuntimeSettingsFromString("video-MRZ");
recognizer.onImageRead = results => {
    for (let result of results) {
        for (let lineResult of result.lineResults) {
            console.log(lineResult.text);
        }
    }
};
recognizer.startScanning(true);
```

The APIs for this class include

## Initialization Control

The following static methods and properties help to set up the runtime environment for the library.

| API Name | Description |
|---|---|
| [engineResourcePath](initialize.html#engineresourcepath) | Specifies the path from where the recognition engine and models, etc. can be loaded. |
| [loadWasm()](initialize.html#loadwasm) | Loads the recognition engine and models. |
| [isWasmLoaded()](initialize.html#iswasmloaded) | Returns whether the recognition engine and models have been loaded. |
| [getVersion()](initialize.html#getversion) | Returns the version of the library. |
| [detectEnvironment()](initialize.html#detectenvironment) | Assess the running environment regarding the features the library requires to run. |

### Create and Destroy Instances

| API Name | Description |
|---|---|
| [createInstance()](initialize.html#createinstance) | Creates a `LabelRecognizer` instance. |
| [destroyContext()](initialize.html#destroycontext) | Destroies the LabelRecognizer instance. |
| [isContextDestroyed()](initialize.html#iscontextdestroyed) | Returns whether the instance has been destroyed. |

### License Control

| API Name | Description |
|---|---|
| [license](initialize.html#license) | Use an alphanumeric string to specify the license. |

## Recognition

### Recognize Labels from Still Images

| API Name | Description |
|---|---|
| [recognize()](recognize.html#recognize) | Decodes labels from an image. |
| [recognizeBase64String()](recognize.html#recognizebase64string) | Decodes labels from a base64-encoded image (with or without MIME). |
| [recognizeUrl()](recognize.html#recognizeurl) | Decodes labels from an image specified by its URL. |
| [recognizeBuffer()](recognize.html#recognizebuffer) | Decodes labels from raw image data. |

### Recognize Labels from Video Frames

| API Name | Description |
|---|---|
| [setImageSource](recognize.html#setimagesource) | Sets an image source for continous scanning. |
| [onUniqueRead](recognize.html#onuniqueread) | This event is triggered when a new, unduplicated label is found when scanning via video. |
| [onImageRead](recognize.html#onimageread) | This event is triggered after the library finishes scanning an image. |
| [onMRZRead](recognize.html#onmrzread) | This event is triggered after the library finishes scanning a frame with the built-in templates `passportMRZ` , `video-passportMRZ` , `visaMRZ` , `video-visaMRZ` , `MRZ` or `video-MRZ` . |
| [onVINRead](recognize.html#onvinread) | This event is triggered after the library finishes scanning an image based on one of the built-in templates `VIN`, `video-VIN`, `VIN_NA` or `video-VIN_NA`. |
| [startScanning()](recognize.html#startscanning) | Starts continuous scanning of incoming images. |
| [stopScanning()](recognize.html#stopscanning) | Stops continuous scanning. |
| [pauseScanning()](recognize.html#pausescanning) | Pause continuous scanning but keep the video stream. |
| [resumeScanning()](recognize.html#resumescanning) | Resumes continuous scanning. |

## Settings

### Scan Settings

| API Name | Description |
|---|---|
| [getScanSettings()](settings.html#getscansettings) | Returns the current scan settings. |
| [updateScanSettings()](settings.html#updatescansettings) | Changes scan settings with the object passed in. |

### Runtime Settings

<!--
| [getRuntimeSettings()](settings.html#getruntimesettings) | Returns the current runtime settings. |
| [updateRuntimeSettings()](settings.html#updateruntimesettings) | Updates runtime settings with a given struct or a preset template. |
| [resetRuntimeSettings()](settings.html#resetruntimesettings) | Resets all parameters to default values. |
| [getModeArgument()](settings.html#getmodeargument) | Returns the argument value for the specified mode parameter. |
| [setModeArgument()](settings.html#setmodeargument) | Sets the argument value for the specified mode parameter. |
-->

| API Name | Description |
|---|---|
| [updateRuntimeSettingsFromString()](settings.html#updateruntimesettingsfromstring) | Updates runtime settings with a template represented by a JSON string. |
| [outputRuntimeSettingsToString()](settings.html#outputruntimesettingstostring) | Output the current runtime settings to a JSON string. |
[updateReferenceRegionFromBarcodeResults()](settings.html#updatereferenceregionfrombarcoderesults) | Updates reference region which is defined with source type `DLR_LST_BARCODE`. |

<!--
| [appendCharacterModelBuffer()](settings.html#appendcharactermodelbuffer) | Appends a CharacterModel to assist the recognition. |
| [eraseCharacterModelByName()](settings.html#erasecharactermodelbyname) | Erases a CharacterModel by its name. |
| [eraseAllCharacterModels()](settings.html#eraseallcharactermodels) | Erases all CharacterModels. |
| 
-->

## Auxiliary

| API Name | Description |
|---|---|
| [ifSaveOriginalImageInACanvas](auxiliary.html#ifsaveoriginalimageinacanvas) | Whether to save the original image into a &lt; canvas&gt; element. |
| [getOriginalImageInACanvas()](auxiliary.html#getoriginalimageinacanvas) | Returns an `HTMLCanvasElement` that holds the original image. |
| [onResourcesLoadStarted](auxiliary.html#onresourcesloadstarted) | This event is triggered when the resource file (.data) for a particular template starts to load. |
| [onResourcesLoadProgress](auxiliary.html#onresourcesloadprogress) | This event is triggered multiple times when the resource file (.data) for a particular template is being loaded. |
| [onResourcesLoaded](auxiliary.html#onresourcesloaded) | This event is triggered when the resource file (.data) for a particular template finishes loading. |

## Interfaces and Enumerations

In order to make the code more predictable and readable, the library defines a series of supporting interfaces and enumerations.

### Interfaces

* [DLRLineResult](interface/dlr-line-result.html)
* [Point](interface/point.html)
* [Quadrilateral](interface/quadrilateral.html)
* [DLRReferenceRegion](interface/dlr-reference-region.html)
* [DLRResult](interface/dlr-result.html)
* [DLRRuntimeSettings](interface/dlr-runtime-settings.html)
* [ImageSource](interface/imagesource.html)
* [DSImage](interface/dsimage.html)

### Enumerations

* [RegionPredetectionMode]({{ site.enumerations }}region-predetection-mode.html)
* [ColourConversionMode]({{ site.enumerations }}colour-conversion-mode.html)
* [GrayscaleTransformationMode]({{ site.enumerations }}grayscale-transformation-mode.html)
* [GrayscaleEnhancementMode]({{ site.enumerations }}grayscale-enhancement-mode.html)
* [BinarizationMode]({{ site.enumerations }}binarization-mode.html)
* [TextureDetectionMode]({{ site.enumerations }}texture-detection-mode.html)
* [ImagePixelFormat]({{ site.enumerations }}image-pixel-format.html)
* [LocalizationSourceType]({{ site.enumerations }}localization-source-type.html)
* [ErrorCode]({{ site.enumerations }}error-code.html)
