---
layout: default-layout
title: Interface CharacterResult - Dynamsoft Label Recognizer JS Edition API Reference
description: The class CharacterResult of Dynamsoft Label Recognizer represents the result of a character recognition process.
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
| [characterH](#characterh)                     | Returns thecharacter with high confidence.                     |
| [characterM](#characterm)                     | Returns thecharacter with medium confidence.                   |
| [characterL](#characterl)                     | Returns thecharacter with low confidence.                      |
| [location](#location)                         | Returns thelocation of the character in a quadrilateral shape. |
| [characterHConfidence](#characterhconfidence) | Returns theconfidence of the character with high confidence.   |
| [characterMConfidence](#charactermconfidence) | Returns theconfidence of the character with medium confidence. |
| [characterLConfidence](#characterlconfidence) | Returns theconfidence of the character with low confidence.    |

## characterH

Returns thecharacter with high confidence.

```typescript
characterH: string
```

## characterM

Returns thecharacter with medium confidence.

```typescript
characterM: string
```

## characterL

Returns thecharacter with low confidence.

```typescript
characterL: string
```

## location

Returns thelocation of the character in a quadrilateral shape.

```typescript
location: Quadrilateral;
```

**See Also**

* [Quadrilateral]({{ site.dcv_js_api }}core/basic-structures/quadrilateral.html)

## characterHConfidence

Returns theconfidence of the character with high confidence.

```typescript
characterHConfidence: number
```

## characterMConfidence

Returns theconfidence of the character with medium confidence.

```typescript
characterMConfidence: number
```

## characterLConfidence

Returns theconfidence of the character with low confidence.

```typescript
characterLConfidence: number
```
