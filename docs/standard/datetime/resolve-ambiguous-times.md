---
title: "Comment&#160;: r&#233;soudre des heures ambigu&#235;s | Microsoft Docs"
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
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: r&#233;soudre des heures ambigu&#235;s
Une heure ambiguë est une heure qui peut être mappée à plusieurs UTC \(temps universel coordonné\).  Cela se produit lorsque l'heure de l'horloge est reculée, comme lors du passage de l'heure d'été à l'heure d'hiver dans un fuseau horaire.  Lorsque vous gérez une heure ambiguë, vous pouvez procéder de l'une des manières suivantes :  
  
-   Proposez une méthode de mappage à l'heure UTC.  Par exemple, vous pouvez supposer qu'une heure ambiguë est toujours exprimée en heure d'hiver du fuseau horaire.  
  
-   Si l'heure ambiguë est un élément de données entré par l'utilisateur, vous pouvez laisser l'utilisateur résoudre l'ambiguïté.  
  
 Cette rubrique indique comment résoudre une heure ambiguë en supposant qu'elle représente l'heure d'hiver du fuseau horaire.  
  
### Pour mapper une heure ambiguë à l'heure d'hiver d'un fuseau horaire  
  
1.  Appelez la méthode <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> pour déterminer si l'heure est ambiguë.  
  
2.  Si l'heure est ambiguë, soustrayez l'heure de l'objet <xref:System.TimeSpan> retourné par la propriété <xref:System.TimeZoneInfo.BaseUtcOffset%2A> du fuseau horaire.  
  
3.  Appelez la méthode `static` \(`Shared` dans Visual Basic .NET\) <xref:System.DateTime.SpecifyKind%2A> pour affecter la valeur <xref:System.DateTimeKind?displayProperty=fullName> à la propriété <xref:System.DateTime.Kind%2A> de la valeur de date et d'heure UTC.  
  
## Exemple  
 L'exemple suivant illustre comment convertir une heure ambiguë en heure UTC en supposant qu'elle représente l'heure d'hiver du fuseau horaire local.  
  
 [!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
 [!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]  
  
 L'exemple représente une méthode nommée `ResolveAmbiguousTime` qui détermine si la valeur <xref:System.DateTime> qui lui est passée est ambiguë.  Si la valeur est ambiguë, la méthode retourne une valeur <xref:System.DateTime> qui représente l'heure UTC correspondante.  La méthode gère cette conversion en soustrayant de l'heure locale la valeur de la propriété <xref:System.TimeZoneInfo.BaseUtcOffset%2A> du fuseau horaire local.  
  
 En règle générale, il est possible de gérer une heure ambiguë en appelant la méthode <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> pour récupérer un tableau des objets <xref:System.TimeSpan> qui contiennent les offsets UTC possibles de l'heure ambiguë.  Toutefois, cet exemple émet l'hypothèse arbitraire qu'une heure ambiguë devrait toujours être mappée à l'heure d'hiver du fuseau horaire.  La propriété <xref:System.TimeZoneInfo.BaseUtcOffset%2A> retourne l'offset entre l'heure UTC et l'heure d'hiver d'un fuseau horaire.  
  
 Dans cet exemple, toutes les références au fuseau horaire local sont faites via la propriété <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> ; le fuseau horaire local n'est jamais assigné à une variable objet.  Il est recommandé d'utiliser cette méthode, car un appel à la méthode <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=fullName> invalide les objets auxquels le fuseau horaire local est assigné.  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   qu'une référence à System.Core.dll soit ajoutée au projet ;  
  
-   que l'espace de noms <xref:System> soit importé avec l'instruction `using` \(requise en code C\#\).  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)   
 [Comment : permettre aux utilisateurs de résoudre des heures ambiguës](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)