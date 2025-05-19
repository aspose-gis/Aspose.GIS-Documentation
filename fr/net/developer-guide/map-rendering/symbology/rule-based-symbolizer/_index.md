---
title: "Symboliseur basé sur des règles"
type: docs
url: /fr/net/rule-based-symbolizer/
weight: 60
description: Le symboliseur basé sur des règles dans la bibliothèque ou l'API C# GIS applique d'autres symboliseurs aux géométries des entités en fonction de règles arbitraires codées en C#.
---

## **Symboliseur basé sur des règles**
Le symboliseur basé sur des règles est le symboliseur le plus flexible. Il applique d'autres symboliseurs aux géométries des entités en fonction de règles arbitraires codées en C#.

Si plusieurs règles correspondent à une entité, tous les symboliseurs correspondants seront appliqués. Vous pouvez spécifier un symboliseur à appliquer aux entités qui ne correspondaient à aucune règle en appelant [AddElseRule](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer/methods/addelserule).
