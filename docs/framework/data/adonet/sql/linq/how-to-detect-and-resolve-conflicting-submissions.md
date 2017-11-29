---
title: "Comment : détecter et résoudre des soumissions en conflit"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8eb2e27ab034d464ba6978d9ddc063e623812619
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>Comment : détecter et résoudre des soumissions en conflit
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournit de nombreuses ressources pour détecter et résoudre des conflits issus de modifications effectuées par plusieurs utilisateurs dans la base de données. Pour plus d’informations, consultez [Comment : gérer les conflits de modifications](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un `try` / `catch` bloc qui intercepte un <xref:System.Data.Linq.ChangeConflictException> exception. La fenêtre de console affiche des informations sur les entités et les membres de chaque conflit.  
  
> [!NOTE]
>  Vous devez inclure la directive `using System.Reflection` (`Imports System.Reflection` dans Visual Basic) pour prendre en charge la récupération d'informations. Pour plus d'informations, consultez <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Apport et soumission de modifications de données](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [Comment : gérer les conflits de modifications](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
