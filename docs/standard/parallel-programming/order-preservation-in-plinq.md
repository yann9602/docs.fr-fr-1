---
title: Conservation de l'ordre en PLINQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, order preservation
ms.assetid: 10d202bc-19e1-4b5c-bbf1-9a977322a9ca
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 060459cf8f408e40ddc394fbcda6a022ec6379de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="order-preservation-in-plinq"></a>Conservation de l'ordre en PLINQ
Dans PLINQ, vise à optimiser les performances tout en préservant leur exactitude. Une requête doit s’exécuter aussi rapidement que possible, mais toujours générer des résultats corrects. Dans certains cas, l’exactitude requiert que l’ordre de la séquence source soit conservé ; Toutefois, le classement peut être sollicite. Par conséquent, par défaut, PLINQ ne conserve pas l’ordre de la séquence source. À cet égard, PLINQ est similaire à [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)], mais contrairement à LINQ to Objects, il conserve l’ordre.  
  
 Pour substituer le comportement par défaut, vous pouvez activer sur la conservation de l’ordre à l’aide de la <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> opérateur sur la séquence source. Vous pouvez désactiver la préservation de commande plus loin dans la requête à l’aide de la <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> (méthode). Avec ces deux méthodes, la requête est traitée en fonction des paramètres heuristiques qui déterminent s’il faut exécuter la requête en parallèle ou séquentielle. Pour plus d’informations, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
 L’exemple suivant montre une requête parallèle non classée qui filtre pour tous les éléments qui correspondent à une condition, sans essayer de classer les résultats de toute façon.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 Cette requête ne produit pas nécessairement les 1000 premières villes de la séquence source qui remplissent la condition, mais plutôt un ensemble de 1000 villes qui répondent à la condition. Opérateurs de requête PLINQ partitionnent la séquence source en plusieurs sous-séquences sont traités comme des tâches simultanées. Si la conservation de l’ordre n’est pas spécifiée, les résultats de chaque partition sont remis à l’étape suivante de la requête dans un ordre arbitraire. En outre, une partition peut entraîner un sous-ensemble de ses résultats avant de continuer à traiter les éléments restants. L’ordre résultant peut être différent à chaque fois. Votre application ne peut pas contrôler cela car il dépend de la manière dont le système d’exploitation planifie les threads.  
  
 L’exemple suivant substitue le comportement par défaut à l’aide de la <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> opérateur sur la séquence source. Cela garantit que le <xref:System.Linq.ParallelEnumerable.Take%2A> méthode retourne les 1000 premières villes de la séquence source qui remplissent la condition.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Toutefois, cette requête probablement ne s’exécute pas aussi rapidement que la version non ordonnée, car il doit effectuer le suivi de l’ordre d’origine dans toutes les partitions et au moment de la fusion, vérifiez que le classement est cohérent. Par conséquent, nous vous recommandons d’utiliser <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> uniquement lorsqu’il est requis et uniquement pour les parties de la requête qui en ont besoin. Lors de la conservation de l’ordre n’est plus nécessaire, utilisez <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> pour le désactiver. L’exemple suivant effectue ceci en composant des deux requêtes.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 Notez que PLINQ conserve le classement d’une séquence de produits par les opérateurs d’ordre pour le reste de la requête. En d’autres termes, les opérateurs tels que <xref:System.Linq.ParallelEnumerable.OrderBy%2A> et <xref:System.Linq.ParallelEnumerable.ThenBy%2A> sont traités comme s’ils étaient suivis d’un appel à <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
## <a name="query-operators-and-ordering"></a>Opérateurs de requête et de classement  
 Les opérateurs de requête suivants présentent la conservation de l’ordre dans toutes les opérations suivantes dans une requête ou jusqu'à ce que <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> est appelée :  
  
-   <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 Les opérateurs de requête PLINQ suivants peuvent dans certains cas nécessitent que les séquences sources classées pour produire des résultats corrects :  
  
-   <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Certains opérateurs de requête PLINQ se comportent différemment, selon que leur séquence source est ordonné ou non ordonné. Le tableau suivant répertorie ces opérateurs.  
  
|Opérateur|Résultat de la séquence source est classée|Résultat de la séquence source n’est pas ordonnée|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Sortie non déterministe pour les opérations non associatives ou non commutatives|Sortie non déterministe pour les opérations non associatives ou non commutatives|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Sortie non déterministe pour les opérations non associatives ou non commutatives|Sortie non déterministe pour les opérations non associatives ou non commutatives|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Résultats classés|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Résultats classés|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Résultats classés|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Retourne l’élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Retourne l’élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Résultats non triées|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Retourne l’élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Retourne l’élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Exécute de façon non déterminante en parallèle|Exécute de façon non déterminante en parallèle|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Résultats classés|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Résultats classés|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Résultats classés|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Résultats classés|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Retourne l’élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Retourne l’élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Réorganise la séquence|Démarre la nouvelle section classée|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Réorganise la séquence|Démarre la nouvelle section classée|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Non applicable (même valeur par défaut en tant que <xref:System.Linq.ParallelEnumerable.AsParallel%2A> )|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Non applicable (même valeur par défaut en tant que <xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Inverse|Sans effet|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Résultats classés|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>(index)|Résultats classés|Résultats non triées.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Résultats classés.|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>(index)|Résultats classés.|Résultats non triées.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Comparaison classée|Comparaison non classée|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Ignore tout d’abord  *n*  éléments|Ignore les  *n*  éléments|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Résultats classés.|Non déterministe. Exécute SkipWhile sur l’ordre arbitraire actuel|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Sortie non déterministe pour les opérations non associatives ou non commutatives|Sortie non déterministe pour les opérations non associatives ou non commutatives|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Prend en premier `n` éléments|Accepte les `n` éléments|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Résultats classés|Non déterministe. Exécute TakeWhile sur l’ordre arbitraire actuel|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Compléments`OrderBy`|Compléments`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Compléments`OrderBy`|Compléments`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Résultats classés|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Résultats classés|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Résultats classés|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Résultats classés|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Résultats classés|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>(index)|Résultats classés|Résultats non triées|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Résultats classés|Résultats non triées|  
  
 Résultats non classés ne sont pas activement mélangées ; Il vous suffit, ils n’ont pas une logique spéciale de tri appliquée. Dans certains cas, une requête non classée peut conserver le classement de la séquence source. Pour les requêtes qui utilisent l’opérateur Select indexé, PLINQ garantit que les éléments de sortie proviendront dans l’ordre croissant indices, mais n’offre aucune garantie quant à la nature des index n’est affectés à quels éléments.  
  
## <a name="see-also"></a>Voir aussi  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Programmation parallèle](../../../docs/standard/parallel-programming/index.md)
