---
title: "How to: Cancel a PLINQ Query | Microsoft Docs"
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
  - "PLINQ queries, how to cancel"
  - "cancellation, PLINQ"
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# How to: Cancel a PLINQ Query
Les exemples suivants montrent deux façons d'annuler une requête PLINQ.  Le premier exemple indique comment annuler une requête qui se compose principalement d'un parcours de données.  Le deuxième exemple indique comment annuler une requête qui contient une fonction de l'utilisateur sollicitant fortement les ressources informatiques.  
  
> [!NOTE]
>  Lorsque l'option "Uniquement mon code" est activée, Visual Studio s'arrête sur la ligne qui lève l'exception et affiche un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur. Cette erreur est bénigne.  Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions illustré dans les exemples ci\-dessous.  Pour empêcher Visual Studio de s'arrêter sur la première erreur, il vous suffit de désactiver la case à cocher "Uniquement mon code" sous **Outils, Options, Débogage, Général**.  
>   
>  Cet exemple est destiné à montrer l'utilisation et peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.  Pour plus d'informations sur l'accélération, consultez [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## Exemple  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 L'infrastructure PLINQ ne restaure pas une <xref:System.OperationCanceledException> unique en une <xref:System.AggregateException?displayProperty=fullName> ; <xref:System.OperationCanceledException> doit être gérée dans un bloc catch séparé.  Si un ou plusieurs délégués utilisateurs lèvent un OperationCanceledException\(externalCT\) \(en utilisant un <xref:System.Threading.CancellationToken?displayProperty=fullName> externe\) et aucune autre exception, et que la requête a été définie en tant que `AsParallel().WithCancellation(externalCT)`, PLINQ émettra une <xref:System.OperationCanceledException> unique \(externalCT\) plutôt qu'une <xref:System.AggregateException?displayProperty=fullName>.  Toutefois, si un délégué utilisateur lève un <xref:System.OperationCanceledException> et un autre délégué lève un autre type d'exception, les deux exceptions seront restaurées en <xref:System.AggregateException>.  
  
 La recommandation générale sur l'annulation est la suivante :  
  
1.  Si vous exécutez une annulation de délégué utilisateur, vous devez informer PLINQ du <xref:System.Threading.CancellationToken> externe et lever une <xref:System.OperationCanceledException>\(externalCT\).  
  
2.  Si l'annulation se produit et qu'aucune autre exception n'est levée, puis, vous devez gérer une <xref:System.OperationCanceledException> plutôt qu'une <xref:System.AggregateException>.  
  
## Exemple  
 L'exemple suivant indique comment gérer une annulation lorsqu'une fonction du code utilisateur sollicite fortement les ressources informatiques.  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 Lorsque vous gérez une annulation dans du code utilisateur, vous n'avez pas à utiliser <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> dans la définition de la requête.  Toutefois, ceci est recommandé car <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> n'a aucun effet sur les performances des requêtes et permet la gestion de l'annulation par les opérateurs de requête et votre code utilisateur.  
  
 Pour vérifier la réactivité du système, il est recommandé de vérifier les annulations toutes les millisecondes ; toutefois, toute durée inférieure ou égale à 10 millisecondes est considérée comme acceptable.  Cette fréquence ne doit pas avoir d'impact négatif sur les performances de votre code.  
  
 Lorsqu'un énumérateur est supprimé, par exemple lorsque le code quitte une boucle foreach \(For Each en Visual Basic\) qui itère au sein de résultats de requête, la requête est annulée, mais aucune exception n'est levée.  
  
## Voir aussi  
 <xref:System.Linq.ParallelEnumerable>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)   
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)