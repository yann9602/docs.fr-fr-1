---
title: Ajout de DataRelations
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
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31494ee9ac6fc8efc9a041f5d56dbba4a4bddad1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="adding-datarelations"></a><span data-ttu-id="d5190-102">Ajout de DataRelations</span><span class="sxs-lookup"><span data-stu-id="d5190-102">Adding DataRelations</span></span>
<span data-ttu-id="d5190-103">Dans un objet <xref:System.Data.DataSet> contenant plusieurs objets <xref:System.Data.DataTable>, vous pouvez utiliser des objets <xref:System.Data.DataRelation> pour associer une table à une autre, pour vous déplacer dans les tables et pour retourner les lignes enfants ou parentes d'une table associée.</span><span class="sxs-lookup"><span data-stu-id="d5190-103">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="d5190-104">Les arguments requis pour créer un **DataRelation** sont un nom pour le **DataRelation** est créé et un tableau d’un ou plusieurs <xref:System.Data.DataColumn> références aux colonnes de servir de parent et enfant colonnes dans la relation.</span><span class="sxs-lookup"><span data-stu-id="d5190-104">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="d5190-105">Après avoir créé un **DataRelation**, vous pouvez l’utiliser pour naviguer entre les tables et de récupérer des valeurs.</span><span class="sxs-lookup"><span data-stu-id="d5190-105">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="d5190-106">Ajout d’un **DataRelation** à un <xref:System.Data.DataSet> ajoute par défaut, un <xref:System.Data.UniqueConstraint> à la table parente et une <xref:System.Data.ForeignKeyConstraint> à la table enfant.</span><span class="sxs-lookup"><span data-stu-id="d5190-106">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="d5190-107">Pour plus d’informations sur ces contraintes par défaut, consultez [contraintes DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="d5190-107">For more information about these default constraints, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="d5190-108">L’exemple de code suivant crée un **DataRelation** à l’aide de deux <xref:System.Data.DataTable> des objets dans un <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="d5190-108">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="d5190-109">Chaque <xref:System.Data.DataTable> contient une colonne nommée **CustID**, qui sert de lien entre les deux <xref:System.Data.DataTable> objets.</span><span class="sxs-lookup"><span data-stu-id="d5190-109">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="d5190-110">L’exemple ajoute un seul **DataRelation** à la **Relations** collection de la <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="d5190-110">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="d5190-111">Le premier argument dans l’exemple spécifie le nom de la **DataRelation** en cours de création.</span><span class="sxs-lookup"><span data-stu-id="d5190-111">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="d5190-112">Le deuxième argument définit le parent **DataColumn** et le troisième argument définit l’enfant **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="d5190-112">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 <span data-ttu-id="d5190-113">A **DataRelation** a également un **Nested** propriété qui, lorsque la valeur **true**, imbrique les lignes de la table enfant dans la ligne associée de la table parente lors de l’écriture en tant qu’éléments XML à l’aide de <xref:System.Data.DataSet.WriteXml%2A> .</span><span class="sxs-lookup"><span data-stu-id="d5190-113">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="d5190-114">Pour plus d’informations, consultez [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="d5190-114">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5190-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5190-115">See Also</span></span>  
 [<span data-ttu-id="d5190-116">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="d5190-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="d5190-117">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="d5190-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
