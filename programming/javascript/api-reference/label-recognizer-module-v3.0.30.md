---
layout: default-layout
title: LabelRecognizer Module - Dynamsoft Label Recognizer JavaScript Edition API
description: This page introduces the LabelRecognizer module in Dynamsoft Label Recognizer JavaScript Edition.
keywords: label recognizer, module, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---
<!-- 3.0.20 -- Updated on 12/07/2023-->

# LabelRecognizer Module

The LabelRecognizer module is defined in the namespace `Dynamsoft.DLR`. It includes a class named "LabelRecognizerModule" along with various interfaces.

## LabelRecognizerModule Class

This class defines common functionality in the `LabelRecognizer` module.

| API Name                                                                                           | Description                                                                           |
| -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `static` [getVersion()](./label-recognizer-module-class.md#getversion)                             | Returns the version of the `LabelRecognizer` module.                                  |
| `static` [loadRecognitionData()](./label-recognizer-module-class.md#loadrecognitiondata)           | Loads a specific data file containing recognition information.                        |
| `static` [onDataLoadProgressChanged](./label-recognizer-module-class.md#ondataloadprogresschanged) | An event that repeatedly fires during the loading of a recognition data file (.data). |

## Interfaces

* [SimplifiedLabelRecognizerSettings](./interfaces/simplified-label-recognizer-settings.md)
* [CharacterResult](./interfaces/character-result.md)
* [LocalizedTextLineElement](./interfaces/localized-textline-element.md)
* [RecognizedTextLineElement](./interfaces/recognized-textline-element.md)
* [LocalizedTextLinesUnit](./interfaces/localized-textlines-unit.md)
* [RecognizedTextLinesUnit](./interfaces/recognized-textlines-unit.md)
* [TextLineResultItem](./interfaces/textline-result-item.md)
* [RecognizedTextLinesResult](./interfaces/recognized-textlines-result.md)
