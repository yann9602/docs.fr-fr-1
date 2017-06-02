---
title: "Merge Options in PLINQ | Microsoft Docs"
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
  - "PLINQ queries, merge options"
ms.assetid: e8f7be3b-88de-4f33-ab14-dc008e76c1ba
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Merge Options in PLINQ
Lorsqu'une requête s'exécute en parallèle, PLINQ partitionne la séquence source pour que plusieurs threads puissent fonctionner simultanément sur différentes parties, généralement des threads.  Si les résultats doivent être consommés sur un thread, par exemple, dans une boucle `foreach` \(`For Each` en [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\), les résultats de chaque thread doivent être fusionnés en une séquence.  Le genre de fusion que PLINQ exécute dépend des opérateurs présents dans la requête.  Par exemple, les opérateurs qui imposent un nouvel ordre des résultats doivent mettre en mémoire tampon tous les éléments des threads.  Du point de vue du thread consommateur \(qui est également celui de l'utilisateur de l'application\), une requête complètement mise en mémoire tampon peut s'exécuter pendant une certaine durée avant de produire son premier résultat.  Par défaut, d'autres opérateurs, sont partiellement mis en mémoire tampon et transmettent leurs résultats par lots.  Un opérateur, <xref:System.Linq.ParallelEnumerable.ForAll%2A> n'est pas mis en mémoire tampon par défaut.  Il transmet immédiatement tous les éléments de tous les threads.  
  
 En utilisant la méthode <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>, comme indiqué dans l'exemple suivant, vous pouvez ajouter un commentaire à PLINQ indiquant quel genre de fusion exécuter.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Pour obtenir un exemple complet, consultez [How to: Specify Merge Options in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md).  
  
 Si la requête en question ne peut pas prendre en charge l'option demandée, l'option sera ignorée.  Dans la plupart des cas, vous ne devez pas spécifier une option de fusion pour une requête PLINQ.  Toutefois, vous pouvez, dans certains cas, après avoir effectuer des tests et des mesures, vous rendre compte qu'une requête s'exécute le mieux dans un mode autre que celui par défaut.  Une utilisation courante de cette option est de forcer un opérateur de fusion de segment à transmettre en continu ses résultats pour une interface utilisateur plus réactive.  
  
## ParallelMergeOptions  
 L'énumération <xref:System.Linq.ParallelMergeOptions> inclut les options suivantes qui spécifient, pour les formes de requête prises en charge, la manière dont la dernière sortie de la requête est transmise lorsque les résultats sont consommés sur un thread :  
  
-   `Not Buffered`  
  
     Avec l'option <xref:System.Linq.ParallelMergeOptions>, chaque élément traité est retourné par chaque thread dès sa production.  Ce comportement est analogue à la « transmission en continu » de la sortie.  Si l'opérateur <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> est présent dans la requête, `NotBuffered` conserve l'ordre des éléments source.  Même si `NotBuffered` commence à transmettre les résultats à mesure qu'ils sont disponibles, la durée totale de production de tous les résultats peut être plus longue qu'avec l'une des autres options de fusion.  
  
-   `Auto Buffered`  
  
     Avec l'option <xref:System.Linq.ParallelMergeOptions> la requête collecte les éléments dans une mémoire tampon puis transmet régulièrement tout le contenu de la mémoire tampon en même temps au thread consommateur.  Ceci est analogue à transmettre les données sources sous forme de « segments » au lieu d'utiliser le comportement de « transmission continue » de `NotBuffered`.  `AutoBuffered` peut prendre plus longtemps que `NotBuffered` pour rendre disponible le premier élément sur le thread consommateur.  La taille de la mémoire tampon et le comportement de transmission exact ne sont pas configurables et peuvent varier en fonction des facteurs associés à la requête.  
  
-   `FullyBuffered`  
  
     Avec l'option <xref:System.Linq.ParallelMergeOptions>, la sortie de la requête entière est mise en mémoire tampon avant la transmission des éléments.  Avec cette option, le premier élément peut prendre plus longtemps à devenir disponible sur le thread consommateur, mais les résultats complets peuvent être produits plus rapidement qu'avec les autres options.  
  
## Opérateurs de requête prenant en charge les options de fusion  
 Le tableau suivant répertorie les opérateurs qui prennent en charge tous les modes d'options de fusion, sujets aux restrictions spécifiées.  
  
|Opérateur|Restrictions|  
|---------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Requêtes non classées avec uniquement un tableau ou une liste source.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Requêtes non classées avec uniquement un tableau ou une liste source.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|None|  
  
 Tous les autres opérateurs de requête PLINQ peuvent ignorer les options de fusion fournies par l'utilisateur.  Certains opérateurs de requête, tels que <xref:System.Linq.ParallelEnumerable.Reverse%2A> et <xref:System.Linq.ParallelEnumerable.OrderBy%2A>, ne peuvent pas transmettre d'éléments tant qu'ils n'ont pas tous été produits et réorganisés.  Par conséquent, lorsque <xref:System.Linq.ParallelMergeOptions> est utilisé dans une requête qui contient également un opérateur tel que <xref:System.Linq.ParallelEnumerable.Reverse%2A>, le comportement de fusion ne sera pas appliqué à la requête tant que l'opérateur n'a pas produit ses résultats.  
  
 La capacité de certains opérateurs à gérer des options de fusion dépend du type de la séquence source et de si l'opérateur <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> a été utilisé précédemment dans la requête.  <xref:System.Linq.ParallelEnumerable.ForAll%2A> est toujours <xref:System.Linq.ParallelMergeOptions> ; il transmet immédiatement ses éléments.  <xref:System.Linq.ParallelEnumerable.OrderBy%2A> est toujours <xref:System.Linq.ParallelMergeOptions> ; il doit trier toute la liste avant la transmission.  
  
## Voir aussi  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)   
 [How to: Specify Merge Options in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)