---
title: "Comment : résoudre des heures ambiguës"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3706747848dbcd29d4ed2e81d5b7447a127a653
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-resolve-ambiguous-times"></a>Comment : résoudre des heures ambiguës

Une heure ambiguë est une heure qui correspond à plusieurs heures UTC. Cela se produit lorsque l’heure de l’horloge est retardée, comme lors du passage à l’heure d’hiver dans un fuseau horaire. Lorsque vous gérez une heure ambiguë, vous pouvez procéder de l’une des manières suivantes :

* Proposez une méthode de mappage à l’heure UTC. Par exemple, vous pouvez supposer qu’une heure ambiguë est toujours exprimée dans le cadre de l’heure d’hiver du fuseau horaire.

* Si l’heure ambiguë est un élément de données entré par l’utilisateur, vous pouvez laisser l’utilisateur résoudre l’ambiguïté.

Cette rubrique montre comment résoudre une heure ambiguë en supposant qu’elle représente l’heure d’hiver du fuseau horaire.

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Pour mapper une heure ambiguë à l’heure d’hiver d’un fuseau horaire

1. Appelez le <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> méthode pour déterminer si l’heure est ambiguë.

2. Si l’heure est ambiguë, soustrayez l’heure de la <xref:System.TimeSpan> objet retourné par du fuseau horaire <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriété.

3. Appelez le `static` (`Shared` dans Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> pour définir la date et l’heure valeur UTC <xref:System.DateTime.Kind%2A> propriété <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Exemple

L’exemple suivant illustre comment convertir une heure ambiguë en heure UTC en supposant qu’elle représente l’heure d’hiver du fuseau horaire local.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

L’exemple se compose d’une méthode nommée `ResolveAmbiguousTime` qui détermine si le <xref:System.DateTime> valeur passée est ambiguë. Si la valeur est ambiguë, la méthode retourne un <xref:System.DateTime> valeur qui représente l’heure UTC correspondante. La méthode gère cette conversion en soustrayant la valeur du fuseau horaire local <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriété à partir de l’heure locale.

En règle générale, une heure ambiguë est contrôlée en appelant le <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> méthode pour récupérer un tableau de <xref:System.TimeSpan> offsets d’objets qui contiennent des UTC possibles de l’heure ambiguë. Toutefois, cet exemple émet l’hypothèse arbitraire qu’une heure ambiguë devrait toujours être mappée à l’heure d’hiver du fuseau horaire. Le <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriété retourne le décalage entre l’heure UTC et l’heure d’hiver d’un fuseau horaire.

Dans cet exemple, toutes les références dans le fuseau horaire local sont effectuées via le <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriété ; l’heure locale zone n’est jamais assigné à une variable objet. Ceci est une pratique recommandée, car un appel à la <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> méthode invalide le fuseau horaire local est attribué à tous les objets.

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

* Une référence à System.Core.dll à ajouter au projet.

* Que le <xref:System> espace de noms importés avec le `using` instruction (requise en code c#).

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
[Comment : permettre aux utilisateurs de résoudre des heures ambiguës](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
