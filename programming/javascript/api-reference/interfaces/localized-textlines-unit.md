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
    auxiliaryRegionElements: Array<AuxiliaryRegionElement>;
}
```

| Property                                                    | Description                                                      |
| ----------------------------------------------------------- | ---------------------------------------------------------------- |
| [localizedTextLines](#localizedtextlines)                   | An array of localized text line elements.                        |
| [auxiliaryRegionElements](#auxiliaryregionelements)         | An array of auxiliary region elements.                           |

## localizedTextLines

An array of `LocalizedTextLineElement` objects, each representing a localized text line.

```typescript
localizedTextLines: Array<LocalizedTextLineElement>;
```

**See Also**

* [LocalizedTextLineElement]({{ site.dlr_js_api }}interfaces/localized-textline-element.html)

## auxiliaryRegionElements

An array of `AuxiliaryRegionElement` objects, each representing an auxiliary region.

```typescript
auxiliaryRegionElements: Array<AuxiliaryRegionElement>;
```

**See Also**

* [AuxiliaryRegionElement]({{ site.dcv_js_api }}core/intermediate-results/auxiliary-region-element.html)
