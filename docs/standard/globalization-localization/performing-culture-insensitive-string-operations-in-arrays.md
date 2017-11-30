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
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a><span data-ttu-id="e2d46-102">Exécution d'opérations de chaînes indépendantes de la culture dans des tableaux</span><span class="sxs-lookup"><span data-stu-id="e2d46-102">Performing Culture-Insensitive String Operations in Arrays</span></span>
<span data-ttu-id="e2d46-103">Les surcharges de la <xref:System.Array.Sort%2A?displayProperty=nameWithType> et <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> méthodes effectuent des tris dépendante de la culture par défaut à l’aide du <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="e2d46-103">Overloads of the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods perform culture-sensitive sorts by default using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="e2d46-104">Résultats dépendante de la culture retournés par ces méthodes peuvent varier selon la culture en raison de différences dans les ordres de tri.</span><span class="sxs-lookup"><span data-stu-id="e2d46-104">Culture-sensitive results returned by these methods can vary by culture due to differences in sort orders.</span></span> <span data-ttu-id="e2d46-105">Pour éliminer le comportement dépendant de la culture, utilisez une des surcharges de cette méthode qui accepte un `comparer` paramètre.</span><span class="sxs-lookup"><span data-stu-id="e2d46-105">To eliminate culture-sensitive behavior, use one of the overloads of this method that accepts a `comparer` parameter.</span></span> <span data-ttu-id="e2d46-106">Le `comparer` paramètre spécifie le <xref:System.Collections.IComparer> implémentation à utiliser lors de la comparaison d’éléments dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="e2d46-106">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing elements in the array.</span></span> <span data-ttu-id="e2d46-107">Pour le paramètre, spécifiez une classe de comparateur indifférent personnalisé qui utilise <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e2d46-107">For the parameter, specify a custom invariant comparer class that uses <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e2d46-108">Un exemple d’une classe de comparateur personnalisé indifférent est fourni dans la sous-rubrique « À l’aide de la classe SortedList » de la [effectuer d’opérations de chaînes indépendantes de la Culture dans des Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="e2d46-108">An example of a custom invariant comparer class is provided in the "Using the SortedList Class" subtopic of the [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) topic.</span></span>  
  
 <span data-ttu-id="e2d46-109">**Remarque** passage **CultureInfo.InvariantCulture** à une comparaison méthode effectue une comparaison indépendante de la culture.</span><span class="sxs-lookup"><span data-stu-id="e2d46-109">**Note** Passing **CultureInfo.InvariantCulture** to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="e2d46-110">Toutefois, elle n’entraîne pas une comparaison non linguistique, par exemple, pour les chemins d’accès de fichier, les clés de Registre et les variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="e2d46-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="e2d46-111">Elle ne prend pas non plus en charge les décisions de sécurité basées sur le résultat de la comparaison.</span><span class="sxs-lookup"><span data-stu-id="e2d46-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="e2d46-112">Pour une comparaison non linguistique ou la prise en charge pour les décisions de sécurité basée sur les résultats, l’application doit utiliser une méthode de comparaison qui accepte une <xref:System.StringComparison> valeur.</span><span class="sxs-lookup"><span data-stu-id="e2d46-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="e2d46-113">L’application doit ensuite passer <xref:System.StringComparison.Ordinal>.</span><span class="sxs-lookup"><span data-stu-id="e2d46-113">The application should then pass <xref:System.StringComparison.Ordinal>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2d46-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2d46-114">See Also</span></span>  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [<span data-ttu-id="e2d46-115">Exécution d'opérations de chaînes indépendantes de la culture</span><span class="sxs-lookup"><span data-stu-id="e2d46-115">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
