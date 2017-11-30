---
title: DataTableReaders
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ed9094a036262bac2e101e7b4268aac2e66a0d10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="datatablereaders"></a><span data-ttu-id="b6251-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="b6251-102">DataTableReaders</span></span>
<span data-ttu-id="b6251-103">L'objet <xref:System.Data.DataTableReader> présente le contenu d'un objet <xref:System.Data.DataTable> ou d'un objet <xref:System.Data.DataSet> sous la forme d'un ou plusieurs jeux de résultats en lecture seule et en avant uniquement.</span><span class="sxs-lookup"><span data-stu-id="b6251-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="b6251-104">Lorsque vous créez un **DataTableReader** d’un **DataTable**, résultant **DataTableReader** objet contient un jeu de résultats avec les mêmes données que le  **DataTable** à partir de laquelle il a été créé, à l’exception de toutes les lignes qui ont été marquées comme supprimées.</span><span class="sxs-lookup"><span data-stu-id="b6251-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="b6251-105">Les colonnes apparaissent dans le même ordre que l’original **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="b6251-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="b6251-106">A **DataTableReader** peut contenir plusieurs jeux de résultats s’il a été créé en appelant <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6251-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="b6251-107">Les résultats sont dans le même ordre que les **DataTables** dans les **DataSet** l’objet <xref:System.Data.DataSet.Tables%2A> collection.</span><span class="sxs-lookup"><span data-stu-id="b6251-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b6251-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b6251-108">In This Section</span></span>  
 [<span data-ttu-id="b6251-109">Création d’un DataReader</span><span class="sxs-lookup"><span data-stu-id="b6251-109">Creating a DataReader</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 <span data-ttu-id="b6251-110">Explique comment créer un **DataTableReader** objet.</span><span class="sxs-lookup"><span data-stu-id="b6251-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="b6251-111">Navigation dans les tables de données</span><span class="sxs-lookup"><span data-stu-id="b6251-111">Navigating DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 <span data-ttu-id="b6251-112">Décrit l’utilisation de la **en lecture** méthode pour parcourir le contenu d’un **DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="b6251-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6251-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6251-113">See Also</span></span>  
 [<span data-ttu-id="b6251-114">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b6251-114">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="b6251-115">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="b6251-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
