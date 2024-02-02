---
layout: default-layout
title: Interface LocalizedTextLinesUnit - Dynamsoft Label Recognizer JS Edition API Reference
description: The class LocalizedTextLinesUnit of Dynamsoft Label Recognizer represents a unit that contains localized text lines.
keywords: Localized text lines unit
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: LocalizedTextLinesUnit
---

# LocalizedTextLinesUnit

The `LocalizedTextLinesUnit` class represents a unit that contains localized text lines.

```typescript
interface LocalizedTextLinesUnit extends Core.IntermediateResultUnit {
    localizedTextLines: Array<LocalizedTextLineElement>;
}
```

| Method                                    | Description                               |
| ----------------------------------------- | ----------------------------------------- |
| [localizedTextLines](#localizedtextlines) | Returns the localized text line elements. |

## localizedTextLines

Returns the localized text line elements.

```typescript
localizedTextLines: Array<LocalizedTextLineElement>;
```

**See Also**

* [LocalizedTextLineElement](./localized-text-line-element.md)
