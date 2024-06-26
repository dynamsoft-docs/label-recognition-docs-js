---
layout: default-layout
title: Interface SimplifiedLabelRecognizerSettings - Dynamsoft Label Recognizer JS Edition API Reference
description: This page shows the JS edition of the interface SimplifiedLabelRecognizerSettings in Dynamsoft DLR Module.
keywords: simplified setting, JS
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: SimplifiedLabelRecognizerSettings
---

# SimplifiedLabelRecognizerSettings

The `SimplifiedLabelRecognizerSettings` interface defines simplified settings for label recognizing.

```typescript
interface SimplifiedLabelRecognizerSettings {
    grayscaleTransformationModes: Array<Core.EnumGrayscaleTransformationMode>;
    grayscaleEnhancementModes: Array<Core.EnumGrayscaleEnhancementMode>;
    characterModelName: string;
    lineStringRegExPattern: string;
    scaleDownThreshold: number
}
```

<!-- | Property                                                      | Description                                                                           |
| ------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| [grayscaleTransformationModes](#grayscaletransformationmodes) | Sets the grayscale transformation modes.                                              |
| [grayscaleEnhancementModes](#grayscaleenhancementmodes)       | Sets the grayscale enhancement modes.                                                 |
| [characterModelName](#charactermodelname)                     | Specifies a character model by its name.                                              |
| [lineStringRegExPattern](#linestringregexpattern)             | Sets the RegEx pattern of the text line string to filter out the unqualified results. |
| [scaleDownThreshold](#scaledownthreshold)                     | Sets the threshold value that determines when the original image is scaled down.      | -->

## grayscaleTransformationModes

Sets the grayscale transformation modes.

```typescript
grayscaleTransformationModes: Array<EnumGrayscaleTransformationMode>
```

**Remarks**

View the parameter reference page of [EnumGrayscaleTransformationMode]({{ site.enums }}core/grayscale-transformation-mode.html){:target="_blank"} for more detail about how to set grayscale transformation modes.

## grayscaleEnhancementModes

Sets the grayscale enhancement modes.

```typescript
grayscaleEnhancementModes: Array<EnumGrayscaleEnhancementMode>;
```

**Remarks**

View the reference page of [EnumGrayscaleEnhancementMode]({{ site.enums }}core/grayscale-enhancement-mode.html){:target="_blank"} for more detail about how to set grayscale enhancement modes.

## characterModelName

Specifies a character model by its name.

```typescript
characterModelName: string;
```

## lineStringRegExPattern

Sets the RegEx pattern of the text line string to filter out the unqualified results.

```typescript
lineStringRegExPattern: string;
```

## scaleDownThreshold

Sets the threshold value that determines when the original image is scaled down.

```typescript
int scaleDownThreshold;
```
