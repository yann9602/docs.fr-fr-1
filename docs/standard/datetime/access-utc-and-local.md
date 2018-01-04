---
title: "Comment : accéder aux objets de zone prédéfinis UTC et l’heure locale"
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
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 600dbb98264c4750db1ffb98b757ad191eaf4fe5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Comment : accéder aux objets de zone prédéfinis UTC et l’heure locale

Le <xref:System.TimeZoneInfo> classe fournit deux propriétés, <xref:System.TimeZoneInfo.Utc%2A> et <xref:System.TimeZoneInfo.Local%2A>, qui donnent accès de votre code à des objets de fuseaux horaires prédéfinis. Cette rubrique explique comment accéder aux objets <xref:System.TimeZoneInfo> retournés par ces propriétés.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Pour accéder à l’objet TimeZoneInfo de temps universel coordonné (UTC)

1. Utilisez le `static` (`Shared` en Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriété pour accéder au temps universel coordonné.

2. Plutôt que d’attribuer le <xref:System.TimeZoneInfo> objet retourné par la propriété à une variable objet, continuer à accéder au temps universel via la <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriété.

### <a name="to-access-the-local-time-zone"></a>Pour accéder au fuseau horaire local

1. Utilisez le `static` (`Shared` en Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriété pour accéder au fuseau horaire de système local.

2. Plutôt que d’attribuer le <xref:System.TimeZoneInfo> objet retourné par la propriété à une variable objet, continuer à accéder au fuseau horaire local via le <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriété.

## <a name="example"></a>Exemple

Le code suivant utilise la <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> et <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriétés pour convertir une heure du fuseau horaire des États-Unis et Canada est Standard, ainsi que pour afficher le nom du fuseau horaire dans la console.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Vous devez toujours accéder au fuseau horaire local via la <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriété au lieu d’affecter l’heure locale de la zone à une <xref:System.TimeZoneInfo> variable objet. De même, vous devez toujours accéder temps universel via la <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriété au lieu d’affecter l’heure UTC de la zone à une <xref:System.TimeZoneInfo> variable objet. Cela empêche le <xref:System.TimeZoneInfo> variable objet est invalidée par un appel à la <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> (méthode).

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

* Une référence à System.Core.dll à ajouter au projet.

* Que le <xref:System> espace de noms importés avec le `using` instruction (requise en code c#).

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
[recherche des fuseaux horaires définis sur un système local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[Comment : instancier un objet TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
