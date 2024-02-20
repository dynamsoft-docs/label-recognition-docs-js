---
layout: default-layout
title: Interface RecognizedTextLineElement - Dynamsoft Label Recognizer JS Edition API Reference
description: The class RecognizedTextLineElement of Dynamsoft Label Recognizer JS edition represents a line of recognized text in an image.
keywords: Recognized text line element
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: RecognizedTextLineElement
---

# RecognizedTextLineElement

The `RecognizedTextLineElement` class represents a line of recognized text in an image.

```typescript
interface RecognizedTextLineElement extends Core.RegionObjectElement {
    text: string;
    confidence: number;
    characterResults: Array<CharacterResult>;
    rowNumber: number;
}
```

| Method                                | Description                                               |
| ------------------------------------- | --------------------------------------------------------- |
| [text](#text)                         | Returns the recognized text.                              |
| [confidence](#confidence)             | Returns the confidence level of the recognized text.      |
| [characterResults](#characterresults) | Returns all the characters contained by the textline.     |
| [rowNumber](#rownumber)               | Returns the row number of the text line within the image. |

## text

Returns the recognized text.

```typescript
text: string;
```

## confidence

Returns the confidence level of the recognized text.

```typescript
confidence: number;
```

## characterResults

Returns all the characters contained by the textline in an array of [CharacterResult](character-result.md).

```typescript
characterResults: Array<CharacterResult>;
```

## rowNumber

Returns the row number of the text line within the image.

```typescript
rowNumber: number;
```
