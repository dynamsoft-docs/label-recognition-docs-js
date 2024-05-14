---
layout: default-layout
title: Interface CharacterCluster - Dynamsoft Label Recognizer JS Edition API Reference
description: The interface CharacterCluster of Dynamsoft Label Recognizer JS edition represents a character cluster generated from the buffered character items. These buffered items will be clustered based on feature similarity to obtain cluster centers.
keywords: character cluster
needGenerateH3Content: true
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: CharacterCluster
---

# CharacterCluster

The `CharacterCluster` interface represents a character cluster generated from the buffered character items. These buffered items will be clustered based on feature similarity to obtain cluster centers.

```typescript
interface CharacterCluster{
        character: string; 
        mean: BufferedCharacterItem; 
    }
```

## character

The character value of the cluster.

```typescript
character: string;  
```

## mean

The mean of the cluster.

```typescript
mean: BufferedCharacterItem; 
```

**See Also**

* [BufferedCharacterItem](./buffered-character-item.md)