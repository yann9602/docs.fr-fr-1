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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2abd54a7ce2500a1fda39dc781052b9d7656afee
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
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
 [Guide pratique pour gérer les conflits de changement](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
