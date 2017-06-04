---
title: "Order Preservation in PLINQ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PLINQ queries, order preservation"
ms.assetid: 10d202bc-19e1-4b5c-bbf1-9a977322a9ca
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Order Preservation in PLINQ
En PLINQ, l'objectif est de maximiser les performances tout en maintenant l'exactitude.  Une requête doit s'exécuter aussi rapidement que possible mais doit produire des résultats corrects.  Dans certains cas, l'exactitude requiert que l'ordre de la séquence source soit conservé ; toutefois, le classement sollicite fortement les ressources informatiques.  Par conséquent, PLINQ ne conserve pas par défaut l'ordre de la séquence source.  À cet égard, PLINQ est similaire à [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)], mais contrairement à LINQ to Objects, il ne conserve pas le classement.  
  
 Pour substituer le comportement par défaut, vous pouvez activer la conservation de l'ordre en utilisant l'opérateur <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> sur la séquence source.  Vous pouvez désactiver ultérieurement la conservation de l'ordre dans la requête à l'aide de la méthode <xref:System.Linq.ParallelEnumerable.AsUnordered%2A>.  Avec les deux méthodes, la requête est traitée en fonction des paramètres heuristiques qui déterminent si la requête doit être exécutée de manière parallèle ou séquentielle.  Pour plus d'informations, consultez [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
 L'exemple suivant affiche une requête parallèle non classée qui filtre tous les éléments qui correspondent à une condition, sans essayer de classer les résultats.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 Cette requête ne renvoie pas nécessairement les 1000 premières villes de la séquence source qui remplissent la condition, mais plutôt un ensemble de 1000 villes qui remplissent la condition.  Les opérateurs de requête PLINQ partitionnent la séquence source en plusieurs sous\-séquences traitées comme des tâches simultanées.  Si la conservation de l'ordre n'est pas spécifiée, les résultats de chaque partition sont donnés à l'étape suivante de la requête dans un ordre arbitraire.  De plus, une partition peut transmettre un sous\-ensemble de ses résultats avant de continuer le traitement des éléments restants.  L'ordre résultant peut être différent à chaque fois.  Votre application ne peut pas contrôler cela parce cela dépend de la manière dont le système d'exploitation planifie les threads.  
  
 L'exemple suivant substitue le comportement par défaut en utilisant l'opérateur <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> sur la séquence source.  Cela vérifie que la méthode <xref:System.Linq.ParallelEnumerable.Take%2A> retourne les 1000 premières villes de la séquence source qui remplissent la condition.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Toutefois, cette requête ne s'exécute pas aussi rapidement que la version non classée probablement parce qu'elle doit effectuer le suivi du classement d'origine dans toutes les partitions et vérifier que le classement est cohérent au moment de la fusion.  Par conséquent, il est recommandé d'utiliser <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> uniquement lorsque cela est obligatoire et uniquement pour les parties de la requête qui le nécessitent.  Lorsque la conservation de l'ordre n'est plus obligatoire, utilisez <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> pour la désactiver.  L'exemple suivant effectue ceci en composant deux requêtes.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 Notez que PLINQ conserve le classement d'une séquence produit par les opérateurs d'ordre pour le reste de la requête.  En d'autres termes, les opérateurs tels que <xref:System.Linq.ParallelEnumerable.OrderBy%2A> et <xref:System.Linq.ParallelEnumerable.ThenBy%2A> sont traités comme s'ils étaient suivis d'un appel à <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
## Opérateurs de requête et classement  
 Les opérateurs de requête suivants présentent la conservation de l'ordre dans toutes les opérations suivantes d'une requête ou jusqu'à ce que <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> soit appelé :  
  
-   <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 Les opérateurs de requête PLINQ suivants peuvent nécessiter dans certains cas que les séquences sources classées produisent des résultats corrects :  
  
-   <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Certains opérateurs de requête PLINQ se comportent différemment, selon que leur séquence source est classée ou non.  Le tableau suivant répertorie ces opérateurs.  
  
|Opérateur|Résultat si la séquence source est classée|Résultat si la séquence source n'est pas classée|  
|---------------|------------------------------------------------|------------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Sortie non déterministe pour les opérations non associatives ou non commutatives|Sortie non déterministe pour les opérations non associatives ou non commutatives|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Sortie non déterministe pour les opérations non associatives ou non commutatives|Sortie non déterministe pour les opérations non associatives ou non commutatives|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Retourne l'élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Retourne l'élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Résultats non classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Retourne l'élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Retourne l'élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Exécute en parallèle de manière non déterministe|Exécute en parallèle de manière non déterministe|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Retourne l'élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Retourne l'élément spécifié|Élément arbitraire|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Réorganise la séquence|Démarre la nouvelle section classée|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Réorganise la séquence|Démarre la nouvelle section classée|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Non applicable \(même valeur par défaut que <xref:System.Linq.ParallelEnumerable.AsParallel%2A>\)|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Non applicable \(même valeur par défaut que <xref:System.Linq.ParallelEnumerable.AsParallel%2A>\)|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Inverse|Sans effet|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Select%2A> \(indexé\)|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A> \(indexé\)|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Comparaison classée|Comparaison non classée|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Ignore les *n* premier éléments|Ignore tous élément *n*|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Résultats classés|Non déterministe  Exécute SkipWhile sur l'ordre arbitraire actuel|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Sortie non déterministe pour les opérations non associatives ou non commutatives|Sortie non déterministe pour les opérations non associatives ou non commutatives|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Prend en premier les éléments `n`|Prend tous les éléments `n`|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Résultats classés|Non déterministe  Exécute TakeWhile sur l'ordre arbitraire actuel|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Complète `OrderBy`|Complète `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Complète `OrderBy`|Complète `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Non applicable|Non applicable|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Where%2A> \(indexé\)|Résultats classés|Résultats non classés|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Résultats classés|Résultats non classés|  
  
 Les résultats non classés ne sont pas lus activement de manière aléatoire ; tout simplement, aucune logique de tri spéciale ne leur est appliquée.  Dans certains cas, une requête non classée peut conserver le classement de la séquence source.  Pour les requêtes qui utilisent l'opérateur Select indexé, PLINQ garantit que les résultats seront générés dans l'ordre croissant des index, mais n'offre aucune garantie sur la nature des index affectés aux résultats.  
  
## Voir aussi  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)   
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)