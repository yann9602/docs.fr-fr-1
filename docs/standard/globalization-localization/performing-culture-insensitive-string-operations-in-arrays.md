---
title: "Exécution d'opérations de chaînes indépendantes de la culture dans des tableaux"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b4e040ed379cdbf43fbe8b2c4379fdd4dc781f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Exécution d'opérations de chaînes indépendantes de la culture dans des tableaux
Les surcharges de la <xref:System.Array.Sort%2A?displayProperty=nameWithType> et <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> méthodes effectuent des tris dépendante de la culture par défaut à l’aide du <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> propriété. Résultats dépendante de la culture retournés par ces méthodes peuvent varier selon la culture en raison de différences dans les ordres de tri. Pour éliminer le comportement dépendant de la culture, utilisez une des surcharges de cette méthode qui accepte un `comparer` paramètre. Le `comparer` paramètre spécifie le <xref:System.Collections.IComparer> implémentation à utiliser lors de la comparaison d’éléments dans le tableau. Pour le paramètre, spécifiez une classe de comparateur indifférent personnalisé qui utilise <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Un exemple d’une classe de comparateur personnalisé indifférent est fourni dans la sous-rubrique « À l’aide de la classe SortedList » de la [effectuer d’opérations de chaînes indépendantes de la Culture dans des Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) rubrique.  
  
 **Remarque** passage **CultureInfo.InvariantCulture** à une comparaison méthode effectue une comparaison indépendante de la culture. Toutefois, elle n’entraîne pas une comparaison non linguistique, par exemple, pour les chemins d’accès de fichier, les clés de Registre et les variables d’environnement. Elle ne prend pas non plus en charge les décisions de sécurité basées sur le résultat de la comparaison. Pour une comparaison non linguistique ou la prise en charge pour les décisions de sécurité basée sur les résultats, l’application doit utiliser une méthode de comparaison qui accepte une <xref:System.StringComparison> valeur. L’application doit ensuite passer <xref:System.StringComparison.Ordinal>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [Exécution d'opérations de chaînes indépendantes de la culture](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
