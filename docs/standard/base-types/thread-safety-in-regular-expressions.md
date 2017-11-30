---
title: "Sécurité des threads dans les expressions régulières"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4cfa24da8083eac01275ad76f5c2db974b39a25
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="df40c-102">Sécurité des threads dans les expressions régulières</span><span class="sxs-lookup"><span data-stu-id="df40c-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="df40c-103">La <xref:System.Text.RegularExpressions.Regex> classe elle-même est thread-safe et immuable (en lecture seule).</span><span class="sxs-lookup"><span data-stu-id="df40c-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="df40c-104">Autrement dit, des objets **Regex** peuvent être créés sur n’importe quel thread et partagés par plusieurs threads ; les méthodes de mise en correspondance peuvent être appelées à partir de n’importe quel thread et elles ne modifient jamais un état global.</span><span class="sxs-lookup"><span data-stu-id="df40c-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="df40c-105">Toutefois, les objets de résultats (**correspondance** et **MatchCollection**) retourné par **Regex** doit être utilisé sur un thread unique.</span><span class="sxs-lookup"><span data-stu-id="df40c-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="df40c-106">Bien que bon nombre de ces objets soient logiquement immuables, leurs implémentations peuvent retarder le calcul de certains résultats pour améliorer les performances, et par conséquent, les appelants doivent en sérialiser l’accès.</span><span class="sxs-lookup"><span data-stu-id="df40c-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="df40c-107">S’il est nécessaire de partager des objets de résultat **Regex** sur plusieurs threads, ces objets peuvent être convertis en instances thread-safe en appelant leurs méthodes synchronisées.</span><span class="sxs-lookup"><span data-stu-id="df40c-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="df40c-108">À l’exception des énumérateurs, toutes les classes d’expression régulière sont thread-safe ou peuvent être converties en objets thread-safe par une méthode synchronisée.</span><span class="sxs-lookup"><span data-stu-id="df40c-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="df40c-109">Les énumérateurs sont la seule exception.</span><span class="sxs-lookup"><span data-stu-id="df40c-109">Enumerators are the only exception.</span></span> <span data-ttu-id="df40c-110">Une application doit sérialiser les appels aux énumérateurs de collections.</span><span class="sxs-lookup"><span data-stu-id="df40c-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="df40c-111">La règle est que si une collection peut être énumérée simultanément sur plusieurs threads, vous devez synchroniser les méthodes d’énumération sur l’objet racine de la collection traversée par l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="df40c-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df40c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df40c-112">See Also</span></span>  
 [<span data-ttu-id="df40c-113">Expressions régulières .NET</span><span class="sxs-lookup"><span data-stu-id="df40c-113">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
