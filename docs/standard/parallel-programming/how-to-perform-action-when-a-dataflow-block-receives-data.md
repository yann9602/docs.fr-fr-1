---
title: "Comment : exécuter des actions lorsqu'un bloc de flux de données reçoit des données"
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
- Task Parallel Library, dataflows
- TPL dataflow library, receiving data
ms.assetid: fc2585dc-965e-4632-ace7-73dd02684ed3
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d049d20f5e685096a72857cd18a89688633883c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Comment : exécuter des actions lorsqu'un bloc de flux de données reçoit des données
Les types de *Bloc de flux de données d’exécution* appellent un délégué fourni par l’utilisateur lorsqu’ils reçoivent des données. Les classes <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, et <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> sont des types de bloc de flux de données d'exécution. Vous pouvez utiliser le mot clé `delegate` (`Sub` dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), <xref:System.Action%601>, <xref:System.Func%602>, ou une expression lambda lorsque vous fournissez une fonction de travail dans un bloc de flux de données d'exécution. Ce document explique comment utiliser <xref:System.Func%602> et les expressions lambda pour effectuer l'action dans des blocs d'exécution.  
  
> [!TIP]
>  La bibliothèque de flux de données TPL (espace de noms <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType>) n'est pas distribuée avec le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], dans le menu Projet choisissez **Gérer les packages NuGet**, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise le flux de données pour lire un fichier de disque et calcule le nombre d'octets qui sont égaux à zéro dans ce fichier. Il utilise <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> pour lire le fichier et calculer le nombre d'octets nuls, et <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> pour imprimer le nombre d'octets nuls sur la console. L'objet <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> spécifie un objet <xref:System.Func%602> pour effectuer le travail lorsque les blocs reçoivent les données. L'objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> utilise une expression lambda pour afficher sur la console le nombre d'octets nuls qui sont lus.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 Bien que vous puissiez spécifier une expression lambda à un objet <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, cet exemple utilise <xref:System.Func%602> pour permettre à l'autre code d'utiliser la méthode `CountBytes`. L'objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> utilise une expression lambda car le travail à effectuer est spécifique à cette tâche et n'est pas susceptible d'être utile depuis un autre code. Pour plus d’informations sur la façon dont les expressions lambda fonctionnent dans la bibliothèque de tâches en parallèle, consultez [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 La section Résumé des Types de délégué dans le [flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document résume les types délégués que vous pouvez fournir aux <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, et <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objets. La table indique également si le type délégué fonctionne de façon synchrone ou asynchrone.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `DataflowExecutionBlocks.cs` (`DataflowExecutionBlocks.vb` pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.vb**  
  
## <a name="robust-programming"></a>Programmation fiable  
 Cet exemple fournit un délégué de type <xref:System.Func%602> à l'objet <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> pour effectuer la tâche du bloc de flux de données de façon synchrone. Pour permettre au bloc de flux de données de se comporter de façon asynchrone, fournissez un délégué de type <xref:System.Func%601> au bloc de flux de données. Lorsqu'un bloc de flux de données se comporte de façon asynchrone, la tâche du bloc de flux de données se termine uniquement lorsque l'objet <xref:System.Threading.Tasks.Task%601> retourné s'achève. L’exemple suivant modifie la méthode `CountBytes` et utilise les opérateurs [async](~/docs/csharp/language-reference/keywords/async.md) et [await](~/docs/csharp/language-reference/keywords/await.md) ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) et [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) pour calculer de façon asynchrone le nombre total d’octets qui sont nuls dans le fichier fourni. La méthode <xref:System.IO.FileStream.ReadAsync%2A> effectue de façon asynchrone des opérations de lecture de fichiers.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Utilisez également des expressions lambda asynchrones pour effectuer une action dans un bloc de flux de données d’exécution. L'exemple suivant modifie l'objet <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> utilisé dans l'exemple précédent pour qu'il utilise une expression lambda pour effectuer de manière asynchrone le travail.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Voir aussi  
 [Le flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
