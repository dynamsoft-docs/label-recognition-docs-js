---
layout: default-layout
title: Interface TextLineResultItem - Dynamsoft Label Recognizer JS Edition API Reference
description: The class TextLineResultItem of Dynamsoft Label Recognizer represents a text line result item recognized by a document layout analysis engine.
keywords: Text line result item
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: TextLineResultItem
---

# TextLineResultItem

The `TextLineResultItem` class represents a text line result item recognized by the library.

```typescript
interface TextLineResultItem extends Core.CapturedResultItem {
    text: string;
    location: Core.Quadrilateral;
    confidence: number;
    characterResults: Array<CharacterResult>
}
```

| Method                                | Description                                                           |
| ------------------------------------- | --------------------------------------------------------------------- |
| [text](#text)                         | Returns the text content of the text line.                            |
| [location](#location)                 | Returns the location of the text line in the form of a quadrilateral. |
| [confidence](#confidence)             | Returns the confidence of the text line recognition result.           |
| [characterResults](#characterresults) | Returns all the characters in the text line.                          |

## Text

Returns the text content of the text line.

```typescript
text: string;
```

## Location

Returns the location of the text line in the form of a quadrilateral.

```typescript
location: Quadrilateral;
```

**See Also**

* [Quadrilateral]({{ site.dcv_js_api }}core/basic-structures/quadrilateral.html)

## confidence

It is used to get the confidence of the text line recognition result.

```typescript
confidence: number;
```

## characterResults

Returns all the characters in the text line.

```typescript
characterResults: Array<CharacterResult>;
```

**See Also**

* [CharacterResult](./character-result.md)
