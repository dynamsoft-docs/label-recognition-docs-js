---
layout: default-layout
title: Interface LocalizedTextLinesUnit - Dynamsoft Label Recognizer JS Edition API Reference
description: The interface LocalizedTextLinesUnit of Dynamsoft Label Recognizer JS edition represents a unit that contains localized text lines.
keywords: Localized text lines unit
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: LocalizedTextLinesUnit
---

# LocalizedTextLinesUnit

The `LocalizedTextLinesUnit` interface represents a unit that contains localized text lines.

```typescript
interface LocalizedTextLinesUnit extends Core.IntermediateResultUnit {
    localizedTextLines: Array<LocalizedTextLineElement>;
}
```

<!-- | Method                                    | Description                               |
| ----------------------------------------- | ----------------------------------------- |
| [localizedTextLines](#localizedtextlines) | Returns the localized text line elements. | -->

## localizedTextLines

The localized text line elements.

```typescript
localizedTextLines: Array<LocalizedTextLineElement>;
```

**See Also**

* [LocalizedTextLineElement]({{ site.dlr_js_api }}interfaces/localized-textline-element.html)
