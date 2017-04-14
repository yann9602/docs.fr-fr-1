---
title: "How to: Handle Exceptions in a PLINQ Query | Microsoft Docs"
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
  - "PLINQ queries, how to handle exceptions"
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# How to: Handle Exceptions in a PLINQ Query
Le premier exemple de cette rubrique indique comment gérer la <xref:System.AggregateException?displayProperty=fullName> qui peut être levée par une requête PLINQ lors de son exécution.  Le deuxième exemple montre comment mettre les blocs try\-catch dans des délégués, aussi près que possible de l'endroit où l'exception sera levée.  De cette façon, vous pouvez les intercepter rapidement voire continuer l'exécution de la requête.  Lorsque les exceptions sont autorisées à se propager vers le thread joint, il est possible qu'une requête puisse continuer à traiter des éléments après que l'exception a été levée.  
  
 Dans certains cas, lorsque PLINQ revient à l'exécution séquentielle et qu'une exception se produit, l'exception peut être propagée directement et non incluse un wrapper dans une <xref:System.AggregateException>.  De même, les <xref:System.Threading.ThreadAbortException> sont toujours propagées directement.  
  
> [!NOTE]
>  Lorsque l'option "Uniquement mon code" est activée, Visual Studio s'arrête sur la ligne qui lève l'exception et affiche un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur. Cette erreur est bénigne.  Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions illustré dans les exemples ci\-dessous.  Pour empêcher Visual Studio de s'arrêter sur la première erreur, il vous suffit de désactiver la case à cocher "Uniquement mon code" sous **Outils, Options, Débogage, Général**.  
>   
>  Cet exemple est destiné à montrer l'utilisation et peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.  Pour plus d'informations sur l'accélération, consultez [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## Exemple  
 Cet exemple montre comment mettre les blocs try\-catch autour du code qui exécute la requête pour intercepter toute <xref:System.AggregateException?displayProperty=fullName> levée.  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 Dans cet exemple, la requête ne peut pas continuer après la levée de l'exception.  Au moment où votre code d'application intercepte l'exception, PLINQ a déjà arrêté la requête sur tous les threads.  
  
## Exemple  
 L'exemple suivant indique comment mettre un bloc try\-catch dans un délégué pour permettre d'intercepter une exception et de continuer l'exécution de la requête.  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## Compilation du code  
  
-   Pour compiler et exécuter ces exemples, copiez\-les dans l'exemple de données PLINQ et appelez la méthode Main.  
  
## Programmation fiable  
 N'interceptez pas d'exception à moins de savoir comment la gérer pour ne pas endommager l'état de votre programme.  
  
## Voir aussi  
 <xref:System.Linq.ParallelEnumerable>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)