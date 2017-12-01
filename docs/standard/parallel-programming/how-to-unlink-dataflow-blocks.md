---
title: "Comment : dissocier des blocs de flux de données"
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
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41f1b83fab6ff44e69ac2f010f70e6e254341f5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-unlink-dataflow-blocks"></a>Comment : dissocier des blocs de flux de données
Ce document décrit comment dissocier un bloc de flux de données cible à partir de sa source.  
  
> [!TIP]
>  La bibliothèque de flux de données TPL (espace de noms <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType>) n'est pas distribuée avec le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], dans le menu Projet choisissez **Gérer les packages NuGet**, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée trois <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> d’objets, chacun des qui appelle le `TrySolution` méthode pour calculer une valeur. Cet exemple ne requiert que le résultat du premier appel à `TrySolution` à terminer.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Pour recevoir la valeur de la première <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objet qui se termine, cet exemple définit le `ReceiveFromAny(T)` (méthode). Le `ReceiveFromAny(T)` méthode accepte un tableau de <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objets ainsi que des liens de chacun de ces objets pour un <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objet. Lorsque vous utilisez la <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> méthode pour lier un bloc de flux de données source à un bloc cible, la source de propage les messages vers la cible de données deviennent disponibles. Étant donné que la <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> classe accepte uniquement le premier message Il est fourni, le `ReceiveFromAny(T)` méthode produit ses résultats en appelant le <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> (méthode). Cela génère le premier message qui est proposé à la <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objet. Le <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> méthode a une version surchargée qui accepte un <xref:System.Boolean> paramètre, `unlinkAfterOne` qui, lorsqu’il est défini `True`, fait en sorte que le bloc source pour supprimer la liaison de la cible une fois que la cible reçoit un message à partir de la source. Il est important pour le <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objet dissocier de ses sources, car la relation entre le tableau de sources et le <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objet n’est plus nécessaire après la <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objet reçoit un message.  
  
 Pour activer les appels restants à `TrySolution` à la fin une fois qu’un d’eux calcule une valeur, le `TrySolution` méthode prend un <xref:System.Threading.CancellationToken> objet qui est annulée après l’appel à `ReceiveFromAny(T)` renvoie. Le <xref:System.Threading.SpinWait.SpinUntil%2A> méthode retourne quand cela <xref:System.Threading.CancellationToken> objet est annulé.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**  
  
## <a name="robust-programming"></a>Programmation fiable  
  
## <a name="see-also"></a>Voir aussi  
 [Le flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
