---
title: "Tri et filtre de données"
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
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2411307623c714ae521d00dcffca05d3569a656e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="bf30a-102">Tri et filtre de données</span><span class="sxs-lookup"><span data-stu-id="bf30a-102">Sorting and Filtering Data</span></span>
<span data-ttu-id="bf30a-103">L'objet <xref:System.Data.DataView> offre plusieurs méthodes de tri et de filtrage de données dans un objet <xref:System.Data.DataTable> :</span><span class="sxs-lookup"><span data-stu-id="bf30a-103">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
-   <span data-ttu-id="bf30a-104">Vous pouvez utiliser la propriété <xref:System.Data.DataView.Sort%2A> pour spécifier un ordre de tri en fonction d'une ou de plusieurs colonnes et inclure des paramètres ASC (ordre croissant) et DESC (ordre décroissant).</span><span class="sxs-lookup"><span data-stu-id="bf30a-104">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
-   <span data-ttu-id="bf30a-105">Vous pouvez utiliser la propriété <xref:System.Data.DataView.ApplyDefaultSort%2A> pour créer automatiquement un ordre de tri, croissant, basé sur la ou les colonnes de clé primaire de la table.</span><span class="sxs-lookup"><span data-stu-id="bf30a-105">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="bf30a-106"><xref:System.Data.DataView.ApplyDefaultSort%2A>s’applique uniquement lorsque le **tri** propriété est une référence null ou une chaîne vide, et lorsque la table a une clé primaire définie.</span><span class="sxs-lookup"><span data-stu-id="bf30a-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
-   <span data-ttu-id="bf30a-107">Vous pouvez utiliser la propriété <xref:System.Data.DataView.RowFilter%2A> pour spécifier des sous-ensembles de lignes basés sur les valeurs de colonne.</span><span class="sxs-lookup"><span data-stu-id="bf30a-107">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="bf30a-108">Pour plus d’informations sur les expressions valides pour la **RowFilter** propriété, consultez les informations de référence pour le <xref:System.Data.DataColumn.Expression%2A> propriété de la <xref:System.Data.DataColumn> classe.</span><span class="sxs-lookup"><span data-stu-id="bf30a-108">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="bf30a-109">Si vous souhaitez retourner les résultats d’une requête particulière exécutée sur les données, au lieu de fournir une vue dynamique d’un sous-ensemble des données, utilisez la <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> méthodes de la **DataView** pour obtenir des performances optimales au lieu de définition de la **RowFilter** propriété.</span><span class="sxs-lookup"><span data-stu-id="bf30a-109">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="bf30a-110">Définition de la **RowFilter** propriété reconstruit l’index des données, ce qui accroît la charge pour votre application et de diminuer les performances.</span><span class="sxs-lookup"><span data-stu-id="bf30a-110">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="bf30a-111">Le **RowFilter** propriété est mieux utilisée dans une application de liaison de données où un contrôle lié affiche des résultats filtrés.</span><span class="sxs-lookup"><span data-stu-id="bf30a-111">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="bf30a-112">Le **trouver** et **FindRows** méthodes tirer parti de l’index en cours sans nécessiter de l’index à reconstruire.</span><span class="sxs-lookup"><span data-stu-id="bf30a-112">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="bf30a-113">Pour plus d’informations sur la **trouver** et **FindRows** méthodes, consultez [recherche les lignes](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="bf30a-113">For more information about the **Find** and **FindRows** methods, see [Finding Rows](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
-   <span data-ttu-id="bf30a-114">Vous pouvez utiliser la propriété <xref:System.Data.DataView.RowStateFilter%2A> pour spécifier les versions de ligne à afficher.</span><span class="sxs-lookup"><span data-stu-id="bf30a-114">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="bf30a-115">Le **DataView** gère implicitement la version de ligne à exposer en fonction de la **RowState** de la ligne sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="bf30a-115">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="bf30a-116">Par exemple, si le **RowStateFilter** a la valeur **DataViewRowState.Deleted**, le **DataView** expose le **d’origine** version de ligne de tous les **Deleted** lignes, car il n’est pas **actuel** version de ligne.</span><span class="sxs-lookup"><span data-stu-id="bf30a-116">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="bf30a-117">Vous pouvez déterminer quelle version de ligne d’une ligne est affichée à l’aide de la **RowVersion** propriété de la **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="bf30a-117">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="bf30a-118">Le tableau suivant montre les options pour **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="bf30a-118">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="bf30a-119">Options DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="bf30a-119">DataViewRowState options</span></span>|<span data-ttu-id="bf30a-120">Description</span><span class="sxs-lookup"><span data-stu-id="bf30a-120">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="bf30a-121">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="bf30a-121">**CurrentRows**</span></span>|<span data-ttu-id="bf30a-122">Le **actuel** version de ligne de toutes les **Unchanged**, **Added**, et **modifié** lignes.</span><span class="sxs-lookup"><span data-stu-id="bf30a-122">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="bf30a-123">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="bf30a-123">This is the default.</span></span>|  
    |<span data-ttu-id="bf30a-124">**Ajouté**</span><span class="sxs-lookup"><span data-stu-id="bf30a-124">**Added**</span></span>|<span data-ttu-id="bf30a-125">Le **actuel** version de ligne de toutes les **Added** lignes.</span><span class="sxs-lookup"><span data-stu-id="bf30a-125">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="bf30a-126">**Deleted**</span><span class="sxs-lookup"><span data-stu-id="bf30a-126">**Deleted**</span></span>|<span data-ttu-id="bf30a-127">Le **d’origine** version de ligne de toutes les **Deleted** lignes.</span><span class="sxs-lookup"><span data-stu-id="bf30a-127">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="bf30a-128">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="bf30a-128">**ModifiedCurrent**</span></span>|<span data-ttu-id="bf30a-129">Le **actuel** version de ligne de toutes les **modifié** lignes.</span><span class="sxs-lookup"><span data-stu-id="bf30a-129">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="bf30a-130">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="bf30a-130">**ModifiedOriginal**</span></span>|<span data-ttu-id="bf30a-131">Le **d’origine** version de ligne de toutes les **modifié** lignes.</span><span class="sxs-lookup"><span data-stu-id="bf30a-131">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="bf30a-132">**Aucun**</span><span class="sxs-lookup"><span data-stu-id="bf30a-132">**None**</span></span>|<span data-ttu-id="bf30a-133">Aucune ligne.</span><span class="sxs-lookup"><span data-stu-id="bf30a-133">No rows.</span></span>|  
    |<span data-ttu-id="bf30a-134">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="bf30a-134">**OriginalRows**</span></span>|<span data-ttu-id="bf30a-135">Le **d’origine** version de ligne de toutes les **Unchanged**, **modifié**, et **Deleted** lignes.</span><span class="sxs-lookup"><span data-stu-id="bf30a-135">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="bf30a-136">**Non modifié**</span><span class="sxs-lookup"><span data-stu-id="bf30a-136">**Unchanged**</span></span>|<span data-ttu-id="bf30a-137">Le **actuel** version de ligne de toutes les **Unchanged** lignes.</span><span class="sxs-lookup"><span data-stu-id="bf30a-137">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="bf30a-138">Pour plus d’informations sur les États et les versions de ligne, consultez [état des lignes et des Versions de ligne](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="bf30a-138">For more information about row states and row versions, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="bf30a-139">L'exemple de code suivant crée une vue faisant apparaître tous les produits pour lesquels la quantité en stock est inférieure ou égale au niveau de passage d'une nouvelle commande, triés d'abord par ID de fournisseur, puis par nom de produit.</span><span class="sxs-lookup"><span data-stu-id="bf30a-139">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf30a-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf30a-140">See Also</span></span>  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="bf30a-141">DataViews</span><span class="sxs-lookup"><span data-stu-id="bf30a-141">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="bf30a-142">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="bf30a-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
