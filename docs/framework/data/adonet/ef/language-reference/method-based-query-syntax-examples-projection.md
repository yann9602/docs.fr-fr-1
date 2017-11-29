---
title: "Exemples de syntaxe de requête fondée sur une méthode : projection"
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
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9ee7c60f78f50fc4b31b39251c9e432b78a9632b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="1a8e1-102">Exemples de syntaxe de requête fondée sur une méthode : projection</span><span class="sxs-lookup"><span data-stu-id="1a8e1-102">Method-Based Query Syntax Examples: Projection</span></span>
<span data-ttu-id="1a8e1-103">Les exemples de cette rubrique montrent comment utiliser le <xref:System.Linq.Enumerable.Select%2A> et <xref:System.Linq.Enumerable.SelectMany%2A> pour interroger le [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) à l’aide de la syntaxe de requête fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="1a8e1-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methodsto query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="1a8e1-104">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1a8e1-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1a8e1-105">Les exemples de cette rubrique utilisent les éléments suivants `using` / `Imports` instructions :</span><span class="sxs-lookup"><span data-stu-id="1a8e1-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="1a8e1-106">Select</span><span class="sxs-lookup"><span data-stu-id="1a8e1-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="1a8e1-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="1a8e1-107">Example</span></span>  
 <span data-ttu-id="1a8e1-108">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Queryable.Select%2A> pour projeter les propriétés `Product.Name` et `Product.ProductID` dans une séquence de types anonymes.</span><span class="sxs-lookup"><span data-stu-id="1a8e1-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="1a8e1-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="1a8e1-109">Example</span></span>  
 <span data-ttu-id="1a8e1-110">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Select%2A> pour retourner une séquence comportant uniquement des noms de produits.</span><span class="sxs-lookup"><span data-stu-id="1a8e1-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="1a8e1-111">SelectMany</span><span class="sxs-lookup"><span data-stu-id="1a8e1-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="1a8e1-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="1a8e1-112">Example</span></span>  
 <span data-ttu-id="1a8e1-113">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.SelectMany%2A> pour sélectionner toutes les commandes où `TotalDue` est inférieur à 500,00.</span><span class="sxs-lookup"><span data-stu-id="1a8e1-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="1a8e1-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="1a8e1-114">Example</span></span>  
 <span data-ttu-id="1a8e1-115">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.SelectMany%2A> pour sélectionner toutes les commandes qui ont été passées le 1er octobre 2002 ou après.</span><span class="sxs-lookup"><span data-stu-id="1a8e1-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="1a8e1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a8e1-116">See Also</span></span>  
 [<span data-ttu-id="1a8e1-117">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1a8e1-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
