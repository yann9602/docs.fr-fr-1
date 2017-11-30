---
title: "Comment : exposer des modèles EAP à l’aide d’une tâche"
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
helpviewer_keywords: tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ae9d90c9bb3d0e8d315cbef510cdfe1b54e66da4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a>Comment : exposer des modèles EAP à l’aide d’une tâche
L’exemple suivant montre comment exposer une séquence arbitraire d’opérations de modèle asynchrone basé sur des événements (EAP) comme une seule tâche à l’aide un <xref:System.Threading.Tasks.TaskCompletionSource%601>. L’exemple montre également comment utiliser un <xref:System.Threading.CancellationToken> à appeler les méthodes d’annulation intégrées sur le <xref:System.Net.WebClient> objets.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque parallèle de tâches (TPL) et programmation asynchrone .NET Framework](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
