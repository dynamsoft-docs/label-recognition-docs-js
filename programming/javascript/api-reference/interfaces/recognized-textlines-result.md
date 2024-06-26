---
layout: default-layout
title: Interface RecognizedTextLinesResult - Dynamsoft Label Recognizer JS Edition API Reference
description: The interface RecognizedTextLinesResult of Dynamsoft Label Recognizer JS edition represents the result of a text recognition process.
keywords: Recognized text lines result
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: RecognizedTextLinesResult
---

# RecognizedTextLinesResult

The `RecognizedTextLinesResult` interface represents the result of a text recognition process. It provides access to information about the recognized text lines, the original image, and any errors that occurred during the recognition process.

```typescript
interface RecognizedTextLinesResult {
    originalImageHashId: string;
    originalImageTag: Core.ImageTag;
    textLinesResultItems: Array<TextLineResultItem>;
    errorCode: number;
    errorString: string;
}
```

<!-- | Method                                        | Description                                        |
| --------------------------------------------- | -------------------------------------------------- |
| [originalImageHashId](#originalimagehashid)   | Returns the hash ID of the original image.         |
| [originalImageTag](#originalimagetag)         | Returns the tag of the original image.             |
| [textLinesResultItems](#textlinesresultitems) | Returns all the recognized text line result items. |
| [errorCode](#errorcode)                       | Returns the error code, if an error occurred.      |
| [errorMessage](#errormessage)                 | Returns the error message, if an error occurred.   | -->

## originalImageHashId

The hash ID of the original image.

```typescript
originalImageHashId: string;
```

## originalImageTag

The tag of the original image.

```typescript
originalImageTag: ImageTag;
```

**See Also**

* [ImageTag]({{ site.dcv_js_api }}core/basic-structures/image-tag.html)

## textLinesResultItems

All the recognized text line result items. 

```typescript
textLinesResultItems: Array<TextLineResultItem>;
```

**See Also**

* [TextLineResultItem](./textline-result-item.md)

## errorCode

The error code, if an error occurred.

```typescript
errorCode: number;
```

## errorMessage

The error message, if an error occurred.

```typescript
errorMessage: string;
```