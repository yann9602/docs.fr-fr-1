---
title: "Comment&#160;: acc&#233;der aux objets UTC et aux objets de fuseau horaire local pr&#233;d&#233;finis | Microsoft Docs"
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
  - "accès au fuseau horaire local"
  - "fuseaux horaires prédéfinis"
  - "fuseaux horaires (.NET Framework), locaux"
  - "fuseaux horaires (.NET Framework), récupérer"
  - "fuseaux horaires (.NET Framework), UTC"
  - "temps UTC, prédéfinis"
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: acc&#233;der aux objets UTC et aux objets de fuseau horaire local pr&#233;d&#233;finis
La classe <xref:System.TimeZoneInfo> fournit deux propriétés, <xref:System.TimeZoneInfo.Utc%2A> et <xref:System.TimeZoneInfo.Local%2A>, qui permettent à votre code d'accéder à des objets de fuseau horaire prédéfinis.  Cette rubrique explique comment accéder aux objets <xref:System.TimeZoneInfo> retournés par ces propriétés.  
  
### Pour accéder à l'objet TimeZoneInfo de temps universel coordonné \(UTC, Coordinated Universal Time\)  
  
1.  Utilisez la propriété `static` \(`Shared` dans Visual Basic\) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=fullName> pour accéder au temps universel coordonné.  
  
2.  Plutôt que d'assigner l'objet <xref:System.TimeZoneInfo> retourné par la propriété à une variable objet, utilisez la propriété <xref:System.TimeZoneInfo.Utc%2A?displayProperty=fullName> pour accéder au temps universel coordonné.  
  
### Pour accéder au fuseau horaire local  
  
1.  Utilisez la propriété `static` \(`Shared` dans Visual Basic\) <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> pour accéder au fuseau horaire du système local.  
  
2.  Plutôt que d'assigner l'objet <xref:System.TimeZoneInfo> retourné par la propriété à une variable objet, utilisez la propriété <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> pour accéder au fuseau horaire local.  
  
## Exemple  
 Le code ci\-dessous utilise les propriétés <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> et <xref:System.TimeZoneInfo.Utc%2A?displayProperty=fullName> pour convertir un point des États\-Unis et le fuseau horaire standard de l'Est canadien, ainsi que pour afficher le nom du fuseau horaire à la console.  
  
 [!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
 [!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]  
  
 Vous devez toujours utiliser la propriété <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> pour accéder au fuseau horaire local plutôt que d'assigner le fuseau horaire local à une variable objet <xref:System.TimeZoneInfo>.  De la même façon, vous devez toujours faire appel à la propriété <xref:System.TimeZoneInfo.Utc%2A?displayProperty=fullName> pour accéder au temps universel coordonné plutôt que d'assigner le fuseau horaire UTC à une variable objet <xref:System.TimeZoneInfo>.  Ainsi, la variable objet <xref:System.TimeZoneInfo> ne peut pas être invalidée par un appel à la méthode <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=fullName>.  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   qu'une référence à System.Core.dll soit ajoutée au projet ;  
  
-   que l'espace de noms <xref:System> soit importé avec l'instruction `using` \(requise en code C\#\).  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)   
 [Recherche des fuseaux horaires définis sur un système local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)   
 [Comment : instancier un objet TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)