---
title: Exemples de LINQ to DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfd91658-8d8a-45a4-a356-e327e809f21d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 808c12ee0f9a52c09fa32a0bdf2cc0177bf8be4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-dataset-examples"></a><span data-ttu-id="5e1ae-102">Exemples de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="5e1ae-102">LINQ to DataSet Examples</span></span>
<span data-ttu-id="5e1ae-103">Cette section fournit des [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] exemples de programmation qui utilisent les opérateurs de requête standard.</span><span class="sxs-lookup"><span data-stu-id="5e1ae-103">This section provides [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programming examples that use the standard query operators.</span></span> <span data-ttu-id="5e1ae-104">Le <xref:System.Data.DataSet> utilisé dans ces exemples est rempli à l’aide de la `FillDataSet` (méthode), qui est spécifié dans [chargement des données dans un groupe de données](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="5e1ae-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="5e1ae-105">Pour plus d’informations, consultez [vue d’ensemble des opérateurs de requête Standard](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="5e1ae-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5e1ae-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5e1ae-106">In This Section</span></span>  
 [<span data-ttu-id="5e1ae-107">Exemples d’expressions de requête</span><span class="sxs-lookup"><span data-stu-id="5e1ae-107">Query Expression Examples</span></span>](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)  
 <span data-ttu-id="5e1ae-108">Contient les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="5e1ae-108">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="5e1ae-109">Projection</span><span class="sxs-lookup"><span data-stu-id="5e1ae-109">Projection</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
  
-   [<span data-ttu-id="5e1ae-110">Restriction</span><span class="sxs-lookup"><span data-stu-id="5e1ae-110">Restriction</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
  
-   [<span data-ttu-id="5e1ae-111">Le partitionnement</span><span class="sxs-lookup"><span data-stu-id="5e1ae-111">Partitioning</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
  
-   [<span data-ttu-id="5e1ae-112">Classement</span><span class="sxs-lookup"><span data-stu-id="5e1ae-112">Ordering</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="5e1ae-113">Opérateurs d’élément</span><span class="sxs-lookup"><span data-stu-id="5e1ae-113">Element Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="5e1ae-114">Opérateurs d’agrégation</span><span class="sxs-lookup"><span data-stu-id="5e1ae-114">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="5e1ae-115">Opérateurs de jointure</span><span class="sxs-lookup"><span data-stu-id="5e1ae-115">Join Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
  
 [<span data-ttu-id="5e1ae-116">Exemples de requête fondée sur une méthode</span><span class="sxs-lookup"><span data-stu-id="5e1ae-116">Method-Based Query Examples</span></span>](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)  
 <span data-ttu-id="5e1ae-117">Contient les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="5e1ae-117">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="5e1ae-118">Projection</span><span class="sxs-lookup"><span data-stu-id="5e1ae-118">Projection</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
  
-   [<span data-ttu-id="5e1ae-119">Le partitionnement</span><span class="sxs-lookup"><span data-stu-id="5e1ae-119">Partitioning</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
  
-   [<span data-ttu-id="5e1ae-120">Classement</span><span class="sxs-lookup"><span data-stu-id="5e1ae-120">Ordering</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="5e1ae-121">Opérateurs de jeu</span><span class="sxs-lookup"><span data-stu-id="5e1ae-121">Set Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
  
-   [<span data-ttu-id="5e1ae-122">Opérateurs de conversion</span><span class="sxs-lookup"><span data-stu-id="5e1ae-122">Conversion Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
  
-   [<span data-ttu-id="5e1ae-123">Opérateurs d’élément</span><span class="sxs-lookup"><span data-stu-id="5e1ae-123">Element Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="5e1ae-124">Opérateurs d’agrégation</span><span class="sxs-lookup"><span data-stu-id="5e1ae-124">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="5e1ae-125">Join</span><span class="sxs-lookup"><span data-stu-id="5e1ae-125">Join</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
  
 [<span data-ttu-id="5e1ae-126">Exemples d’opérateurs spécifiques aux DataSets</span><span class="sxs-lookup"><span data-stu-id="5e1ae-126">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 <span data-ttu-id="5e1ae-127">Contient des exemples qui montrent comment utiliser la méthode <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> et la classe <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="5e1ae-127">Contains examples that demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e1ae-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e1ae-128">See Also</span></span>  
 [<span data-ttu-id="5e1ae-129">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="5e1ae-129">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
 [<span data-ttu-id="5e1ae-130">Chargement des données dans un jeu de données</span><span class="sxs-lookup"><span data-stu-id="5e1ae-130">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
