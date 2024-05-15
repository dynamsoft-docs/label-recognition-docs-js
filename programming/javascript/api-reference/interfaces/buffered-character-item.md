---
layout: default-layout
title: Interface BufferedCharacterItem - Dynamsoft Label Recognizer JS Edition API Reference
description: The interface BufferedCharacterItem of Dynamsoft Label Recognizer JS edition represents a buffered character item. Each buffered character item represents a recognized character along with its image and features.
keywords: Buffered character item
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: BufferedCharacterItem
---

# BufferedCharacterItem

The `BufferedCharacterItem` interface represents a buffered character item. Each buffered character item represents a recognized character along with its image and features.

```typescript
interface BufferedCharacterItem {
    character: string; 
    image: Core.DSImageData; 
    features: Array<{id: number, value: number}>; 
    }
```

## character

The buffered character value.

```typescript
character: string; 
```

## image

The image data of the buffered character.

```typescript
image: Core.DSImageData;  
```

**See Also**

* [DSImageData]({{ site.dcv_js_api }}core/basic-structures/ds-image-data.html)
  
## features

An array of features, each feature object contains feature id and value of the buffered character.

```typescript
features: Array<{id: number, value: number}>; 
```