---
layout: default-layout
title: Interface RawTextLine - Dynamsoft Label Recognizer JS Edition API Reference
description: The interface RawTextLine of Dynamsoft Label Recognizer JS edition represents a raw text line.
keywords: raw text line
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: RawTextLine
---

# RawTextLine

The `RawTextLine` interface represents a raw text line.

```typescript
interface RawTextLine extends Core.RegionObjectElement{
    text: string;
    confidence: number;
    characterResults: Array<CharacterResult>;
    rowNumber: number;
    specificationName: string;
    location: Core.Quadrilateral;
    status: DLR.EnumRawTextLineStatus;
};
```

## text

The raw text.

```typescript
text: string;
```

## confidence

The confidence level of the raw text.

```typescript
confidence: number;
```

## characterResults

All the characters contained by the text line in an array of [CharacterResult](character-result.md).

```typescript
characterResults: Array<CharacterResult>;
```

## rowNumber

The row number of the text line within the image.

```typescript
rowNumber: number;
```

## specificationName

The name of the text line specification that generated this element.

```typescript
specificationName: string;
```

## location

The location of the text line.

```typescript
location: Core.Quadrilateral;
```

**See Also**

* [Quadrilateral]({{ site.dcv_js_api }}core/basic-structures/quadrilateral.html)

## status

The status of a raw text line.

```typescript
status: DLR.EnumRawTextLineStatus;
```

**See Also**

* [EnumRawTextLineStatus]({{ site.enums }}label-recognizer/raw-text-line-status.html)