---
title: "Comment : parcourir une arborescence binaire avec des tâches parallèles"
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
helpviewer_keywords: tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c029a763faaa0b4d6ea5612efe079e47415b6fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>Comment : parcourir une arborescence binaire avec des tâches parallèles
L’exemple suivant montre deux façons dans lequel les tâches parallèles peuvent être utilisées pour parcourir une arborescence de données. La création de l’arborescence elle-même est considérée comme un exercice.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 Les deux méthodes indiquées sont fonctionnellement équivalents. À l’aide de la <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> pour créer et exécuter des tâches, vous obtenez un descripteur des tâches peuvent être utilisés pour attendre les tâches et gérer des exceptions.  
  
## <a name="see-also"></a>Voir aussi  
 [La bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
