---
title: Interrogation de DataSets (LINQ to DataSet)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3793417502d359a9d05899f6e1d4306aac7ca88b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="35820-102">Interrogation de DataSets (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="35820-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="35820-103">Une fois qu'un objet <xref:System.Data.DataSet> a été rempli avec des données, vous pouvez commencer de l'interroger.</span><span class="sxs-lookup"><span data-stu-id="35820-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="35820-104">La formulation de requêtes avec [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] est semblable à l'utilisation de [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] sur d'autres sources de données [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="35820-104">Formulating queries with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] is similar to using [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] against other [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-enabled data sources.</span></span> <span data-ttu-id="35820-105">N’oubliez pas, toutefois, que lorsque vous utilisez [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] des requêtes sur un <xref:System.Data.DataSet> objet que vous interrogez une énumération de <xref:System.Data.DataRow> des objets, au lieu d’une énumération d’un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="35820-105">Remember, however, that when you use [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries over a <xref:System.Data.DataSet> object you are querying an enumeration of <xref:System.Data.DataRow> objects, instead of an enumeration of a custom type.</span></span> <span data-ttu-id="35820-106">Cela signifie que vous pouvez utiliser un des membres de la <xref:System.Data.DataRow> classe dans votre [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] des requêtes.</span><span class="sxs-lookup"><span data-stu-id="35820-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="35820-107">Vous pouvez ainsi créer des requêtes riches et complexes.</span><span class="sxs-lookup"><span data-stu-id="35820-107">This lets you to create rich, complex queries.</span></span>  
  
 <span data-ttu-id="35820-108">Comme avec d’autres implémentations de [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], vous pouvez créer [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] requêtes sous deux formes différentes : syntaxe d’expression et la syntaxe de requête fondée sur une méthode de requête.</span><span class="sxs-lookup"><span data-stu-id="35820-108">As with other implementations of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], you can create [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="35820-109">Pour plus d’informations sur ces deux formes, consultez [mise en route de LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).</span><span class="sxs-lookup"><span data-stu-id="35820-109">For more information about these two forms, see [Getting Started with LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).</span></span> <span data-ttu-id="35820-110">Vous pouvez utiliser une syntaxe d'expression de requête ou une syntaxe de requête fondée sur une méthode sur des tables uniques d'un <xref:System.Data.DataSet>, sur plusieurs tables sur un <xref:System.Data.DataSet>, ou sur les tables d'un <xref:System.Data.DataSet> typé.</span><span class="sxs-lookup"><span data-stu-id="35820-110">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35820-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="35820-111">In This Section</span></span>  
 [<span data-ttu-id="35820-112">Requêtes de table unique</span><span class="sxs-lookup"><span data-stu-id="35820-112">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="35820-113">Explique comment exécuter des requêtes d'analyse unique.</span><span class="sxs-lookup"><span data-stu-id="35820-113">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="35820-114">Requêtes de table croisée</span><span class="sxs-lookup"><span data-stu-id="35820-114">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="35820-115">Explique comment exécuter des requêtes d'analyse croisée.</span><span class="sxs-lookup"><span data-stu-id="35820-115">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="35820-116">Interrogation de DataSets typés</span><span class="sxs-lookup"><span data-stu-id="35820-116">Querying Typed DataSets</span></span>](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 <span data-ttu-id="35820-117">Explique comment interroger des objets <xref:System.Data.DataSet> typés.</span><span class="sxs-lookup"><span data-stu-id="35820-117">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35820-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35820-118">See Also</span></span>  
 [<span data-ttu-id="35820-119">Exemples LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="35820-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="35820-120">Chargement de données dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="35820-120">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
