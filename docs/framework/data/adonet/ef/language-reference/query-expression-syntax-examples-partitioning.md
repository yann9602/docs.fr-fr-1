---
title: "Exemples de syntaxe d'expression de requête : partition"
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
ms.assetid: 7e41aed0-3be9-4f75-98de-860a85552a3c
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7e69a1120130b3b740ac6f1f8d187d8139ba1142
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="query-expression-syntax-examples-partitioning"></a><span data-ttu-id="3e06f-102">Exemples de syntaxe d'expression de requête : partition</span><span class="sxs-lookup"><span data-stu-id="3e06f-102">Query Expression Syntax Examples: Partitioning</span></span>
<span data-ttu-id="3e06f-103">Les exemples de cette rubrique montrent comment utiliser le <xref:System.Linq.Enumerable.Skip%2A> et <xref:System.Linq.Enumerable.Take%2A> méthodes permettant d’interroger la [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) à l’aide de la syntaxe d’expression de requête.</span><span class="sxs-lookup"><span data-stu-id="3e06f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="3e06f-104">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3e06f-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="3e06f-105">Les exemples de cette rubrique utilisent les éléments suivants `using` / `Imports` instructions :</span><span class="sxs-lookup"><span data-stu-id="3e06f-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="3e06f-106">Ignorer</span><span class="sxs-lookup"><span data-stu-id="3e06f-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="3e06f-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="3e06f-107">Example</span></span>  
 <span data-ttu-id="3e06f-108">L'exemple suivant utilise la méthode <xref:System.Linq.Enumerable.Skip%2A> pour obtenir toutes les adresses de Seattle, à l'exception des deux premières.</span><span class="sxs-lookup"><span data-stu-id="3e06f-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="3e06f-109">Take</span><span class="sxs-lookup"><span data-stu-id="3e06f-109">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="3e06f-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="3e06f-110">Example</span></span>  
 <span data-ttu-id="3e06f-111">L'exemple suivant utilise la méthode <xref:System.Linq.Enumerable.Take%2A> pour obtenir les trois premières adresses de Seattle.</span><span class="sxs-lookup"><span data-stu-id="3e06f-111">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="3e06f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e06f-112">See Also</span></span>  
 [<span data-ttu-id="3e06f-113">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="3e06f-113">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
