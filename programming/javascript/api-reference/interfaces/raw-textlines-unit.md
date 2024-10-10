---
layout: default-layout
title: Interface RawTextLinesUnit - Dynamsoft Label Recognizer JS Edition API Reference
description: The interface RawTextLinesUnit of Dynamsoft Label Recognizer JS edition represents an intermediate result unit containing raw text lines.
keywords: Raw text lines unit
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: RawTextLinesUnit
---

# RawTextLinesUnit

The `RawTextLinesUnit` interface represents an intermediate result unit containing raw text lines.

```typescript
interface RawTextLinesUnit extends Core.IntermediateResultUnit {
    RawTextLines: Array<RawTextLine>;
}
```

## RawTextLines

An array of RawTextLine objects.

```typescript
RawTextLines: Array<RawTextLine>;
```

**See Also**

* [RawTextLine]({{ site.dlr_js_api }}interfaces/raw-text-line.html)
