---
title: "How to: Write a Simple Parallel.ForEach Loop | Microsoft Docs"
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
  - "foreach, parallel version"
  - "parallel programming, foreach"
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# How to: Write a Simple Parallel.ForEach Loop
Cet exemple indique comment utiliser une boucle <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> pour permettre le parallélisme des données sur toute source de données <xref:System.Collections.IEnumerable?displayProperty=fullName> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>.  
  
> [!NOTE]
>  Cette documentation utilise des expressions lambda pour définir des délégués en PLINQ.  Si vous n'êtes pas familiarisé avec les expressions lambda en C\# ou Visual Basic, consultez [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## Exemple  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 Une boucle <xref:System.Threading.Tasks.Parallel.ForEach%2A> fonctionne comme une boucle <xref:System.Threading.Tasks.Parallel.For%2A>.  La collection source est partitionnée et le travail est planifié sur plusieurs threads en fonction de l'environnement système.  Plus les processeurs du système sont nombreux, plus l'exécution de la méthode parallèle est rapide.  Pour certaines collections source, une boucle séquentielle peut être plus rapide, en fonction de la taille de la source et du genre de travail exécuté.  Pour plus d'informations sur les performances, consultez [Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)  
  
 Pour plus d'informations sur les boucles parallèles, consultez [How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).  
  
 Pour utiliser <xref:System.Threading.Tasks.Parallel.ForEach%2A> avec une collection non générique, vous pouvez utiliser la méthode d'extension <xref:System.Linq.Enumerable.Cast%2A> pour convertir la collection en collection générique, comme l'illustre l'exemple suivant :  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 Vous pouvez également utiliser Parallel LINQ \(PLINQ\) pour paralléliser le traitement des sources de données <xref:System.Collections.Generic.IEnumerable%601>.  PLINQ vous permet d'utiliser la syntaxe de requête déclarative pour exprimer le comportement de la boucle.  Pour plus d'informations, consultez [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## Compilation du code  
  
-   Copiez et collez ce code dans un projet Application console 2010 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] et appuyez sur F5.  
  
-   Ajoutez une référence à System.Drawing.dll.  
  
-   Appuyez sur F5.  
  
## Voir aussi  
 [Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)   
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)