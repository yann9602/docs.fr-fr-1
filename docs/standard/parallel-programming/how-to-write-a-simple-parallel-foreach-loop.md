---
title: "Comment : écrire une boucle Parallel.ForEach simple"
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
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16d8cd3c3c01c2f9d83786e78f0eb1c45a38a49b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Comment : écrire une boucle Parallel.ForEach simple
Cet exemple montre comment utiliser un <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> boucle pour permettre le parallélisme des données sur n’importe quel <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> source de données.  
  
> [!NOTE]
>  Cette documentation utilise des expressions lambda pour définir les délégués en PLINQ. Si les expressions lambda en C# ou Visual Basic ne vous sont pas familières, consultez la page [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 A <xref:System.Threading.Tasks.Parallel.ForEach%2A> boucle fonctionne comme un <xref:System.Threading.Tasks.Parallel.For%2A> boucle. La collection source est partitionnée et le travail est planifié sur plusieurs threads en fonction de l’environnement du système. Plus de processeurs sur le système, plus la méthode parallèle s’exécute. Pour certaines collections source, une boucle séquentielle peut être plus rapide, selon la taille de la source et le type de travail en cours d’exécution. Pour plus d’informations sur les performances, consultez [pièges potentiels dans le parallélisme des tâches et les données](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)  
  
 Pour plus d’informations sur les boucles parallèles, consultez [Comment : écrire une boucle Parallel.For Simple](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).  
  
 Pour utiliser <xref:System.Threading.Tasks.Parallel.ForEach%2A> avec une collection non générique, vous pouvez utiliser la <xref:System.Linq.Enumerable.Cast%2A> méthode d’extension pour convertir la collection à une collection générique, comme indiqué dans l’exemple suivant :  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 Vous pouvez également utiliser Parallel LINQ (PLINQ) pour paralléliser le traitement de <xref:System.Collections.Generic.IEnumerable%601> des sources de données. PLINQ vous permet d’utiliser la syntaxe de requête déclarative pour exprimer le comportement de la boucle. Pour plus d’informations, consultez [PLINQ (Parallel LINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Copiez et collez ce code dans un [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] projet d’Application Console 2010.  
  
-   Ajoutez une référence à System.Drawing.dll  
  
-   Appuyez sur F5  
  
## <a name="see-also"></a>Voir aussi  
 [Parallélisme de données](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Programmation parallèle](../../../docs/standard/parallel-programming/index.md)  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
