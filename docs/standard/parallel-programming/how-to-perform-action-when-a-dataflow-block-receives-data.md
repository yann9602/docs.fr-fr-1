---
title: "How to: Perform Action When a Dataflow Block Receives Data | Microsoft Docs"
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
  - "Task Parallel Library, dataflows"
  - "TPL dataflow library, receiving data"
ms.assetid: fc2585dc-965e-4632-ace7-73dd02684ed3
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Perform Action When a Dataflow Block Receives Data
Les types*de bloc de données de flux d'exécution* appellent un délégué fourni par utilisateur lorsqu'ils reçoivent des données.  Les classes <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=fullName>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=fullName>, et <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=fullName> sont des types de bloc de flux de données d'exécution.  Vous pouvez utiliser le mot clé `delegate` \(`Sub` dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\), <xref:System.Action%601>, <xref:System.Func%602>, ou une expression lambda lorsque vous fournissez une fonction de travail dans un bloc de flux de données d'exécution.  Ce document explique comment utiliser <xref:System.Func%602> et les expressions lambda pour effectuer l'action dans des blocs d'exécution.  
  
> [!TIP]
>  La bibliothèque de flux de données de TPL \(espace de noms<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> \) n'est pas distribuée avec [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choisissez **Gérer les packages NuGet** dans le menu Projet, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
## Exemple  
 L'exemple suivant utilise le flux de données pour lire un fichier de disque et calcule le nombre d'octets dans le fichier qui sont égals à zéro.  Il utilise <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> pour lire le fichier et calculer le nombre d'octets zéro, et <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> pour afficher le nombre d'octets zéro sur la console.  L'objet <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> spécifie un objet <xref:System.Func%602> pour effectuer le travail lorsque les blocs acceptent des données.  L'objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> utilise une expression lambda pour afficher sur la console le nombre d'octets zéro qui sont lus.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 Bien que vous puissiez spécifier une expression lambda à un objet <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, cet exemple utilise <xref:System.Func%602> pour permettre à l'autre code d'utiliser la méthode `CountBytes`.  L'objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> utilise une expression lambda car le travail à effectuer est spécifique à cette tâche et ne peut pas être utile à l'autre code.  Pour plus d'informations sur la façon dont les expressions lambda fonctionnent dans la bibliothèque de tâches en parallèle, consultez [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Le résumé de la section des types délégués dans le document [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) récapitule les types délégués que vous pouvez fournir aux objets <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, et <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>.  La table indique également si le type délégué fonctionne de façon synchrone ou asynchrone.  
  
## Compilation du code  
 Copiez l'exemple de code et collez\-le dans un projet Visual Studio, ou collez\-le dans un fichier nommé `DataflowExecutionBlocks.cs`\(`DataflowExecutionBlocks.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\), exécutez ensuite la commande suivante dans une fenêtre d'invite de commandes Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.vb**  
  
## Programmation fiable  
 Cet exemple fournit un délégué de type <xref:System.Func%602> à l'objet <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> pour effectuer la tâche du bloc de flux de données de façon synchrone.  Pour permettre au bloc de flux de données de se comporter de façon asynchrone, fournissez un délégué de type <xref:System.Func%601> au bloc de flux de données.  Lorsqu'un bloc de flux de données se comporte de façon asynchrone, la tâche du bloc de flux de données est terminée uniquement lorsque l'objet <xref:System.Threading.Tasks.Task%601> retourné se termine.  L'exemple suivant modifie la méthode `CountBytes` et utilise les opérateurs [async](../Topic/async%20\(C%23%20Reference\).md) et [attendez](../Topic/await%20\(C%23%20Reference\).md) \([Async](../Topic/Async%20\(Visual%20Basic\).md) et [Attendez](../Topic/Await%20Operator%20\(Visual%20Basic\).md) dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\) pour calculer de façon asynchrone le nombre total d'octets qui sont à zéro dans le fichier spécifié.  La méthode <xref:System.IO.FileStream.ReadAsync%2A> effectue de façon asynchrone des opérations de lecture de fichier .  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Utilisez également des expressions lambda asynchrones pour effectuer une action dans un bloc de flux de données d'exécution.  L'exemple suivant modifie l'objet <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> utilisé dans l'exemple précédent pour qu'il utilise une expression lambda pour effectuer de manière asynchrone le travail.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## Voir aussi  
 [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)