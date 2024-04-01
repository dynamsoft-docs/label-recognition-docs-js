---
layout: default-layout
title: Interface LocalizedTextLineElement - Dynamsoft Label Recognizer JS Edition API Reference
description: The class LocalizedTextLineElement of Dynamsoft Label Recognizer JS edition represents a localized text line element.
keywords: Localized text line element
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: LocalizedTextLineElement
---

# LocalizedTextLineElement

The `LocalizedTextLineElement` class represents a localized text line element.

```typescript
interface LocalizedTextLineElement extends Core.RegionObjectElement {
    characterQuads: Array<Core.Quadrilateral>;
    rowNumber: number;
}
```
<!-- 
| Method                            | Description                                                    |
| --------------------------------- | -------------------------------------------------------------- |
| [characterQuads](#characterquads) | Returns the quadrilaterals of all characters in the text line. |
| [rowNumber](#rownumber)           | Returns the row number of the text line.                       | -->

## characterQuads

Returns the quadrilaterals of all characters in the text line.

```typescript
characterQuads: Array<Quadrilateral>;
```

**See Also**

* [Quadrilateral]({{ site.dcv_js_api }}core/basic-structures/quadrilateral.html)

## rowNumber

Returns the row number of the text line.

```typescript
rowNumber: number
```
