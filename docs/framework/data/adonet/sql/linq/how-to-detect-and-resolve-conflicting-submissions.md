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
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="9eb2f-102">Comment : détecter et résoudre des soumissions en conflit</span><span class="sxs-lookup"><span data-stu-id="9eb2f-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9eb2f-103"> fournit de nombreuses ressources pour détecter et résoudre des conflits issus de modifications effectuées par plusieurs utilisateurs dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="9eb2f-103"> provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="9eb2f-104">Pour plus d’informations, consultez [Comment : gérer les conflits de modifications](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="9eb2f-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eb2f-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="9eb2f-105">Example</span></span>  
 <span data-ttu-id="9eb2f-106">L’exemple suivant montre un `try` / `catch` bloc qui intercepte un <xref:System.Data.Linq.ChangeConflictException> exception.</span><span class="sxs-lookup"><span data-stu-id="9eb2f-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="9eb2f-107">La fenêtre de console affiche des informations sur les entités et les membres de chaque conflit.</span><span class="sxs-lookup"><span data-stu-id="9eb2f-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9eb2f-108">Vous devez inclure la directive `using System.Reflection` (`Imports System.Reflection` dans Visual Basic) pour prendre en charge la récupération d'informations.</span><span class="sxs-lookup"><span data-stu-id="9eb2f-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="9eb2f-109">Pour plus d'informations, consultez <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="9eb2f-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9eb2f-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9eb2f-110">See Also</span></span>  
 [<span data-ttu-id="9eb2f-111">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="9eb2f-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="9eb2f-112">Comment : gérer les conflits de modifications</span><span class="sxs-lookup"><span data-stu-id="9eb2f-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
