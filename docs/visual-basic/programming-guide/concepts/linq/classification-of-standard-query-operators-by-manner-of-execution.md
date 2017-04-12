---
title: "Classification des opérateurs de requête Standard en mode d’exécution (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 7f55b0be-9f6e-44f8-865c-6afbea50cc54
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a13f2fcf33c2faacd5b2662cd96d0f962b54322f
ms.lasthandoff: 03/13/2017

---
# <a name="classification-of-standard-query-operators-by-manner-of-execution-visual-basic"></a>Classification des opérateurs de requête Standard en mode d’exécution (Visual Basic)
Mises en œuvre des objets des méthodes d’opérateur de requête standard LINQ s’exécutent dans une de deux manières principales : immédiate ou différée. Les opérateurs de requête qui utilisent l’exécution différée peuvent être divisés en deux catégories : diffusion en continu et non diffusion. Si vous savez comment exécutent les opérateurs de requête différents, il peut vous aider à comprendre les résultats que vous obtenez à partir d’une requête donnée. Cela est particulièrement vrai si la source de données change ou si vous générez une requête sur une autre requête. Cette rubrique classe les opérateurs de requête standard en fonction de leur mode d’exécution.  
  
## <a name="manners-of-execution"></a>Modes d’exécution  
  
### <a name="immediate"></a>Immédiat  
 L’exécution immédiate signifie que la source de données est en lecture et l’opération est effectuée au point dans le code où la requête est déclarée. Tous les opérateurs de requête standard qui retournent un résultat unique et non énumérable s’exécutent immédiatement.  
  
### <a name="deferred"></a>Différé  
 L’exécution différée signifie que l’opération n’est pas effectuée au point dans le code où la requête est déclarée. L’opération est effectuée uniquement lorsque la variable de requête est énumérée, par exemple en utilisant un `For Each` instruction. Cela signifie que les résultats de l’exécution de la requête dépendant de la source de données lorsque la requête est exécutée plutôt que lorsque la requête est définie. Si la variable de requête est énumérée plusieurs fois, les résultats peuvent différer chaque fois. Presque tous les opérateurs de requête standard dont le type de retour est <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Linq.IOrderedEnumerable%601>s’exécutent de manière différée.</xref:System.Linq.IOrderedEnumerable%601> </xref:System.Collections.Generic.IEnumerable%601>  
  
 Opérateurs de requête qui utilisent l’exécution différée peuvent en outre être classés comme la diffusion en continu ou diffusion non.  
  
#### <a name="streaming"></a>Diffusion en continu  
 Opérateurs diffusant en continu est inutile lire toutes les données sources avant d’obtenir des éléments. Au moment de l’exécution, un opérateur de diffusion en continu effectue son opération sur chaque élément source car elle est en lecture et génère l’élément si nécessaire. Un opérateur continue à lire des éléments source jusqu'à ce qu’un élément de résultat peut être généré. Cela signifie que plusieurs éléments source peuvent être lus pour produire un élément de résultat.  
  
#### <a name="non-streaming"></a>Non diffusion  
 Opérateurs de non diffusion doivent lire toutes les données sources avant qu’ils puissent obtenir un élément de résultat. Opérations de tri ou de regroupement appartiennent à cette catégorie. Au moment de l’exécution, opérateurs de requête non continue lire toutes les données source, placent dans une structure de données, effectuer l’opération et génèrent les éléments de résultat.  
  
## <a name="classification-table"></a>Tableau de classification  
 Le tableau suivant classe chaque méthode d’opérateur de requête standard en fonction de son mode d’exécution.  
  
> [!NOTE]
>  Si un opérateur est marqué dans deux colonnes, deux séquences d’entrée sont impliquées dans l’opération, et chaque séquence est évaluée différemment. Dans ces cas, il est toujours la première séquence dans la liste de paramètres est évaluée en différé, mode de diffusion en continu.  
  
