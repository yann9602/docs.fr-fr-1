---
title: LINQ to DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cdd3f21d8b02c24db24d2efd08487ef1a290e022
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="linq-to-dataset"></a><span data-ttu-id="4cf6d-102">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="4cf6d-102">LINQ to DataSet</span></span>
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="4cf6d-103"> facilite et accélère l'interrogation de données mises en cache dans un objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="4cf6d-103"> makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="4cf6d-104">Plus précisément, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifie l’interrogation en permettant aux développeurs d’écrire des requêtes dans le langage de programmation, à la place d’à l’aide d’un langage de requête distincte.</span><span class="sxs-lookup"><span data-stu-id="4cf6d-104">Specifically, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="4cf6d-105">Cela est particulièrement utile pour [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] développeurs peuvent désormais tirer parti de la vérification de la syntaxe de la compilation, les types statiques et prise en charge de IntelliSense fournis par le [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] dans les requêtes.</span><span class="sxs-lookup"><span data-stu-id="4cf6d-105">This is especially useful for [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] in their queries.</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="4cf6d-106"> peut également être utilisé pour interroger des données qui ont été consolidées à partir d'une ou plusieurs sources de données.</span><span class="sxs-lookup"><span data-stu-id="4cf6d-106"> can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="4cf6d-107">Cela permet plusieurs scénarios qui requièrent de la flexibilité dans la manière dont les données sont représentées et gérées, comme l'interrogation de données agrégées localement et la mise en cache en couche intermédiaire dans les applications Web.</span><span class="sxs-lookup"><span data-stu-id="4cf6d-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="4cf6d-108">En particulier, les applications génériques de création de rapports, d'analyse et de business intelligence requièrent cette méthode de manipulation.</span><span class="sxs-lookup"><span data-stu-id="4cf6d-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="4cf6d-109">Le [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] fonctionnalité est exposée principalement via les méthodes d’extension dans le <xref:System.Data.DataRowExtensions> et <xref:System.Data.DataTableExtensions> classes.</span><span class="sxs-lookup"><span data-stu-id="4cf6d-109">The [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="4cf6d-110">s’appuie sur et utilise existants [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architecture et n’est pas censé remplacer [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] dans le code d’application.</span><span class="sxs-lookup"><span data-stu-id="4cf6d-110"> builds on and uses the existing [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architecture, and is not meant to replace [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] in application code.</span></span> <span data-ttu-id="4cf6d-111">Le code ADO.NET 2.0 existant continuera à fonctionner dans une application [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4cf6d-111">Existing ADO.NET 2.0 code will continue to function in a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] application.</span></span> <span data-ttu-id="4cf6d-112">La relation de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] avec [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] et le magasin de données est illustrée dans le diagramme suivant.</span><span class="sxs-lookup"><span data-stu-id="4cf6d-112">The relationship of [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] and the data store is illustrated in the following diagram.</span></span>  
  
 <span data-ttu-id="4cf6d-113">![LINQ to DataSet est basé sur le fournisseur ADO.NET](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span><span class="sxs-lookup"><span data-stu-id="4cf6d-113">![LINQ to DataSet is based on the ADO.NET Provider](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4cf6d-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4cf6d-114">In This Section</span></span>  
 [<span data-ttu-id="4cf6d-115">Prise en main</span><span class="sxs-lookup"><span data-stu-id="4cf6d-115">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="4cf6d-116">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="4cf6d-116">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="4cf6d-117">Référence</span><span class="sxs-lookup"><span data-stu-id="4cf6d-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="4cf6d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4cf6d-118">See Also</span></span>  
 [<span data-ttu-id="4cf6d-119">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="4cf6d-119">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="4cf6d-120">LINQ et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4cf6d-120">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [<span data-ttu-id="4cf6d-121">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4cf6d-121">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
