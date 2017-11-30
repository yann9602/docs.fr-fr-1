---
title: Options de fusion en PLINQ
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
helpviewer_keywords: PLINQ queries, merge options
ms.assetid: e8f7be3b-88de-4f33-ab14-dc008e76c1ba
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e9bf586c1805fc5b5f1cc5f96f4e6b08d80c199a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="merge-options-in-plinq"></a>Options de fusion en PLINQ
Lorsqu’une requête s’exécute en parallèle, PLINQ partitionne la séquence source afin que plusieurs threads puissent fonctionner sur différentes parties simultanément, en général sur des threads distincts. Si les résultats doivent être consommés sur un thread, par exemple, dans un `foreach` (`For Each` dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) de boucle, puis les résultats de chaque thread doivent être fusionnés en une séquence. Le type de fusion que PLINQ exécute dépend des opérateurs présents dans la requête. Par exemple, les opérateurs qui imposent un nouvel ordre des résultats doivent mettre en mémoire tampon tous les éléments de tous les threads. Du point de vue du thread consommateur (qui est également celui de l’utilisateur de l’application), une requête entièrement mis en mémoire tampon peut s’exécuter pendant une certaine durée avant qu’il génère son premier résultat. Autres opérateurs, par défaut, sont partiellement mis en mémoire tampon ; ils produisent leurs résultats par lots. Un opérateur, <xref:System.Linq.ParallelEnumerable.ForAll%2A> n’est pas mis en mémoire tampon par défaut. Il transmet immédiatement tous les éléments de tous les threads.  
  
 À l’aide de la <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> (méthode), comme indiqué dans l’exemple suivant, vous pouvez fournir un indicateur à PLINQ indiquant quel genre de fusion exécuter.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Pour obtenir un exemple complet, consultez [Comment : spécifier les Options de fusion en PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md).  
  
 Si la requête ne peut pas prendre en charge l’option demandée, l’option sera simplement ignorée. Dans la plupart des cas, il est inutile de spécifier une option de fusion pour une requête PLINQ. Toutefois, dans certains cas vous trouver en testant et en mesure une requête s’exécute mieux dans un mode non définis par défaut. Une utilisation courante de cette option est pour forcer un opérateur de fusion de segment pour diffuser ses résultats afin de fournir une interface utilisateur plus réactive.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 Le <xref:System.Linq.ParallelMergeOptions> énumération inclut les options suivantes qui spécifient, pour les formes de requête prises en charge, la manière dont la sortie finale de la requête est transmise lorsque les résultats sont consommés sur un thread :  
  
-   `Not Buffered`  
  
     La <xref:System.Linq.ParallelMergeOptions.NotBuffered> option, chaque élément traité à retourner à partir de chaque thread dès qu’il est généré. Ce comportement est similaire à « streaming » de la sortie. Si le <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> opérateur n’est présent dans la requête, `NotBuffered` conserve l’ordre des éléments de la source. Bien que `NotBuffered` commence à transmettre les résultats dès qu’elles sont disponibles, la durée totale de la production de tous les résultats pourront toujours être supérieure à l’aide d’une des autres options de fusion.  
  
-   `Auto Buffered`  
  
     Le <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option entraîne la requête à regrouper des éléments dans une mémoire tampon, puis générer régulièrement le contenu de la mémoire tampon à la fois pour le thread consommateur. Cela est analogue à transmettre les données sources dans « blocs » au lieu d’utiliser le comportement « diffusion en continu » de `NotBuffered`. `AutoBuffered`peut prendre plus de `NotBuffered` à disposition le premier élément sur le thread consommateur. La taille de la mémoire tampon et le comportement de transmission exact ne sont pas configurable et peuvent varier en fonction de différents facteurs qui se rapportent à la requête.  
  
-   `FullyBuffered`  
  
     La <xref:System.Linq.ParallelMergeOptions.FullyBuffered> option, la sortie de la requête entière à être mis en mémoire tampon avant qu’un des éléments sont transmis. Lorsque vous utilisez cette option, il peut prendre plus de temps avant le premier élément est disponible sur le thread consommateur, mais les résultats complets peuvent être produits plus rapidement qu’avec les autres options.  
  
## <a name="query-operators-that-support-merge-options"></a>Opérateurs de requête qui prennent en charge les Options de fusion  
 Le tableau suivant répertorie les opérateurs qui prennent en charge tous les modes de l’option de fusion, soumis aux restrictions spécifiées.  
  
|Opérateur|Restrictions|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Aucune|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Aucune|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Requêtes non classées qui ont uniquement un tableau ou une liste source.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Aucune|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|Aucune|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Requêtes non classées qui ont uniquement un tableau ou une liste source.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Aucune|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Aucune|  
  
 Tous les autres opérateurs de requête PLINQ peuvent ignorer les options de fusion fournis par l’utilisateur. Certains opérateurs de requête, par exemple, <xref:System.Linq.ParallelEnumerable.Reverse%2A> et <xref:System.Linq.ParallelEnumerable.OrderBy%2A>, Impossible de générer des éléments jusqu'à ce que tous les produits et réorganisés. Par conséquent, lorsque <xref:System.Linq.ParallelMergeOptions> est utilisé dans une requête qui contient également un opérateur tel que <xref:System.Linq.ParallelEnumerable.Reverse%2A>, le comportement de fusion n’est pas appliqué dans la requête jusqu'à ce que cet opérateur a produit ses résultats.  
  
 La capacité de certains opérateurs à gérer les options de fusion varie selon le type de la séquence source et si le <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> opérateur a été utilisé précédemment dans la requête. <xref:System.Linq.ParallelEnumerable.ForAll%2A>est toujours <xref:System.Linq.ParallelMergeOptions.NotBuffered> ; il transmet immédiatement ses éléments. <xref:System.Linq.ParallelEnumerable.OrderBy%2A>est toujours <xref:System.Linq.ParallelMergeOptions.FullyBuffered>; il doit trier l’intégralité de la liste avant la transmission.  
  
## <a name="see-also"></a>Voir aussi  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Comment : spécifier des options de fusion en PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
