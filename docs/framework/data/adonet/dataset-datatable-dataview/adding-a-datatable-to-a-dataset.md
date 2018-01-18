---
title: "Ajout d'un nouveau DataTable à un DataSet"
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
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6b72727ac42691b510e52370c937fa40baf6c006
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="adding-a-datatable-to-a-dataset"></a><span data-ttu-id="f50ed-102">Ajout d'un nouveau DataTable à un DataSet</span><span class="sxs-lookup"><span data-stu-id="f50ed-102">Adding a DataTable to a DataSet</span></span>
<span data-ttu-id="f50ed-103">ADO.NET vous permet de créer des objets <xref:System.Data.DataTable> et de les ajouter à un objet <xref:System.Data.DataSet> existant.</span><span class="sxs-lookup"><span data-stu-id="f50ed-103">ADO.NET enables you to create <xref:System.Data.DataTable> objects and add them to an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f50ed-104">Vous pouvez définir des informations de contrainte pour un objet <xref:System.Data.DataTable> en utilisant les propriétés <xref:System.Data.DataTable.PrimaryKey%2A> et <xref:System.Data.DataColumn.Unique%2A>.</span><span class="sxs-lookup"><span data-stu-id="f50ed-104">You can set constraint information for a <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.PrimaryKey%2A> and <xref:System.Data.DataColumn.Unique%2A> properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f50ed-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="f50ed-105">Example</span></span>  
 <span data-ttu-id="f50ed-106">L'exemple suivant construit un objet <xref:System.Data.DataSet>, ajoute un nouvel objet <xref:System.Data.DataTable> à l'objet <xref:System.Data.DataSet>, puis ajoute trois objets <xref:System.Data.DataColumn> à la table.</span><span class="sxs-lookup"><span data-stu-id="f50ed-106">The following example constructs a <xref:System.Data.DataSet>, adds a new <xref:System.Data.DataTable> object to the <xref:System.Data.DataSet>, and then adds three <xref:System.Data.DataColumn> objects to the table.</span></span> <span data-ttu-id="f50ed-107">Enfin, ce code définit une colonne en tant que colonne clé primaire.</span><span class="sxs-lookup"><span data-stu-id="f50ed-107">Finally, the code sets one column as the primary key column.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a><span data-ttu-id="f50ed-108">Respect de la casse</span><span class="sxs-lookup"><span data-stu-id="f50ed-108">Case Sensitivity</span></span>  
 <span data-ttu-id="f50ed-109">Un objet <xref:System.Data.DataSet> peut contenir plusieurs tables ou relations dont les noms ne diffèrent que par la casse.</span><span class="sxs-lookup"><span data-stu-id="f50ed-109">Two or more tables or relations with the same name, but different casing, can exist in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f50ed-110">Dans ces cas, les références par nom aux tables et relations respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="f50ed-110">In such cases, references by name to tables and relations are case sensitive.</span></span> <span data-ttu-id="f50ed-111">Par exemple, si le <xref:System.Data.DataSet> **dataSet** contient des tables **Table1** et **table1**, vous devez référencer **Table1** par nom en tant que **dataSet.Tables["Table1 »]**, et **table1** en tant que **dataSet.Tables["table1 »]**.</span><span class="sxs-lookup"><span data-stu-id="f50ed-111">For example, if the <xref:System.Data.DataSet> **dataSet** contains tables **Table1** and **table1**, you would reference **Table1** by name as **dataSet.Tables["Table1"]**, and **table1** as **dataSet.Tables["table1"]**.</span></span> <span data-ttu-id="f50ed-112">Tentative de référencer une des tables comme **dataSet.Tables["TABLE1 »]** génèrent une exception.</span><span class="sxs-lookup"><span data-stu-id="f50ed-112">Attempting to reference either of the tables as **dataSet.Tables["TABLE1"]** would generate an exception.</span></span>  
  
 <span data-ttu-id="f50ed-113">Le comportement de respect de la casse ne s'applique pas s'il n'existe qu'une seule table ou relation ayant un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="f50ed-113">The case-sensitivity behavior does not apply if only one table or relation has a particular name.</span></span> <span data-ttu-id="f50ed-114">Par exemple, si le <xref:System.Data.DataSet> a uniquement **Table1**, vous pouvez faire référence à l’aide de **dataSet.Tables["TABLE1 »]**.</span><span class="sxs-lookup"><span data-stu-id="f50ed-114">For example, if the <xref:System.Data.DataSet> has only **Table1**, you can reference it using **dataSet.Tables["TABLE1"]**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f50ed-115">La propriété <xref:System.Data.DataSet.CaseSensitive%2A> de l'objet <xref:System.Data.DataSet> n'affecte pas ce comportement.</span><span class="sxs-lookup"><span data-stu-id="f50ed-115">The <xref:System.Data.DataSet.CaseSensitive%2A> property of the <xref:System.Data.DataSet> does not affect this behavior.</span></span> <span data-ttu-id="f50ed-116">La propriété <xref:System.Data.DataSet.CaseSensitive%2A> s'applique aux données de l'objet <xref:System.Data.DataSet> et affecte les contraintes de tri, de recherche, de filtrage, d'application, etc.</span><span class="sxs-lookup"><span data-stu-id="f50ed-116">The <xref:System.Data.DataSet.CaseSensitive%2A> property applies to the data in the <xref:System.Data.DataSet> and affects sorting, searching, filtering, enforcing constraints, and so on.</span></span>  
  
## <a name="namespace-support"></a><span data-ttu-id="f50ed-117">Prise en charge des espaces de noms</span><span class="sxs-lookup"><span data-stu-id="f50ed-117">Namespace Support</span></span>  
 <span data-ttu-id="f50ed-118">Dans les versions d'ADO.NET antérieures à 2.0, deux tables ne pouvaient pas porter le même nom, même si elles se trouvaient dans des espaces de noms différents.</span><span class="sxs-lookup"><span data-stu-id="f50ed-118">In versions of ADO.NET earlier than 2.0, two tables could not have the same name, even if they were in different namespaces.</span></span> <span data-ttu-id="f50ed-119">Cette limite a été supprimée dans ADO.NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="f50ed-119">This limitation was removed in ADO.NET 2.0.</span></span> <span data-ttu-id="f50ed-120">Un objet <xref:System.Data.DataSet> peut contenir deux tables avec la même valeur de propriété <xref:System.Data.DataTable.TableName%2A> mais des valeurs de propriété <xref:System.Data.DataTable.Namespace%2A> différentes.</span><span class="sxs-lookup"><span data-stu-id="f50ed-120">A <xref:System.Data.DataSet> can contain two tables that have the same <xref:System.Data.DataTable.TableName%2A> property value but different <xref:System.Data.DataTable.Namespace%2A> property values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f50ed-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f50ed-121">See Also</span></span>  
 [<span data-ttu-id="f50ed-122">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="f50ed-122">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="f50ed-123">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="f50ed-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
