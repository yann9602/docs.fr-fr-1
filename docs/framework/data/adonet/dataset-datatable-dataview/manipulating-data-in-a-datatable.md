---
title: "Manipulation des données dans un DataTable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 58d04a3ba1d73d4236353ff4f08a747ac7b6f0cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="9c9db-102">Manipulation des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="9c9db-102">Manipulating Data in a DataTable</span></span>
<span data-ttu-id="9c9db-103">Après avoir créé un objet <xref:System.Data.DataTable> dans un objet <xref:System.Data.DataSet>, vous pouvez réaliser les mêmes opérations que lorsque vous utilisez une table d'une base de données.</span><span class="sxs-lookup"><span data-stu-id="9c9db-103">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="9c9db-104">Vous pouvez ajouter, afficher, modifier et supprimer les données de la table, surveiller les erreurs et les événements et interroger les données de la table.</span><span class="sxs-lookup"><span data-stu-id="9c9db-104">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="9c9db-105">Lors de la modification des données dans un **DataTable**, vous pouvez également vérifier si les modifications sont précises et déterminent s’il faut accepter ou rejeter les modifications par programme.</span><span class="sxs-lookup"><span data-stu-id="9c9db-105">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c9db-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9c9db-106">In This Section</span></span>  
 [<span data-ttu-id="9c9db-107">Ajout de données à un DataTable</span><span class="sxs-lookup"><span data-stu-id="9c9db-107">Adding Data to a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-data-to-a-datatable.md)  
 <span data-ttu-id="9c9db-108">Explique comment créer des lignes et les ajouter à une table.</span><span class="sxs-lookup"><span data-stu-id="9c9db-108">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="9c9db-109">Affichage des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="9c9db-109">Viewing Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/viewing-data-in-a-datatable.md)  
 <span data-ttu-id="9c9db-110">Décrit comment accéder aux données d'une ligne, notamment aux versions actuelles et d'origine des données.</span><span class="sxs-lookup"><span data-stu-id="9c9db-110">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="9c9db-111">Méthode Load</span><span class="sxs-lookup"><span data-stu-id="9c9db-111">The Load Method</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/the-load-method.md)  
 <span data-ttu-id="9c9db-112">Décrit l’utilisation de la **charge** méthode pour remplir un **DataTable** avec des lignes.</span><span class="sxs-lookup"><span data-stu-id="9c9db-112">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="9c9db-113">Modifications de DataTable</span><span class="sxs-lookup"><span data-stu-id="9c9db-113">DataTable Edits</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-edits.md)  
 <span data-ttu-id="9c9db-114">Explique comment modifier les données d'une ligne, notamment suspendre les modifications d'une ligne jusqu'à la vérification et l'acceptation des modifications proposées.</span><span class="sxs-lookup"><span data-stu-id="9c9db-114">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="9c9db-115">États des lignes et versions des lignes</span><span class="sxs-lookup"><span data-stu-id="9c9db-115">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 <span data-ttu-id="9c9db-116">Fournit des informations sur les différents états d'une ligne.</span><span class="sxs-lookup"><span data-stu-id="9c9db-116">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="9c9db-117">Suppression de DataRow</span><span class="sxs-lookup"><span data-stu-id="9c9db-117">DataRow Deletion</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarow-deletion.md)  
 <span data-ttu-id="9c9db-118">Décrit comment supprimer une ligne d'une table.</span><span class="sxs-lookup"><span data-stu-id="9c9db-118">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="9c9db-119">Informations sur l’erreur de ligne</span><span class="sxs-lookup"><span data-stu-id="9c9db-119">Row Error Information</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 <span data-ttu-id="9c9db-120">Explique comment insérer des informations d'erreur par ligne et résoudre les problèmes liés aux données dans une application.</span><span class="sxs-lookup"><span data-stu-id="9c9db-120">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="9c9db-121">AcceptChanges et RejectChanges</span><span class="sxs-lookup"><span data-stu-id="9c9db-121">AcceptChanges and RejectChanges</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="9c9db-122">Explique comment accepter ou rejeter les modifications apportées à une ligne.</span><span class="sxs-lookup"><span data-stu-id="9c9db-122">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c9db-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c9db-123">See Also</span></span>  
 [<span data-ttu-id="9c9db-124">DataTables</span><span class="sxs-lookup"><span data-stu-id="9c9db-124">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="9c9db-125">Gestion des événements de DataTable</span><span class="sxs-lookup"><span data-stu-id="9c9db-125">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="9c9db-126">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="9c9db-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
