---
title: "Comment&#160;: utiliser des fuseaux horaires en arithm&#233;tique de date et heure | Microsoft Docs"
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
  - "opérations arithmétiques (.NET Framework), dates et heures"
  - "dates (.NET Framework), ajouter et retrancher"
  - "fuseaux horaires (.NET Framework), opérations arithmétiques"
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: utiliser des fuseaux horaires en arithm&#233;tique de date et heure
Généralement, lorsque vous effectuez des opérations arithmétiques de date et heure à l'aide des valeurs <xref:System.DateTime> ou <xref:System.DateTimeOffset>, le résultat ne reflète aucune règle d'ajustement de fuseau horaire.  Cela est vrai même lorsque le fuseau horaire de la valeur de date et d'heure est clairement identifiable \(par exemple, lorsque la propriété <xref:System.DateTime.Kind%2A> a la valeur <xref:System.DateTimeKind>\).  Cette rubrique indique comment exécuter des opérations arithmétiques sur des valeurs de date et d'heure qui appartiennent à un fuseau horaire particulier.  Les résultats des opérations arithmétiques refléteront les règles d'ajustement du fuseau horaire.  
  
### Pour appliquer des règles d'ajustement à l'arithmétique de date et heure  
  
1.  Implémentez une méthode permettant de coupler fortement une valeur de date et d'heure avec le fuseau horaire auquel elle appartient.  Par exemple, déclarez une structure qui inclut la valeur de date et d'heure et son fuseau horaire.  L'exemple suivant utilise cette approche pour lier une valeur <xref:System.DateTime> à son fuseau horaire.  
  
     [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
     [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]  
  
2.  Convertissez une heure en temps universel coordonné \(UTC, Coordinated Universal Time\) en appelant la méthode <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> ou la méthode <xref:System.TimeZoneInfo.ConvertTime%2A>.  
  
3.  Exécutez l'opération arithmétique sur l'heure UTC.  
  
4.  Convertissez l'heure UTC en un fuseau horaire associé à l'heure d'origine en appelant la méthode <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=fullName>.  
  
## Exemple  
 L'exemple suivant ajoute deux heures et trente minutes au 9 mars 2008, à 1h30 du matin, heure du Centre \(des États\-Unis\).  Le passage du fuseau horaire à l'heure d'été a lieu trente minutes plus tard, à 02H00 du matin le 9 Mars 2008.  Étant donné que l'exemple suit les quatre étapes répertoriées dans la section précédente, il indique l'heure correcte c'est\-à\-dire 05H00 du matin; le 9 Mars 2008.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
 [!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]  
  
 Les valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset> sont dissociées de tout fuseau horaire auquel elles peuvent appartenir.  Pour exécuter des opérations arithmétiques de date et heure qui appliquent automatiquement les règles d'ajustement d'un fuseau horaire, le fuseau horaire auquel toute valeur de date et d'heure appartient doit être immédiatement identifiable.  Cela signifie qu'une date et une heure, ainsi que le fuseau horaire associé, doivent être fortement couplés.  Vous disposez de plusieurs méthodes pour y parvenir, comme celles décrites ci\-dessous.  
  
-   Supposez que toutes les heures utilisées dans une application appartiennent à un fuseau horaire particulier.  Bien qu'appropriée dans certains cas, cette approche présente une souplesse et une portabilité limitées.  
  
-   Définissez un type qui couple fortement une date et une heure avec le fuseau horaire associé en les incluant en tant que champs du type.  Cette approche est utilisée dans l'exemple de code qui définit une structure permettant de stocker la date et l'heure, ainsi que le fuseau horaire, dans deux champs membre.  
  
 L'exemple illustre comment exécuter des opérations arithmétiques sur les valeurs <xref:System.DateTime> pour appliquer les règles d'ajustement de fuseau horaire au résultat.  Les valeurs <xref:System.DateTimeOffset> peuvent tout aussi bien être utilisées.  L'exemple suivant illustre comment le code de l'exemple d'origine peut être adapté pour utiliser <xref:System.DateTimeOffset> au lieu de <xref:System.DateTime>.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
 [!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]  
  
 Notez que si cet ajout est appliqué à la valeur <xref:System.DateTimeOffset> alors qu'elle n'a pas été préalablement convertie en heure UTC, le résultat indique le point correct dans le temps, mais son offset ne reflète pas celui du fuseau horaire désigné pour cette heure.  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   qu'une référence à System.Core.dll soit ajoutée au projet ;  
  
-   que l'espace de noms <xref:System> soit importé avec l'instruction `using` \(requise en code C\#\).  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)   
 [Exécution d'opérations arithmétiques avec des dates et heures](../../../docs/standard/datetime/performing-arithmetic-operations.md)