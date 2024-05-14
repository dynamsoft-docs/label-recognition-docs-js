---
layout: default-layout
title: Interface BufferedCharacterItemSet - Dynamsoft Label Recognizer JS Edition API Reference
description: The interface BufferedCharacterItemSet of Dynamsoft Label Recognizer JS edition represents a collection of buffered character items. Each item in the collection is a BufferedCharacterItem object.
keywords: buffered character item set
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: BufferedCharacterItemSet
---

# BufferedCharacterItemSet

The `BufferedCharacterItemSet` interface represents a collection of buffered character items. Each item in the collection is a `BufferedCharacterItem` object.

```typescript
interface BufferedCharacterItemSet{
    items: Array<BufferedCharacterItem>; 
    characterClusters: Array<CharacterCluster>; 
}
```

## items

An array of `BufferedCharacterItem`.

```typescript
items: Array<BufferedCharacterItem>; 
```

**See Also**

* [BufferedCharacterItem](./buffered-character-item.md)

## characterClusters

An array of `CharacterCluster`.

```typescript
characterClusters: Array<CharacterCluster>; 
```

**See Also**

* [CharacterCluster](./character-cluster.md)