---
title: "Création de colonnes AutoIncrement"
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
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7bc71e3ae817bbdaf5dc14f22041e297cab949b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="85d70-102">Création de colonnes AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="85d70-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="85d70-103">Pour garantir que les valeurs de colonne sont uniques, vous pouvez les définir de sorte qu'elles s'incrémentent automatiquement lors de l'ajout de lignes à la table.</span><span class="sxs-lookup"><span data-stu-id="85d70-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="85d70-104">Pour créer un auto-incrémentée <xref:System.Data.DataColumn>, définissez le <xref:System.Data.DataColumn.AutoIncrement%2A> propriété de la colonne à **true**.</span><span class="sxs-lookup"><span data-stu-id="85d70-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="85d70-105">Le <xref:System.Data.DataColumn> commence alors avec la valeur définie dans le <xref:System.Data.DataColumn.AutoIncrementSeed%2A> propriété et à chaque ligne ajoutée à la valeur de la **AutoIncrement** colonne augmente la valeur définie dans le <xref:System.Data.DataColumn.AutoIncrementStep%2A> propriété de la colonne.</span><span class="sxs-lookup"><span data-stu-id="85d70-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="85d70-106">Pour **AutoIncrement** colonnes, nous vous recommandons la <xref:System.Data.DataColumn.ReadOnly%2A> propriété de la **DataColumn** avoir la valeur **true**.</span><span class="sxs-lookup"><span data-stu-id="85d70-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="85d70-107">L'exemple suivant montre comment créer une colonne commençant par la valeur 200, avec une incrémentation par pas de 3.</span><span class="sxs-lookup"><span data-stu-id="85d70-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a><span data-ttu-id="85d70-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85d70-108">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 [<span data-ttu-id="85d70-109">Définition de schéma d’un DataTable</span><span class="sxs-lookup"><span data-stu-id="85d70-109">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="85d70-110">DataTables</span><span class="sxs-lookup"><span data-stu-id="85d70-110">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="85d70-111">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="85d70-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
