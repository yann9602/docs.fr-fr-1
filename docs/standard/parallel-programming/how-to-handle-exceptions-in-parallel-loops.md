---
title: "How to: Handle Exceptions in Parallel Loops | Microsoft Docs"
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
  - "parallel loops, how to handle exceptions"
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# How to: Handle Exceptions in Parallel Loops
Les surcharges <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> ne possèdent pas de mécanisme permettant de gérer les exceptions.  En cela, elles sont similaires aux boucles `for` et `foreach` \(`For` et `For Each` en Visual Basic\). Une exception non gérée provoque l'arrêt immédiat de la boucle.  
  
 Quand vous ajoutez votre propre logique de gestion des exceptions à des boucles parallèles, gérez le cas dans lequel de telles exceptions peuvent être levées simultanément sur plusieurs threads et le cas dans lequel une exception levée sur un thread provoque la levée d'une autre exception sur un autre thread.  Vous pouvez gérer les deux cas en encapsulant toutes les exceptions de la boucle dans un <xref:System.AggregateException?displayProperty=fullName>.  L'exemple suivant montre une méthode possible.  
  
> [!NOTE]
>  Quand l'option Uniquement mon code est activée, Visual Studio, dans certains cas, peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur. Cette erreur est sans gravité.  Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans l'exemple ci\-dessous.  Pour empêcher Visual Studio de s'arrêter sur la première erreur, il suffit de désactiver la case à cocher Uniquement mon code sous **Outils, Options, Débogage, Général**.  
  
## Exemple  
 Dans cet exemple, toutes les exceptions sont interceptées, puis encapsulées dans une <xref:System.AggregateException?displayProperty=fullName> qui est ensuite levée.  L'appelant peut décider des exceptions à gérer.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## Voir aussi  
 [Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)   
 [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)