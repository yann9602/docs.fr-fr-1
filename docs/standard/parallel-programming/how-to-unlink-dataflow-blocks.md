---
title: "How to: Unlink Dataflow Blocks | Microsoft Docs"
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
  - "dataflow blocks, unlinking in TPL"
  - "Task Parallel Library, dataflows"
  - "TPL dataflow library, unlinking dataflow blocks"
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Unlink Dataflow Blocks
Ce document explique comment dissocier un bloc cible de flux de données de sa source.  
  
> [!TIP]
>  La bibliothèque de flux de données de TPL \(espace de noms<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> \) n'est pas distribuée avec [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choisissez **Gérer les packages NuGet** dans le menu Projet, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
## Exemple  
 L'exemple suivant crée trois objets <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, chacun d'entre eux appelle la méthode `TrySolution` pour calculer une valeur.  Cet exemple requiert seulement que le résultat du premier appel à `TrySolution` soit terminé.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Pour obtenir la valeur du premier objet <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> qui finit, cet exemple définit la méthode `ReceiveFromAny(T)`.  La méthode `ReceiveFromAny(T)` reçoit un tableau d'objets <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> et lie chacun de ces objets à un objet <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>.  Lorsque vous utilisez la méthode <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> pour lier un bloc de flux de données source à un bloc cible, la source envoie les messages à la cible lorsque des données sont disponible.  Étant donné que la classe <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> accepte uniquement le premier message offert, la méthode `ReceiveFromAny(T)` produit son résultat en appelant la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>.  Cela génère le premier message qui est proposé à l'objet <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>.  La méthode <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> a une version surchargée qui accepte un paramètre <xref:System.Boolean>, `unlinkAfterOne` qui, lorsqu'il est affecté à `True`, demande au bloc source de se dissocier de la cible une fois que la cible a reçu un message de la source.  Il est important pour l'objet <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> de se dissocier de ses sources car la relation entre le tableau de sources et l'objet <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> n'est plus requise après que l'objet <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> est reçu un message.  
  
 Pour permettre aux appels restants à `TrySolution` de se terminer après que l'un d'entre eux calcule une valeur, la méthode `TrySolution` prend un objet <xref:System.Threading.CancellationToken> qui est annulée après que l'appel à `ReceiveFromAny(T)` retourne.  La méthode <xref:System.Threading.SpinWait.SpinUntil%2A> retourne lorsque cet objet <xref:System.Threading.CancellationToken> est annulé.  
  
## Compilation du code  
 Copiez l'exemple de code et collez\-le dans un projet Visual Studio, ou collez\-le dans un fichier nommé `DataflowReceiveAny.cs`\(`DataflowReceiveAny.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\), exécutez ensuite la commande suivante dans une fenêtre d'invite de commandes Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**  
  
## Programmation fiable  
  
## Voir aussi  
 [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)