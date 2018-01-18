---
title: "Comment : regrouper des éléments dans une séquence"
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
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b3cf24760c826cf3dac75305eedb33b732869ff1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="group-elements-in-a-sequence"></a><span data-ttu-id="9ba54-102">Comment : regrouper des éléments dans une séquence</span><span class="sxs-lookup"><span data-stu-id="9ba54-102">Group Elements in a Sequence</span></span>
<span data-ttu-id="9ba54-103">L'opérateur <xref:System.Linq.Enumerable.GroupBy%2A> regroupe les éléments d'une séquence.</span><span class="sxs-lookup"><span data-stu-id="9ba54-103">The <xref:System.Linq.Enumerable.GroupBy%2A> operator groups the elements of a sequence.</span></span> <span data-ttu-id="9ba54-104">Les exemples suivants utilisent la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="9ba54-104">The following examples use the Northwind database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ba54-105">Les valeurs de colonne null dans les requêtes <xref:System.Linq.Enumerable.GroupBy%2A> peuvent parfois lever une exception <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="9ba54-105">Null column values in <xref:System.Linq.Enumerable.GroupBy%2A> queries can sometimes throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="9ba54-106">Pour plus d’informations, consultez la section « GroupBy InvalidOperationException » de [dépannage](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="9ba54-106">For more information, see the "GroupBy InvalidOperationException" section of [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ba54-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ba54-107">Example</span></span>  
 <span data-ttu-id="9ba54-108">L'exemple suivant partitionne `Products` par `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="9ba54-108">The following example partitions `Products` by `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a><span data-ttu-id="9ba54-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ba54-109">Example</span></span>  
 <span data-ttu-id="9ba54-110">L'exemple suivant utilise <xref:System.Linq.Enumerable.Max%2A> pour rechercher le prix unitaire maximal pour chaque `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="9ba54-110">The following example uses <xref:System.Linq.Enumerable.Max%2A> to find the maximum unit price for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a><span data-ttu-id="9ba54-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ba54-111">Example</span></span>  
 <span data-ttu-id="9ba54-112">L'exemple suivant utilise Average pour rechercher le `UnitPrice` moyen pour chaque `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="9ba54-112">The following example uses Average to find the average `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="9ba54-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ba54-113">Example</span></span>  
 <span data-ttu-id="9ba54-114">L'exemple suivant utilise <xref:System.Linq.Queryable.Sum%2A> pour rechercher le `UnitPrice` total pour chaque `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="9ba54-114">The following example uses <xref:System.Linq.Queryable.Sum%2A> to find the total `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="9ba54-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ba54-115">Example</span></span>  
 <span data-ttu-id="9ba54-116">L'exemple suivant utilise <xref:System.Linq.Queryable.Count%2A> pour rechercher le nombre de `Products` de fin de série dans chaque `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="9ba54-116">The following example uses <xref:System.Linq.Queryable.Count%2A> to find the number of discontinued `Products` in each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="9ba54-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ba54-117">Example</span></span>  
 <span data-ttu-id="9ba54-118">L'exemple suivant utilise une clause `where` pour rechercher toutes les catégories comportant au moins 10 produits.</span><span class="sxs-lookup"><span data-stu-id="9ba54-118">The following example uses a following `where` clause to find all categories that have at least 10 products.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a><span data-ttu-id="9ba54-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ba54-119">Example</span></span>  
 <span data-ttu-id="9ba54-120">L'exemple suivant regroupe les produits par `CategoryID` et `SupplierID`.</span><span class="sxs-lookup"><span data-stu-id="9ba54-120">The following example groups products by `CategoryID` and `SupplierID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a><span data-ttu-id="9ba54-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ba54-121">Example</span></span>  
 <span data-ttu-id="9ba54-122">L'exemple suivant retourne deux séquences de produits.</span><span class="sxs-lookup"><span data-stu-id="9ba54-122">The following example returns two sequences of products.</span></span> <span data-ttu-id="9ba54-123">La première séquence contient des produits dont le prix unitaire est inférieur ou égal à 10.</span><span class="sxs-lookup"><span data-stu-id="9ba54-123">The first sequence contains products with unit price less than or equal to 10.</span></span> <span data-ttu-id="9ba54-124">La deuxième séquence contient des produits dont le prix unitaire est supérieur à 10.</span><span class="sxs-lookup"><span data-stu-id="9ba54-124">The second sequence contains products with unit price greater than 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a><span data-ttu-id="9ba54-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ba54-125">Example</span></span>  
 <span data-ttu-id="9ba54-126">L'opérateur <xref:System.Linq.Queryable.GroupBy%2A> ne peut prendre qu'un argument Key.</span><span class="sxs-lookup"><span data-stu-id="9ba54-126">The <xref:System.Linq.Queryable.GroupBy%2A> operator can take only a single key argument.</span></span> <span data-ttu-id="9ba54-127">Pour effectuer un regroupement sur plusieurs clés, vous devez créer un type anonyme, comme dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="9ba54-127">If you need to group by more than one key, you must create an anonymous type, as in the following example:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a><span data-ttu-id="9ba54-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ba54-128">See Also</span></span>  
 [<span data-ttu-id="9ba54-129">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="9ba54-129">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="9ba54-130">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="9ba54-130">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
