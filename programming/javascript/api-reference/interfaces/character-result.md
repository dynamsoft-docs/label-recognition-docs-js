---
layout: default-layout
title: Interface CharacterResult - Dynamsoft Label Recognizer JS Edition API Reference
description: The class CharacterResult of Dynamsoft Label Recognizer JS edition represents the result of a character recognition process.
keywords: Character result
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: CharacterResult
---

# CharacterResult

The `CharacterResult` class represents the result of a character recognition process. It contains the characters recognized (high, medium, and low confidence), their respective confidences, and the location of the character in a quadrilateral shape.

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

| Method                                        | Description                                                    |
| --------------------------------------------- | -------------------------------------------------------------- |
| [characterH](#characterh)                     | Returns the character with high confidence.                     |
| [characterM](#characterm)                     | Returns the character with medium confidence.                   |
| [characterL](#characterl)                     | Returns the character with low confidence.                      |
| [location](#location)                         | Returns the location of the character in a quadrilateral shape. |
| [characterHConfidence](#characterhconfidence) | Returns the confidence of the character with high confidence.   |
| [characterMConfidence](#charactermconfidence) | Returns the confidence of the character with medium confidence. |
| [characterLConfidence](#characterlconfidence) | Returns the confidence of the character with low confidence.    |

## characterH

Returns the character with high confidence.

```typescript
characterH: string
```

## characterM

Returns the character with medium confidence.

```typescript
characterM: string
```

## characterL

Returns the character with low confidence.

```typescript
characterL: string
```

## location

Returns the location of the character in a quadrilateral shape.

```typescript
location: Quadrilateral;
```

**See Also**

* [Quadrilateral]({{ site.dcv_js_api }}core/basic-structures/quadrilateral.html)

## characterHConfidence

Returns the confidence of the character with high confidence.

```typescript
characterHConfidence: number
```

## characterMConfidence

Returns the confidence of the character with medium confidence.

```typescript
characterMConfidence: number
```

## characterLConfidence

Returns the confidence of the character with low confidence.

```typescript
characterLConfidence: number
```