|Opérateur de requête standard|Type de retour|Exécution immédiate|Exécution en continu différée|Exécution Non continue différée|  
|-----------------------------|-----------------|-------------------------|----------------------------------|---------------------------------------|  
|<xref:System.Linq.Enumerable.Aggregate%2A></xref:System.Linq.Enumerable.Aggregate%2A>|TSource|x|||  
|<xref:System.Linq.Enumerable.All%2A></xref:System.Linq.Enumerable.All%2A>|<xref:System.Boolean></xref:System.Boolean>|x|||  
|<xref:System.Linq.Enumerable.Any%2A></xref:System.Linq.Enumerable.Any%2A>|<xref:System.Boolean></xref:System.Boolean>|x|||  
|<xref:System.Linq.Enumerable.AsEnumerable%2A></xref:System.Linq.Enumerable.AsEnumerable%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
|<xref:System.Linq.Enumerable.Average%2A></xref:System.Linq.Enumerable.Average%2A>|Valeur numérique unique|x|||  
|<xref:System.Linq.Enumerable.Cast%2A></xref:System.Linq.Enumerable.Cast%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
|<xref:System.Linq.Enumerable.Concat%2A></xref:System.Linq.Enumerable.Concat%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
|<xref:System.Linq.Enumerable.Contains%2A></xref:System.Linq.Enumerable.Contains%2A>|<xref:System.Boolean></xref:System.Boolean>|x|||  
|<xref:System.Linq.Enumerable.Count%2A></xref:System.Linq.Enumerable.Count%2A>|<xref:System.Int32></xref:System.Int32>|x|||  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A></xref:System.Linq.Enumerable.DefaultIfEmpty%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
|<xref:System.Linq.Enumerable.Distinct%2A></xref:System.Linq.Enumerable.Distinct%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
|<xref:System.Linq.Enumerable.ElementAt%2A></xref:System.Linq.Enumerable.ElementAt%2A>|TSource|x|||  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A></xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|TSource|x|||  
|<xref:System.Linq.Enumerable.Empty%2A></xref:System.Linq.Enumerable.Empty%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>|x|||  
|<xref:System.Linq.Enumerable.Except%2A></xref:System.Linq.Enumerable.Except%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x|x|  
|<xref:System.Linq.Enumerable.First%2A></xref:System.Linq.Enumerable.First%2A>|TSource|x|||  
|<xref:System.Linq.Enumerable.FirstOrDefault%2A></xref:System.Linq.Enumerable.FirstOrDefault%2A>|TSource|x|||  
|<xref:System.Linq.Enumerable.GroupBy%2A></xref:System.Linq.Enumerable.GroupBy%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>|||x|  
|<xref:System.Linq.Enumerable.GroupJoin%2A></xref:System.Linq.Enumerable.GroupJoin%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x|x|  
<xref:System.Linq.Enumerable.Intersect%2A></xref:System.Linq.Enumerable.Intersect%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x|x|  
|<xref:System.Linq.Enumerable.Join%2A></xref:System.Linq.Enumerable.Join%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x|x|  
|<xref:System.Linq.Enumerable.Last%2A></xref:System.Linq.Enumerable.Last%2A>|TSource|x|||  
|<xref:System.Linq.Enumerable.LastOrDefault%2A></xref:System.Linq.Enumerable.LastOrDefault%2A>|TSource|x|||  
|<xref:System.Linq.Enumerable.LongCount%2A></xref:System.Linq.Enumerable.LongCount%2A>|<xref:System.Int64></xref:System.Int64>|x|||  
|<xref:System.Linq.Enumerable.Max%2A></xref:System.Linq.Enumerable.Max%2A>|Valeur numérique unique, TSource ou TResult|x|||  
|<xref:System.Linq.Enumerable.Min%2A></xref:System.Linq.Enumerable.Min%2A>|Valeur numérique unique, TSource ou TResult|x|||  
|<xref:System.Linq.Enumerable.OfType%2A></xref:System.Linq.Enumerable.OfType%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
|<xref:System.Linq.Enumerable.OrderBy%2A></xref:System.Linq.Enumerable.OrderBy%2A>|<xref:System.Linq.IOrderedEnumerable%601></xref:System.Linq.IOrderedEnumerable%601>|||x|  
|<xref:System.Linq.Enumerable.OrderByDescending%2A></xref:System.Linq.Enumerable.OrderByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601></xref:System.Linq.IOrderedEnumerable%601>|||x|  
|<xref:System.Linq.Enumerable.Range%2A></xref:System.Linq.Enumerable.Range%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
|<xref:System.Linq.Enumerable.Repeat%2A></xref:System.Linq.Enumerable.Repeat%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
|<xref:System.Linq.Enumerable.Reverse%2A></xref:System.Linq.Enumerable.Reverse%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>|||x|  
|<xref:System.Linq.Enumerable.Select%2A></xref:System.Linq.Enumerable.Select%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
|<xref:System.Linq.Enumerable.SelectMany%2A></xref:System.Linq.Enumerable.SelectMany%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
|<xref:System.Linq.Enumerable.SequenceEqual%2A></xref:System.Linq.Enumerable.SequenceEqual%2A>|<xref:System.Boolean></xref:System.Boolean>|x|||  
|<xref:System.Linq.Enumerable.Single%2A></xref:System.Linq.Enumerable.Single%2A>|TSource|x|||  
|<xref:System.Linq.Enumerable.SingleOrDefault%2A></xref:System.Linq.Enumerable.SingleOrDefault%2A>|TSource|x|||  
|<xref:System.Linq.Enumerable.Skip%2A></xref:System.Linq.Enumerable.Skip%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
|<xref:System.Linq.Enumerable.SkipWhile%2A></xref:System.Linq.Enumerable.SkipWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
|<xref:System.Linq.Enumerable.Sum%2A></xref:System.Linq.Enumerable.Sum%2A>|Valeur numérique unique|x|||  
|<xref:System.Linq.Enumerable.Take%2A></xref:System.Linq.Enumerable.Take%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
<xref:System.Linq.Enumerable.TakeWhile%2A></xref:System.Linq.Enumerable.TakeWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
|<xref:System.Linq.Enumerable.ThenBy%2A></xref:System.Linq.Enumerable.ThenBy%2A>|<xref:System.Linq.IOrderedEnumerable%601></xref:System.Linq.IOrderedEnumerable%601>|||x|  
|<xref:System.Linq.Enumerable.ThenByDescending%2A></xref:System.Linq.Enumerable.ThenByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601></xref:System.Linq.IOrderedEnumerable%601>|||x|  
|<xref:System.Linq.Enumerable.ToArray%2A></xref:System.Linq.Enumerable.ToArray%2A>|Tableau TSource|x|||  
|<xref:System.Linq.Enumerable.ToDictionary%2A></xref:System.Linq.Enumerable.ToDictionary%2A>|<xref:System.Collections.Generic.Dictionary%602></xref:System.Collections.Generic.Dictionary%602>|x|||  
|<xref:System.Linq.Enumerable.ToList%2A></xref:System.Linq.Enumerable.ToList%2A>|<xref:System.Collections.Generic.IList%601></xref:System.Collections.Generic.IList%601>|x|||  
|<xref:System.Linq.Enumerable.ToLookup%2A></xref:System.Linq.Enumerable.ToLookup%2A>|<xref:System.Linq.ILookup%602></xref:System.Linq.ILookup%602>|x|||  
|<xref:System.Linq.Enumerable.Union%2A></xref:System.Linq.Enumerable.Union%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
|<xref:System.Linq.Enumerable.Where%2A></xref:System.Linq.Enumerable.Where%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||x||  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq.Enumerable></xref:System.Linq.Enumerable>   
 [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Syntaxe d’Expression de requête pour les opérateurs de requête Standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)   
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
