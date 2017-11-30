---
title: "Exemples de syntaxe de requête fondée sur une méthode : opérateurs d'élément"
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
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2ba75d8462e44c7432406139557ac90fa53369f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="0760e-102">Exemples de syntaxe de requête fondée sur une méthode : opérateurs d'élément</span><span class="sxs-lookup"><span data-stu-id="0760e-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="0760e-103">Les exemples de cette rubrique montrent comment utiliser le <xref:System.Linq.Enumerable.First%2A> méthode pour interroger le [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) à l’aide de la syntaxe de requête fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="0760e-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="0760e-104">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0760e-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0760e-105">L’exemple de cette rubrique utilise les éléments suivants `using` / `Imports` instructions :</span><span class="sxs-lookup"><span data-stu-id="0760e-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="0760e-106">First</span><span class="sxs-lookup"><span data-stu-id="0760e-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="0760e-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="0760e-107">Example</span></span>  
 <span data-ttu-id="0760e-108">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.First%2A> pour rechercher la première adresse de messagerie qui commence par 'caroline'.</span><span class="sxs-lookup"><span data-stu-id="0760e-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first e-mail address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="0760e-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0760e-109">See Also</span></span>  
 [<span data-ttu-id="0760e-110">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0760e-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
