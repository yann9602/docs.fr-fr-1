---
title: "Définition de schéma de DataTable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e848a0fac5d41628d4d39f1771019eb870e6395b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="datatable-schema-definition"></a><span data-ttu-id="958e2-102">Définition de schéma de DataTable</span><span class="sxs-lookup"><span data-stu-id="958e2-102">DataTable Schema Definition</span></span>
<span data-ttu-id="958e2-103">Le schéma, ou structure, d'une table est représenté par des colonnes et des contraintes.</span><span class="sxs-lookup"><span data-stu-id="958e2-103">The schema, or structure, of a table is represented by columns and constraints.</span></span> <span data-ttu-id="958e2-104">Vous définissez le schéma d'un objet <xref:System.Data.DataTable> à l'aide d'objets <xref:System.Data.DataColumn> ainsi que d'objets <xref:System.Data.ForeignKeyConstraint> et <xref:System.Data.UniqueConstraint>.</span><span class="sxs-lookup"><span data-stu-id="958e2-104">You define the schema of a <xref:System.Data.DataTable> using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="958e2-105">Les colonnes d'une table peuvent mapper aux colonnes d'une source de données. Elles contiennent des valeurs calculées à partir d'expressions, incrémentent automatiquement leurs valeurs ou contiennent des valeurs de clé primaire.</span><span class="sxs-lookup"><span data-stu-id="958e2-105">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="958e2-106">Les références par nom aux colonnes, relations et contraintes d'une table respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="958e2-106">References by name to columns, relations, and constraints in a table are case-sensitive.</span></span> <span data-ttu-id="958e2-107">Une table peut donc contenir plusieurs colonnes, relations ou contraintes dont les noms ne diffèrent que par la casse.</span><span class="sxs-lookup"><span data-stu-id="958e2-107">Two or more columns, relations, or constraints can therefore exist in a table that have the same name, but that differ in case.</span></span> <span data-ttu-id="958e2-108">Par exemple, vous pouvez avoir **Col1** et **col1**.</span><span class="sxs-lookup"><span data-stu-id="958e2-108">For example, you can have **Col1** and **col1**.</span></span> <span data-ttu-id="958e2-109">Dans ce cas, une référence par nom à l'une des colonnes doit correspondre exactement à la casse du nom de colonne. Sinon, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="958e2-109">In such as case, a reference to one of the columns by name must match the case of the column name exactly; otherwise an exception is thrown.</span></span> <span data-ttu-id="958e2-110">Par exemple, si la table **myTable** contient les colonnes **Col1** et **col1**, vous devez référencer **Col1** par nom comme  **myTable.Columns["Col1 »]**, et **col1** en tant que **myTable.Columns["col1 »]**.</span><span class="sxs-lookup"><span data-stu-id="958e2-110">For example, if the table **myTable** contains the columns **Col1** and **col1**, you would reference **Col1** by name as **myTable.Columns["Col1"]**, and **col1** as **myTable.Columns["col1"]**.</span></span> <span data-ttu-id="958e2-111">Tentative de référencer une des colonnes en tant que **myTable.Columns["COL1 »]** génèrent une exception.</span><span class="sxs-lookup"><span data-stu-id="958e2-111">Attempting to reference either of the columns as **myTable.Columns["COL1"]** would generate an exception.</span></span>  
  
 <span data-ttu-id="958e2-112">La règle de respect de la casse ne s'applique pas s'il n'existe qu'une seule colonne, relation ou contrainte ayant un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="958e2-112">The case-sensitivity rule does not apply if only one column, relation, or constraint  with a particular name exists.</span></span> <span data-ttu-id="958e2-113">En d'autres termes, si aucun autre objet de colonne, relation ou contrainte de la table ne correspond au nom de cet objet de colonne, relation ou contrainte, vous pouvez référencer l'objet par son nom sans respecter la casse, sans qu'une exception ne soit levée.</span><span class="sxs-lookup"><span data-stu-id="958e2-113">That is, if no other column, relation, or constraint object in the table matches the name of that particular column, relation, or constraint object, you may reference the object by name using any case, and no exception is thrown.</span></span> <span data-ttu-id="958e2-114">Par exemple, si la table n’a que **Col1**, vous pouvez faire référence à l’aide de **mon. Colonnes [« COL1 »]**.</span><span class="sxs-lookup"><span data-stu-id="958e2-114">For example, if the table has only **Col1**, you can reference it using **my.Columns["COL1"]**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="958e2-115">Le <xref:System.Data.DataTable.CaseSensitive%2A> propriété de la **DataTable** n’affecte pas ce comportement.</span><span class="sxs-lookup"><span data-stu-id="958e2-115">The <xref:System.Data.DataTable.CaseSensitive%2A> property of the **DataTable** does not affect this behavior.</span></span> <span data-ttu-id="958e2-116">Le **CaseSensitive** propriété s’applique aux données dans une table et affecte le tri, la recherche, le filtrage, en appliquant des contraintes et ainsi de suite, mais pas pour les références aux colonnes, relations et contraintes.</span><span class="sxs-lookup"><span data-stu-id="958e2-116">The **CaseSensitive** property applies to the data in a table and affects sorting, searching, filtering, enforcing constraints, and so on, but not to references to the columns, relations, and constraints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="958e2-117">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="958e2-117">In This Section</span></span>  
 [<span data-ttu-id="958e2-118">Ajout de colonnes à un DataTable</span><span class="sxs-lookup"><span data-stu-id="958e2-118">Adding Columns to a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 <span data-ttu-id="958e2-119">Décrit comment définir les colonnes d’une table à l’aide de **DataColumn** objets.</span><span class="sxs-lookup"><span data-stu-id="958e2-119">Describes how to define the columns of a table using **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="958e2-120">Création de colonnes d’expressions</span><span class="sxs-lookup"><span data-stu-id="958e2-120">Creating Expression Columns</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 <span data-ttu-id="958e2-121">Explique comment la **Expression** propriété d’une colonne peut être utilisée pour calculer des valeurs basées sur les valeurs des autres colonnes dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="958e2-121">Explains how the **Expression** property of a column can be used to calculate values based on the values from other columns in the row.</span></span>  
  
 [<span data-ttu-id="958e2-122">Création de colonnes AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="958e2-122">Creating AutoIncrement Columns</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 <span data-ttu-id="958e2-123">Décrit comment définir une colonne afin qu'elle incrémente automatiquement des valeurs numériques de façon à garantir le caractère unique des valeurs de colonne d'une ligne.</span><span class="sxs-lookup"><span data-stu-id="958e2-123">Describes how a column can be set to automatically increment numerical values to ensure a unique column value per row.</span></span>  
  
 [<span data-ttu-id="958e2-124">Définition des clés primaires</span><span class="sxs-lookup"><span data-stu-id="958e2-124">Defining Primary Keys</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 <span data-ttu-id="958e2-125">Explique comment spécifier la clé primaire d’une table à partir d’un ou plusieurs **DataColumn** objets.</span><span class="sxs-lookup"><span data-stu-id="958e2-125">Describes how to specify the primary key of a table from one or more **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="958e2-126">Contraintes de DataTable</span><span class="sxs-lookup"><span data-stu-id="958e2-126">DataTable Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 <span data-ttu-id="958e2-127">Décrit comment définir des contraintes uniques et de clé étrangère pour les colonnes d'une table.</span><span class="sxs-lookup"><span data-stu-id="958e2-127">Describes how to define foreign key and unique constraints for columns in a table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="958e2-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="958e2-128">See Also</span></span>  
 [<span data-ttu-id="958e2-129">DataTables</span><span class="sxs-lookup"><span data-stu-id="958e2-129">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="958e2-130">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="958e2-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
