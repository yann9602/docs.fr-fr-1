---
title: "Exemples de syntaxe de requête fondée sur une méthode : conversion"
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
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: aafc059b5560af1fef54c20a3718d3f405ce7ba9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="21874-102">Exemples de syntaxe de requête fondée sur une méthode : conversion</span><span class="sxs-lookup"><span data-stu-id="21874-102">Method-Based Query Syntax Examples: Conversion</span></span>
<span data-ttu-id="21874-103">Les exemples de cette rubrique montrent comment utiliser le <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> et <xref:System.Linq.Enumerable.ToList%2A> méthodes permettant d’interroger la [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) à l’aide de la syntaxe de requête fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="21874-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="21874-104">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="21874-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="21874-105">Les exemples de cette rubrique utilisent les éléments suivants `using` / `Imports` instructions :</span><span class="sxs-lookup"><span data-stu-id="21874-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="21874-106">ToArray</span><span class="sxs-lookup"><span data-stu-id="21874-106">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="21874-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="21874-107">Example</span></span>  
 <span data-ttu-id="21874-108">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.ToArray%2A> pour évaluer immédiatement une séquence dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="21874-108">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="21874-109">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="21874-109">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="21874-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="21874-110">Example</span></span>  
 <span data-ttu-id="21874-111">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.ToDictionary%2A> pour évaluer immédiatement une séquence et une expression clé associée dans un dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="21874-111">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="21874-112">ToList</span><span class="sxs-lookup"><span data-stu-id="21874-112">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="21874-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="21874-113">Example</span></span>  
 <span data-ttu-id="21874-114">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.ToList%2A> pour évaluer immédiatement une séquence dans un objet <xref:System.Collections.Generic.List%601> où `T` est de type <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="21874-114">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="21874-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21874-115">See Also</span></span>  
 [<span data-ttu-id="21874-116">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="21874-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
