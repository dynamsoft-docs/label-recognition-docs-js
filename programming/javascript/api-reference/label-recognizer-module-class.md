---
layout: default-layout
title: LabelRecognizerModule Class - Dynamsoft Label Recognizer JavaScript Edition API
description: This page introduces APIs related to the LabelRecognizerModule Class of Dynamsoft Label Recognizer JavaScript Edition.
keywords: capture vision, Label Recognizer Module, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---

# LabelRecognizerModule Class

The `LabelRecognizerModule` Class is defined in the namespace `Dynamsoft.DLR`.

| API Name                                                         | Description                                                                           |
| ---------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `static` [getVersion()](#getversion)                             | Returns the version of the `LabelRecognizer` module.                                  |
| `static` [loadRecognitionData()](#loadrecognitiondata)           | Loads a specific data file containing recognition information.                        |
| `static` [onDataLoadProgressChanged](#ondataloadprogresschanged) | An event that repeatedly fires during the loading of a recognition data file (.data). |

## getVersion

Returns the version of the `LabelRecognizer` module.

```typescript
static getVersion(): string;
```

**Code snippet**

```javascript
const version = Dynamsoft.DLR.LabelRecognizerModule.getVersion();
console.log(version);
```

## loadRecognitionData

Loads a specific data file containing recognition information to aid in identifying text composed of predetermined characters. This file typically comprises a Convolutional Neural Networks (CNN) model.

```typescript
static loadRecognitionData(dataName: string, dataPath?: string): Promise<void>;
```

**Parameters**

* `dataName`: specifies the name of the recognition data. Available values are "MRZ", "VIN", "Letter", "Number", "NumberLetter", "UpperCase", "NumberUppercase".
* `dataPath`: specifies the path to find the data file. If not specified, the default path points to the package "dynamsoft-label-recognizer-data" which has the same root path as the package "dynamsoft-label-recognizer".

**Code snippet**

```javascript
await Dynamsoft.DLR.LabelRecognizerModule.loadRecognitionData("NumberLetter");
```

## onDataLoadProgressChanged

An event that repeatedly fires during the loading of a recognition data file (.data).

```typescript
static onDataLoadProgressChanged: (filePath: string, tag: "starting" | "in progress" | "completed", progress: { loaded: number, total: number }) => {};
```

**Properties**

* `filePath`: Returns the path of the recognition data file.
* `tag`: Indicates the ongoing status of the file download. Available values are "starting", "in progress", "completed".
* `progress`: Shows the numerical progress of the download.
            
**Code snippet**

```js
Dynamsoft.DLR.LabelRecognizerModule.onDataLoadProgressChanged = (filePath, tag, progress) => {
    console.log("The loading of the file " + filePath + " is " + tag +" ( " + progress.loaded + "/" + progress.total+ ").");
}
await Dynamsoft.DLR.LabelRecognizerModule.loadRecognitionData("NumberLetter");
```