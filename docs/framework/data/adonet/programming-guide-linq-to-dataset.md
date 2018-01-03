---
title: Guide de programmation (LINQ to DataSet)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 298ff0c6bfc5bc251483de8e90e3a394a2337369
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="8afc5-102">Guide de programmation (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="8afc5-102">Programming Guide (LINQ to DataSet)</span></span>
<span data-ttu-id="8afc5-103">Cette section fournit des informations conceptuelles et des exemples pour la programmation avec [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8afc5-103">This section provides conceptual information and examples for programming with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8afc5-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8afc5-104">In This Section</span></span>  
 [<span data-ttu-id="8afc5-105">Requêtes dans LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="8afc5-105">Queries in LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md)  
 <span data-ttu-id="8afc5-106">Fournit des informations sur la manière d'écrire des requêtes [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8afc5-106">Provides information about how to write [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="8afc5-107">Interrogation de DataSets</span><span class="sxs-lookup"><span data-stu-id="8afc5-107">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="8afc5-108">Explique comment interroger des objets <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8afc5-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="8afc5-109">Comparaison de DataRows</span><span class="sxs-lookup"><span data-stu-id="8afc5-109">Comparing DataRows</span></span>](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="8afc5-110">Explique comment utiliser l'objet <xref:System.Data.DataRowComparer> pour comparer des lignes de données.</span><span class="sxs-lookup"><span data-stu-id="8afc5-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="8afc5-111">Création d’un DataTable à partir d’une requête</span><span class="sxs-lookup"><span data-stu-id="8afc5-111">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="8afc5-112">Fournit des informations sur la création d’un <xref:System.Data.DataTable> à partir d’un [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] requête à l’aide de la <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="8afc5-112">Provides information about creating a <xref:System.Data.DataTable> from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="8afc5-113">Comment : implémenter CopyToDataTable\<T > où le Type générique T n’est pas un DataRow</span><span class="sxs-lookup"><span data-stu-id="8afc5-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="8afc5-114">Explique comment implémenter une méthode `CopyToDataTable<T>` personnalisée dans laquelle le paramètre générique T n'est pas du type <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="8afc5-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="8afc5-115">Méthodes génériques Field et SetField</span><span class="sxs-lookup"><span data-stu-id="8afc5-115">Generic Field and SetField Methods</span></span>](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="8afc5-116">Fournit des informations sur les méthodes génériques <xref:System.Data.DataRowExtensions.Field%2A> et <xref:System.Data.DataRowExtensions.SetField%2A>.</span><span class="sxs-lookup"><span data-stu-id="8afc5-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="8afc5-117">Liaison de données et LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="8afc5-117">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="8afc5-118">Décrit la liaison de données à l'aide de l'objet <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="8afc5-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="8afc5-119">Débogage des requêtes LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="8afc5-119">Debugging LINQ to DataSet Queries</span></span>](../../../../docs/framework/data/adonet/debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="8afc5-120">Fournit des informations de débogage et dépannage [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] requêtes.</span><span class="sxs-lookup"><span data-stu-id="8afc5-120">Provides information about debugging and troubleshooting [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="8afc5-121">Sécurité</span><span class="sxs-lookup"><span data-stu-id="8afc5-121">Security</span></span>](../../../../docs/framework/data/adonet/security-linq-to-dataset.md)  
 <span data-ttu-id="8afc5-122">Décrit les problèmes de sécurité dans [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8afc5-122">Describes security issues in [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
 [<span data-ttu-id="8afc5-123">Exemples LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="8afc5-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 <span data-ttu-id="8afc5-124">Fournit des exemples de requête qui utilisent des opérateurs [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8afc5-124">Provides query examples that use the [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8afc5-125">Référence</span><span class="sxs-lookup"><span data-stu-id="8afc5-125">Reference</span></span>  
 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="8afc5-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8afc5-126">See Also</span></span>  
 [<span data-ttu-id="8afc5-127">LINQ to ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8afc5-127">LINQ to ADO.NET</span></span>](http://msdn.microsoft.com/en-us/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 [<span data-ttu-id="8afc5-128">NOT IN BUILD : Guide de programmation général LINQ</span><span class="sxs-lookup"><span data-stu-id="8afc5-128">NOT IN BUILD: LINQ General Programming Guide</span></span>](http://msdn.microsoft.com/en-us/609c7a6b-cbdd-429d-99f3-78d13d3bc049)  
 [<span data-ttu-id="8afc5-129">Infrastructure LINQ</span><span class="sxs-lookup"><span data-stu-id="8afc5-129">LINQ Framework</span></span>](http://msdn.microsoft.com/en-us/897ea0fc-40db-4694-bbe5-7dd339d5bf94)
