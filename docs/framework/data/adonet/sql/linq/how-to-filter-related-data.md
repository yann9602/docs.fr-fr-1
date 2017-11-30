---
title: "Comment : filtrer des données liées"
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
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2f02b09cc5389a90ea42a0dd851579327972c20c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="9c7dc-102">Comment : filtrer des données liées</span><span class="sxs-lookup"><span data-stu-id="9c7dc-102">How to: Filter Related Data</span></span>
<span data-ttu-id="9c7dc-103">Utilisez la méthode <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> pour spécifier des sous-requêtes afin de limiter la quantité de données récupérées.</span><span class="sxs-lookup"><span data-stu-id="9c7dc-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c7dc-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c7dc-104">Example</span></span>  
 <span data-ttu-id="9c7dc-105">Dans l'exemple suivant, la méthode <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> limite les `Orders` récupérées à celles qui n'ont pas encore été expédiées aujourd'hui.</span><span class="sxs-lookup"><span data-stu-id="9c7dc-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="9c7dc-106">Sans cette approche, toutes les `Orders` auraient été récupérées bien que seul un sous-ensemble soit désiré.</span><span class="sxs-lookup"><span data-stu-id="9c7dc-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9c7dc-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c7dc-107">See Also</span></span>  
 [<span data-ttu-id="9c7dc-108">Interrogation de la base de données</span><span class="sxs-lookup"><span data-stu-id="9c7dc-108">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
