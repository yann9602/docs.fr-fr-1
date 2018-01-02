---
title: "Comment : récupérer des informations sur les conflits entre membres"
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
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e9dd92ad1b5c91798923296def8f207637b4bad2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="38d9b-102">Comment : récupérer des informations sur les conflits entre membres</span><span class="sxs-lookup"><span data-stu-id="38d9b-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="38d9b-103">Vous pouvez utiliser la classe <xref:System.Data.Linq.MemberChangeConflict> pour récupérer des informations sur des membres individuels en conflit.</span><span class="sxs-lookup"><span data-stu-id="38d9b-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="38d9b-104">Dans ce contexte, vous pouvez assurer la gestion personnalisée du conflit pour un membre quelconque.</span><span class="sxs-lookup"><span data-stu-id="38d9b-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="38d9b-105">Pour plus d’informations, consultez [d’accès concurrentiel optimiste : vue d’ensemble](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="38d9b-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="38d9b-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="38d9b-106">Example</span></span>  
 <span data-ttu-id="38d9b-107">Le code suivant itère au sein des objets <xref:System.Data.Linq.ObjectChangeConflict>.</span><span class="sxs-lookup"><span data-stu-id="38d9b-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="38d9b-108">Pour chacun de ces objets, il itère ensuite au sein des objets <xref:System.Data.Linq.MemberChangeConflict>.</span><span class="sxs-lookup"><span data-stu-id="38d9b-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38d9b-109">Incluez <xref:System.Reflection> pour fournir des informations <xref:System.Data.Linq.MemberChangeConflict.Member%2A>.</span><span class="sxs-lookup"><span data-stu-id="38d9b-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="38d9b-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38d9b-110">See Also</span></span>  
 [<span data-ttu-id="38d9b-111">Guide pratique pour gérer les conflits de changement</span><span class="sxs-lookup"><span data-stu-id="38d9b-111">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
