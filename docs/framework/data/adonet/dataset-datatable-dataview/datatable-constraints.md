---
title: Contraintes de DataTable
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
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 500dad1699843bae04aea6d5c16a1ccf53bb102a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="datatable-constraints"></a><span data-ttu-id="877fd-102">Contraintes de DataTable</span><span class="sxs-lookup"><span data-stu-id="877fd-102">DataTable Constraints</span></span>
<span data-ttu-id="877fd-103">Vous pouvez utiliser des contraintes pour appliquer des restrictions sur les données dans un objet <xref:System.Data.DataTable> afin de conserver l'intégrité des données.</span><span class="sxs-lookup"><span data-stu-id="877fd-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="877fd-104">Une contrainte est une règle automatique, appliquée à une ou plusieurs colonnes en relation, qui détermine l'action à réaliser lorsque la valeur d'une ligne est modifiée.</span><span class="sxs-lookup"><span data-stu-id="877fd-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="877fd-105">Les contraintes sont appliquées lors de la `System.Data.DataSet.EnforceConstraints` propriété de la <xref:System.Data.DataSet> est **true**.</span><span class="sxs-lookup"><span data-stu-id="877fd-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="877fd-106">Pour obtenir un exemple de code montrant comment définir la propriété `EnforceConstraints`, consultez la rubrique de référence <xref:System.Data.DataSet.EnforceConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="877fd-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="877fd-107">Il y a deux types de contraintes dans ADO.NET : la <xref:System.Data.ForeignKeyConstraint> et la <xref:System.Data.UniqueConstraint>.</span><span class="sxs-lookup"><span data-stu-id="877fd-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="877fd-108">Par défaut, les deux contraintes sont automatiquement créées lorsque vous créez une relation entre deux ou plusieurs tables en ajoutant un <xref:System.Data.DataRelation> à la **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="877fd-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="877fd-109">Toutefois, vous pouvez désactiver ce comportement en spécifiant **createConstraints** = **false** lors de la création de la relation.</span><span class="sxs-lookup"><span data-stu-id="877fd-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="877fd-110">ForeignKeyConstraint</span><span class="sxs-lookup"><span data-stu-id="877fd-110">ForeignKeyConstraint</span></span>  
 <span data-ttu-id="877fd-111">A **ForeignKeyConstraint** applique des règles sur la manière dont les mises à jour et suppressions dans les tables connexes sont propagées.</span><span class="sxs-lookup"><span data-stu-id="877fd-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="877fd-112">Par exemple, si une valeur dans une ligne d’une table est mise à jour ou supprimée et cette valeur est également utilisée dans une ou plusieurs tables connexes, une **ForeignKeyConstraint** détermine ce qui se passe dans les tables associées.</span><span class="sxs-lookup"><span data-stu-id="877fd-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="877fd-113">Le <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> et <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> propriétés de la **ForeignKeyConstraint** définissent l’action à entreprendre lorsque l’utilisateur tente de supprimer ou mettre à jour une ligne dans une table associée.</span><span class="sxs-lookup"><span data-stu-id="877fd-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="877fd-114">Le tableau suivant décrit les différents paramètres disponibles pour le **DeleteRule** et **UpdateRule** propriétés de la **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="877fd-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="877fd-115">Paramètre de règle</span><span class="sxs-lookup"><span data-stu-id="877fd-115">Rule setting</span></span>|<span data-ttu-id="877fd-116">Description</span><span class="sxs-lookup"><span data-stu-id="877fd-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="877fd-117">**Cascade**</span><span class="sxs-lookup"><span data-stu-id="877fd-117">**Cascade**</span></span>|<span data-ttu-id="877fd-118">Supprime ou met à jour les lignes connexes.</span><span class="sxs-lookup"><span data-stu-id="877fd-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="877fd-119">**SetNull**</span><span class="sxs-lookup"><span data-stu-id="877fd-119">**SetNull**</span></span>|<span data-ttu-id="877fd-120">Définir les valeurs des lignes connexes **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="877fd-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="877fd-121">**SetDefault**</span><span class="sxs-lookup"><span data-stu-id="877fd-121">**SetDefault**</span></span>|<span data-ttu-id="877fd-122">Définit les valeurs des lignes connexes sur la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="877fd-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="877fd-123">**Aucun**</span><span class="sxs-lookup"><span data-stu-id="877fd-123">**None**</span></span>|<span data-ttu-id="877fd-124">N'effectue aucune action sur les lignes connexes.</span><span class="sxs-lookup"><span data-stu-id="877fd-124">Take no action on related rows.</span></span> <span data-ttu-id="877fd-125">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="877fd-125">This is the default.</span></span>|  
  
 <span data-ttu-id="877fd-126">A **ForeignKeyConstraint** peuvent limiter, et propager les modifications apportées à des colonnes associées.</span><span class="sxs-lookup"><span data-stu-id="877fd-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="877fd-127">En fonction des propriétés définies pour le **ForeignKeyConstraint** d’une colonne, si le **EnforceConstraints** propriété de la **DataSet** est **lavaleurtrue**, certaines opérations réalisées dans la ligne parente entraîne une exception.</span><span class="sxs-lookup"><span data-stu-id="877fd-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="877fd-128">Par exemple, si le **DeleteRule** propriété de la **ForeignKeyConstraint** est **aucun**, une ligne parente ne peut pas être supprimée s’il a des lignes enfants.</span><span class="sxs-lookup"><span data-stu-id="877fd-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="877fd-129">Vous pouvez créer une contrainte de clé étrangère entre des colonnes uniques ou entre un tableau de colonnes à l’aide de la **ForeignKeyConstraint** constructeur.</span><span class="sxs-lookup"><span data-stu-id="877fd-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="877fd-130">Passez résultant **ForeignKeyConstraint** de l’objet à la **ajouter** (méthode) de la table **contraintes** propriété, qui est un **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="877fd-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="877fd-131">Vous pouvez également passer des arguments de constructeur à plusieurs surcharges de la **ajouter** méthode d’un **ConstraintCollection** pour créer un **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="877fd-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="877fd-132">Lorsque vous créez un **ForeignKeyConstraint**, que vous pouvez passer le **DeleteRule** et **UpdateRule** valeurs au constructeur en tant qu’arguments, ou vous peuvent les définir en tant que propriétés comme dans le après exemple (où le **DeleteRule** a la valeur **aucun**).</span><span class="sxs-lookup"><span data-stu-id="877fd-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None    
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],   
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;    
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a><span data-ttu-id="877fd-133">AcceptRejectRule</span><span class="sxs-lookup"><span data-stu-id="877fd-133">AcceptRejectRule</span></span>  
 <span data-ttu-id="877fd-134">Modifications apportées aux lignes peuvent être acceptées à l’aide de la **AcceptChanges** méthode ou annulées à l’aide du **RejectChanges** méthode de la **DataSet**, **DataTable**, ou **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="877fd-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="877fd-135">Lorsqu’un **DataSet** contient **ForeignKeyConstraints**, l’appel le **AcceptChanges** ou **RejectChanges** méthodes applique le  **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="877fd-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="877fd-136">Le **AcceptRejectRule** propriété de la **ForeignKeyConstraint** détermine l’action à entreprendre sur les enfants des lignes lorsque **AcceptChanges** ou  **RejectChanges** est appelée sur la ligne parente.</span><span class="sxs-lookup"><span data-stu-id="877fd-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="877fd-137">Le tableau suivant répertorie les paramètres disponibles pour le **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="877fd-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="877fd-138">Paramètre de règle</span><span class="sxs-lookup"><span data-stu-id="877fd-138">Rule setting</span></span>|<span data-ttu-id="877fd-139">Description</span><span class="sxs-lookup"><span data-stu-id="877fd-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="877fd-140">**Cascade**</span><span class="sxs-lookup"><span data-stu-id="877fd-140">**Cascade**</span></span>|<span data-ttu-id="877fd-141">Accepte ou rejette les modifications des lignes enfants.</span><span class="sxs-lookup"><span data-stu-id="877fd-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="877fd-142">**Aucun**</span><span class="sxs-lookup"><span data-stu-id="877fd-142">**None**</span></span>|<span data-ttu-id="877fd-143">N'effectue aucune action sur les lignes enfants.</span><span class="sxs-lookup"><span data-stu-id="877fd-143">Take no action on child rows.</span></span> <span data-ttu-id="877fd-144">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="877fd-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="877fd-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="877fd-145">Example</span></span>  
 <span data-ttu-id="877fd-146">L'exemple suivant crée un objet <xref:System.Data.ForeignKeyConstraint>, définit plusieurs de ses propriétés, notamment la <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, et l'ajoute à la <xref:System.Data.ConstraintCollection> d'un objet <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="877fd-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="877fd-147">UniqueConstraint</span><span class="sxs-lookup"><span data-stu-id="877fd-147">UniqueConstraint</span></span>  
 <span data-ttu-id="877fd-148">Le **UniqueConstraint** objet, qui peut être assigné à une seule colonne ou à un tableau de colonnes dans un **DataTable**, garantit que toutes les données dans l’ou les colonnes spécifiées sont uniques pour chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="877fd-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="877fd-149">Vous pouvez créer une contrainte unique pour une colonne ou un tableau de colonnes à l’aide de la **UniqueConstraint** constructeur.</span><span class="sxs-lookup"><span data-stu-id="877fd-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="877fd-150">Passez résultant **UniqueConstraint** de l’objet à la **ajouter** (méthode) de la table **contraintes** propriété, qui est un **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="877fd-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="877fd-151">Vous pouvez également passer des arguments de constructeur à plusieurs surcharges de la **ajouter** méthode d’un **ConstraintCollection** pour créer un **UniqueConstraint**.</span><span class="sxs-lookup"><span data-stu-id="877fd-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="877fd-152">Lorsque vous créez un **UniqueConstraint** pour une ou plusieurs colonnes, vous pouvez éventuellement spécifier si l’ou les colonnes sont une clé primaire.</span><span class="sxs-lookup"><span data-stu-id="877fd-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="877fd-153">Vous pouvez également créer une contrainte unique pour une colonne en définissant le **Unique** propriété de la colonne à **true**.</span><span class="sxs-lookup"><span data-stu-id="877fd-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="877fd-154">Vous pouvez également définir le **Unique** propriété d’une seule colonne à **false** supprime toute contrainte qui peut-être exister.</span><span class="sxs-lookup"><span data-stu-id="877fd-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="877fd-155">Lorsque vous définissez une ou plusieurs colonnes comme clé primaire d'une table, une contrainte unique est automatiquement créée pour les colonnes spécifiées.</span><span class="sxs-lookup"><span data-stu-id="877fd-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="877fd-156">Si vous supprimez une colonne à partir de la **PrimaryKey** propriété d’un **DataTable**, le **UniqueConstraint** est supprimé.</span><span class="sxs-lookup"><span data-stu-id="877fd-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="877fd-157">L’exemple suivant crée un **UniqueConstraint** pour deux colonnes d’une **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="877fd-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]   
    {custTable.Columns["CustomerID"],   
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a><span data-ttu-id="877fd-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="877fd-158">See Also</span></span>  
 <xref:System.Data.DataRelation>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.ForeignKeyConstraint>  
 <xref:System.Data.UniqueConstraint>  
 [<span data-ttu-id="877fd-159">Définition de schéma de DataTable</span><span class="sxs-lookup"><span data-stu-id="877fd-159">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="877fd-160">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="877fd-160">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="877fd-161">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="877fd-161">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
