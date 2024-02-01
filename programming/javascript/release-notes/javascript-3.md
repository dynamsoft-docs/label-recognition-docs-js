---
layout: default-layout
title: JavaScript 3.x Release Notes  - Dynamsoft Label Recognizer
description: This is the Release Notes page for Dynamsoft Label Recognizer JavaScript SDK.
keywords:  label recognizer, release notes, javascript
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: v3.x Release Notes
---

# Release Notes - JavaScript 3.x

## 3.0.30 (02/01/2024)

### Changelog

In this version, the SDK has been refactored under the `DynamsoftCaptureVision` (DCV) architecture. To learn more about the architecture, please see [Architecture of Dynamsoft Capture Vision](https://www.dynamsoft.com/capture-vision/docs/core/architecture/){:target="_blank"}. The following highlights the major changes: 

* The class `LabelRecognizer` is removed and its functionalities are now incorporated into the newly added Class `CaptureVisionRouter`.

* License-related functions are handled by class [Dynamsoft.License.LicenseManager]({{ site.dcv_js_api }}license/license-manager.html#initLicense).

* Camera-related functions are handled by [DynamsoftCameraEnhancer(DCE)](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/){:target="_blank"}. Please note that the following features are grouped together as enhanced features that require a license:
  * Enhanced-focus.
  * Auto-zoom.
  * Tap-to-focus.

* This version of `LabelRecognizer` only accepts `DynamsoftCameraEnhancer(DCE)` version 4.0.1 and above, which has been refactored to be compliant with the [ImageSourceAdapter (ISA) interface](https://www.dynamsoft.com/capture-vision/docs/core/architecture/input.html#image-source-adapter){:target="_blank"}, as a valid image source.

* Recognized text results are returned via the [CapturedResultReceiver (CRR) interface](https://www.dynamsoft.com/capture-vision/docs/core/architecture/output.html#captured-result-receiver){:target="_blank"}.