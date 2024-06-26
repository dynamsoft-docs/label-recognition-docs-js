---
layout: default-layout
title: Interface CharacterResult - Dynamsoft Label Recognizer JS Edition API Reference
description: The interface CharacterResult of Dynamsoft Label Recognizer JS edition represents the result of a character recognition process.
keywords: Character result
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: CharacterResult
---

# CharacterResult

The `CharacterResult` interface represents the result of a character recognition process. It contains the characters recognized (high, medium, and low confidence), their respective confidences, and the location of the character in a quadrilateral shape.

```typescript
interface CharacterResult {
    characterH: string;
    characterM: string;
    characterL: string;
    characterHConfidence: number;
    characterMConfidence: number;
    characterLConfidence: number;
    location: Quadrilateral;
}
```

<!-- | Method                                        | Description                                                    |
| --------------------------------------------- | -------------------------------------------------------------- |
| [characterH](#characterh)                     | The character with high confidence.                     |
| [characterM](#characterm)                     | The character with medium confidence.                   |
| [characterL](#characterl)                     | The character with low confidence.                      |
| [location](#location)                         | The location of the character in a quadrilateral shape. |
| [characterHConfidence](#characterhconfidence) | The confidence of the character with high confidence.   |
| [characterMConfidence](#charactermconfidence) | The confidence of the character with medium confidence. |
| [characterLConfidence](#characterlconfidence) | The confidence of the character with low confidence.    | -->

## characterH

The character with high confidence.

```typescript
characterH: string
```

## characterM

The character with medium confidence.

```typescript
characterM: string
```

## characterL

The character with low confidence.

```typescript
characterL: string
```

## location

The location of the character in a quadrilateral shape.

```typescript
location: Quadrilateral;
```

**See Also**

* [Quadrilateral]({{ site.dcv_js_api }}core/basic-structures/quadrilateral.html)

## characterHConfidence

The confidence of the character with high confidence.

```typescript
characterHConfidence: number
```

## characterMConfidence

The confidence of the character with medium confidence.

```typescript
characterMConfidence: number
```

## characterLConfidence

The confidence of the character with low confidence.

```typescript
characterLConfidence: number
```
