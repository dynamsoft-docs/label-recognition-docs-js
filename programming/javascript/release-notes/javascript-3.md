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

## 3.0.20 (01/xx/2024)

### ADDED

* Added option `captureAndRecognizeInParallel` to the interface `ScanSettings` to control whether to speed up the recognition by capturing the next frame in advance.

### CHANGED

* The method `setImageSource()` now takes an additional parameter `options` which helps to pass the information needed by the `LabelRecognizer` object, such as the definition (`Dynamsoft.DCE.DrawingItem`) for creating the shapes that highlight barcodes.
* The method `pauseScanning()` now accepts an optional parameter `options`, which can control the behavior of the pause, such as whether to keep results highlighted (`keepResultsHighlighted`).
* This version uses [Dynamsoft Camera Enhancer version 3.0.1](https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/release-note/release-notes-3.x.html?ver=latest#301-08042022).

### FIXED

* Fix a bug with VIN result verification, which may lead to errors when the VIN code start and end with the character "1".
