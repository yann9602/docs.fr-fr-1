---
title: Interrogation de la collection DataRowView dans un DataView
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
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b17a489552e7b2bcb6044fce99e5f526b8293a25
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a><span data-ttu-id="a838a-102">Interrogation de la collection DataRowView dans un DataView</span><span class="sxs-lookup"><span data-stu-id="a838a-102">Querying the DataRowView Collection in a DataView</span></span>
<span data-ttu-id="a838a-103">L'objet <xref:System.Data.DataView> expose une collection énumérable d'objets <xref:System.Data.DataRowView>.</span><span class="sxs-lookup"><span data-stu-id="a838a-103">The <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="a838a-104">L'objet <xref:System.Data.DataRowView> représente une vue personnalisée d'un objet <xref:System.Data.DataRow> et affiche une version spécifique de cet objet <xref:System.Data.DataRow> dans un contrôle.</span><span class="sxs-lookup"><span data-stu-id="a838a-104"><xref:System.Data.DataRowView> represents a customized view of a <xref:System.Data.DataRow> and displays a specific version of that <xref:System.Data.DataRow> in a control.</span></span> <span data-ttu-id="a838a-105">Une seule version d'un objet <xref:System.Data.DataRow> peut être affichée par le biais d'un contrôle, comme un objet <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="a838a-105">Only one version of a <xref:System.Data.DataRow> can be displayed through a control, such as a <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="a838a-106">Vous pouvez accéder à l'objet <xref:System.Data.DataRow> qui est exposé par le <xref:System.Data.DataRowView> par le biais de la propriété <xref:System.Data.DataRowView.Row%2A> de l'objet <xref:System.Data.DataRowView>.</span><span class="sxs-lookup"><span data-stu-id="a838a-106">You can access the <xref:System.Data.DataRow> that is exposed by the <xref:System.Data.DataRowView> through the <xref:System.Data.DataRowView.Row%2A> property of the <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="a838a-107">Lorsque vous affichez des valeurs à l'aide d'un <xref:System.Data.DataRowView>, la propriété <xref:System.Data.DataView.RowStateFilter%2A> détermine la version de ligne de l'objet <xref:System.Data.DataRow> sous-jacent qui est exposée.</span><span class="sxs-lookup"><span data-stu-id="a838a-107">When you view values by using a <xref:System.Data.DataRowView>, the <xref:System.Data.DataView.RowStateFilter%2A> property determines which row version of the underlying <xref:System.Data.DataRow> is exposed.</span></span> <span data-ttu-id="a838a-108">Pour plus d’informations sur les différentes versions de ligne à l’aide de l’accès à un <xref:System.Data.DataRow>, consultez [état des lignes et des Versions de ligne](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="a838a-108">For information about accessing different row versions using a <xref:System.Data.DataRow>, see [Row States and Row Versions](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span> <span data-ttu-id="a838a-109">Étant donné que la collection de <xref:System.Data.DataRowView> objets exposés par le <xref:System.Data.DataView> est dénombrable, vous pouvez utiliser [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] pour l’interroger.</span><span class="sxs-lookup"><span data-stu-id="a838a-109">Because the collection of <xref:System.Data.DataRowView> objects exposed by the <xref:System.Data.DataView> is enumerable, you can use [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to query over it.</span></span>  
  
 <span data-ttu-id="a838a-110">L'exemple suivant recherche les produits de couleur rouge dans la table `Product` et crée une table à partir de cette requête.</span><span class="sxs-lookup"><span data-stu-id="a838a-110">The following example queries the `Product` table for red-colored products and creates a table from that query.</span></span> <span data-ttu-id="a838a-111">Un objet <xref:System.Data.DataView> est créé à partir de cette table et la propriété <xref:System.Data.DataView.RowStateFilter%2A> est définie pour filtrer sur les lignes supprimées et modifiées.</span><span class="sxs-lookup"><span data-stu-id="a838a-111">A <xref:System.Data.DataView> is created from the table and the <xref:System.Data.DataView.RowStateFilter%2A> property is set to filter on deleted and modified rows.</span></span> <span data-ttu-id="a838a-112">L'objet <xref:System.Data.DataView> est ensuite utilisé comme source dans une requête LINQ, et les objets <xref:System.Data.DataRowView> qui ont été modifiés et supprimés sont liés à un contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="a838a-112">The <xref:System.Data.DataView> is then used as a source in a LINQ query, and the <xref:System.Data.DataRowView> objects that have been modified and deleted are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 <span data-ttu-id="a838a-113">L'exemple suivant crée une table de produits à partir d'une vue qui est liée à un contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="a838a-113">The following example creates a table of products from a view that is bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="a838a-114">Une requête recherche les produits de couleur rouge dans l'objet <xref:System.Data.DataView> et les résultats classés sont liés à un contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="a838a-114">The <xref:System.Data.DataView> is queried for red-colored products and the ordered results are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a><span data-ttu-id="a838a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a838a-115">See Also</span></span>  
 [<span data-ttu-id="a838a-116">Liaison de données et LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="a838a-116">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
