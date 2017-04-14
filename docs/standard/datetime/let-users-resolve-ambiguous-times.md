---
title: "Comment&#160;: permettre aux utilisateurs de r&#233;soudre des heures ambigu&#235;s | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "heure ambiguë (.NET Framework)"
  - "fuseaux horaires (.NET Framework), heure ambiguë"
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: permettre aux utilisateurs de r&#233;soudre des heures ambigu&#235;s
Une heure ambiguë est une heure qui peut être mappée à plusieurs UTC \(temps universel coordonné\).  Cela se produit lorsque l'heure de l'horloge est reculée, comme lors du passage de l'heure d'été à l'heure d'hiver dans un fuseau horaire.  Lorsque vous gérez une heure ambiguë, vous pouvez procéder de l'une des manières suivantes :  
  
-   Si l'heure ambiguë est un élément de données entré par l'utilisateur, vous pouvez laisser l'utilisateur résoudre l'ambiguïté.  
  
-   Proposez une méthode de mappage à l'heure UTC.  Par exemple, vous pouvez supposer qu'une heure ambiguë est toujours exprimée en heure d'hiver du fuseau horaire.  
  
 Cette rubrique indique comment permettre à un utilisateur de résoudre une heure ambiguë.  
  
### Pour permettre à un utilisateur de résoudre une heure ambiguë  
  
1.  Obtenez la date et l'heure entrées par l'utilisateur.  
  
2.  Appelez la méthode <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> pour déterminer si l'heure est ambiguë.  
  
3.  Si l'heure est ambiguë, appelez la méthode <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> pour récupérer un tableau d'objets <xref:System.TimeSpan>.  Chaque élément du tableau contient un offset UTC auquel l'heure ambiguë peut être mappée.  
  
4.  Laissez l'utilisateur sélectionner l'offset désiré.  
  
5.  Calculez la date et l'heure UTC en soustrayant l'offset sélectionné par l'utilisateur de l'heure locale.  
  
6.  Appelez la méthode `static` \(`Shared` dans Visual Basic .NET\) <xref:System.DateTime.SpecifyKind%2A> pour affecter la valeur <xref:System.DateTimeKind?displayProperty=fullName> à la propriété <xref:System.DateTime.Kind%2A> de la valeur de date et d'heure UTC.  
  
## Exemple  
 L'exemple suivant invite l'utilisateur à entrer une date et une heure et, si cette dernière est ambiguë, lui permet de sélectionner l'heure UTC à laquelle l'heure ambiguë est mappée.  
  
 [!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
 [!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]  
  
 La partie principale de l'exemple de code utilise un tableau d'objets <xref:System.TimeSpan> pour indiquer les offsets possibles de l'heure ambiguë par rapport à l'heure UTC.  Toutefois, ces offsets ne seront probablement pas explicites pour l'utilisateur.  Pour clarifier leur signification, le code note également si un offset représente l'heure d'hiver du fuseau horaire local ou son heure d'été.  Le code détermine l'heure d'hiver et l'heure d'été en comparant l'offset avec la valeur de la propriété <xref:System.TimeZoneInfo.BaseUtcOffset%2A>.  Cette propriété indique la différence entre l'heure UTC et l'heure d'hiver du fuseau horaire.  
  
 Dans cet exemple, toutes les références au fuseau horaire local sont faites via la propriété <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> ; le fuseau horaire local n'est jamais assigné à une variable objet.  Il est recommandé d'utiliser cette méthode, car un appel à la méthode <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=fullName> invalide les objets auxquels le fuseau horaire local est assigné.  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   qu'une référence à System.Core.dll soit ajoutée au projet ;  
  
-   que l'espace de noms <xref:System> soit importé avec l'instruction `using` \(requise en code C\#\).  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)   
 [Comment : résoudre des heures ambiguës](../../../docs/standard/datetime/resolve-ambiguous-times.md)