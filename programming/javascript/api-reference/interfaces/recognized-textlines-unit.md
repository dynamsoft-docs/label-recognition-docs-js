---
layout: default-layout
title: Interface RecognizedTextLinesUnit - Dynamsoft Label Recognizer JS Edition API Reference
description: The class RecognizedTextLinesUnit of Dynamsoft Label Recognizer JS edition represents an intermediate result unit containing recognized text lines.
keywords: Recognized text lines unit
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: RecognizedTextLinesUnit
---

# RecognizedTextLinesUnit

The `RecognizedTextLinesUnit` class represents an intermediate result unit containing recognized text lines.

```typescript
interface RecognizedTextLinesUnit extends Core.IntermediateResultUnit {
    recognizedTextLines: Array<RecognizedTextLineElement>;
}
```

<!-- | Method                                      | Description                                        |
| ------------------------------------------- | -------------------------------------------------- |
| [recognizedTextLines](#recognizedtextlines) | Returns all the RecognizedTextLineElement objects. | -->

## recognizedTextLines

Returns all the RecognizedTextLineElement objects.

```typescript
recognizedTextLines: Array<RecognizedTextLineElement>;
```

**See Also**

* [RecognizedTextLineElement]({{ site.dlr_js_api }}interfaces/recognized-textline-element.html)
