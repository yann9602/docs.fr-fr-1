---
title: "Comment : empêcher une tâche enfant de s’attacher à son parent"
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
helpviewer_keywords: tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4717e3a077648d9db51fe39228209617b384bd0c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Comment : empêcher une tâche enfant de s’attacher à son parent
Ce document montre comment empêcher une tâche enfant de s’attacher à la tâche parente. Empêcher une tâche enfant de s’attacher à son parent est utile lorsque vous appelez un composant qui est écrit par un tiers, et qui utilise également des tâches. Par exemple, un composant tiers qui utilise le <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option pour créer un <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> objet peut provoquer des problèmes dans votre code si elle est longue ou lève une exception non gérée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant compare les effets de l’aide des options par défaut pour les effets d’empêcher une tâche enfant de s’attacher au parent. L’exemple crée un <xref:System.Threading.Tasks.Task> objet qui appelle une bibliothèque tierce qui utilise également un <xref:System.Threading.Tasks.Task> objet. La bibliothèque tierce utilise le <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option permettant de créer le <xref:System.Threading.Tasks.Task> objet. L’application utilise le <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option permettant de créer la tâche parente. Cette option indique à l’exécution pour supprimer la <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> spécification dans les tâches enfants.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Une tâche parente ne se termine pas tant que toutes les tâches enfants terminées, une tâche enfant à exécution longue peut entraîner l’application globale des performances médiocres. Dans cet exemple, lorsque l’application utilise les options par défaut pour créer une tâche parent, la tâche enfant doit se terminer avant la fin de la tâche parente. Lorsque l’application utilise la <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, l’enfant n’est pas attachée au parent. Par conséquent, l’application peut effectuer une tâche supplémentaire une fois la tâche parente et avant qu’il doit attendre la tâche enfant se termine.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `DenyChildAttach.cs` (`DenyChildAttach.vb` pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe DenyChildAttach.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe DenyChildAttach.vb**  
  
## <a name="robust-programming"></a>Programmation fiable  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation asynchrone basée sur les tâches](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
