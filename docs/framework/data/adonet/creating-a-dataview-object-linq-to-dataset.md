---
title: "Création d'un objet DataView (LINQ to DataSet)"
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
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4363e4e4e444a2c34b79e3b3ad8d8e2f36fe8e1a
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2017
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a>Création d'un objet DataView (LINQ to DataSet)
Il existe deux manières de créer un <xref:System.Data.DataView> dans le contexte de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Vous pouvez créer un <xref:System.Data.DataView> à partir d'une requête [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sur une <xref:System.Data.DataTable>, ou vous pouvez la créer à partir d'une <xref:System.Data.DataTable> typée ou non typée. Dans les deux cas, vous créez le <xref:System.Data.DataView> en utilisant l’une de le <xref:System.Data.DataTableExtensions.AsDataView%2A> les méthodes d’extension ; <xref:System.Data.DataView> n’est pas être construit directement dans le [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] contexte.  
  
 Une fois le <xref:System.Data.DataView> créé, vous pouvez le lier à un contrôle d'interface utilisateur dans une application Windows Forms ou ASP.NET, ou modifier les paramètres de filtrage et de tri.  
  
 <xref:System.Data.DataView> construit un index, ce qui augmente considérablement les performances des applications qui utilisent l'index, telles que le filtrage et le tri. L'index d'un <xref:System.Data.DataView> est construit à la fois lors de la création du <xref:System.Data.DataView> et lorsque l'une des informations de tri ou de filtrage est modifiée. La création d'un <xref:System.Data.DataView>, suivie de la définition des informations de tri et de filtrage, entraîne la construction de l'index deux fois au moins : une fois lors de la création du <xref:System.Data.DataView>, puis à nouveau lorsqu'une des propriétés de tri ou de filtrage est modifiée.  
  
 Pour plus d’informations sur le filtrage et tri avec <xref:System.Data.DataView>, consultez [filtrage avec DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) et [tri avec DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a>Création d'un DataView à partir d'une requête LINQ to DataSet  
 Un objet <xref:System.Data.DataView> peut être créé à partir des résultats d'une requête [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] où les résultats sont une projection d'objets <xref:System.Data.DataRow>. L'objet <xref:System.Data.DataView> nouvellement créé hérite des informations de filtrage et de tri de la requête à partir de laquelle il a été créé.  
  
> [!NOTE]
>  Dans la plupart des cas, les expressions utilisées pour le filtrage et le tri ne doivent pas avoir d'effets secondaires et doivent être déterministes. De plus, les expressions ne doivent pas contenir de logique dépendant d'un nombre défini d'exécutions, étant donné que les opérations de tri et de filtrage doivent pouvoir être exécutées de façon illimitée.  
  
 La création d'un <xref:System.Data.DataView> à partir d'une requête qui retourne des types anonymes ou des requêtes qui effectuent des opérations de jointure n'est pas prise en charge.  
  
 Seuls les opérateurs de requête ci-dessous sont pris en charge dans une requête utilisée pour créer un <xref:System.Data.DataView> :  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 Notez que, lorsqu'un objet <xref:System.Data.DataView> est créé à partir d'une requête [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], la méthode <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> doit être la dernière méthode appelée dans la requête. Ceci est illustré dans l’exemple suivant, qui crée un <xref:System.Data.DataView> de commandes en ligne triées par montant total dû :  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 Vous pouvez également utiliser basé sur la chaîne <xref:System.Data.DataView.RowFilter%2A> et <xref:System.Data.DataView.Sort%2A> propriétés à filtrer et trier un <xref:System.Data.DataView> après qu’il a été créé à partir d’une requête. Notez que cela entraîne la suppression des informations de tri et de filtrage héritées de la requête. L'exemple suivant crée un <xref:System.Data.DataView> à partir d'une requête [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] qui filtre par noms commençant par la lettre 'S'. La propriété <xref:System.Data.DataView.Sort%2A> basée sur chaîne est définie pour un tri sur le nom par ordre croissant et sur le prénom par ordre décroissant :  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a>Création d'un DataView à partir d'un DataTable  
 Outre créé à partir d’un [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] requête, un <xref:System.Data.DataView> objet peut être créé à partir d’un <xref:System.Data.DataTable> à l’aide de la <xref:System.Data.DataTableExtensions.AsDataView%2A> (méthode).  
  
 L'exemple ci-dessous crée un <xref:System.Data.DataView> à partir de la table SalesOrderDetail et le définit comme source de données d'un objet <xref:System.Windows.Forms.BindingSource>. Cet objet agit comme un proxy pour un contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 Le filtrage et le tri peuvent être définis sur le <xref:System.Data.DataView> après qu'il a été créé à partir d'un <xref:System.Data.DataTable>. L'exemple suivant crée une table <xref:System.Data.DataView> à partir de la table Contact et définit la propriété <xref:System.Data.DataView.Sort%2A> pour trier les noms par ordre croissant et les prénoms par ordre décroissant :  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 Cependant, on constate une baisse de performance lorsqu'on définit la propriété <xref:System.Data.DataView.RowFilter%2A> ou <xref:System.Data.DataView.Sort%2A> après la création du <xref:System.Data.DataView> à partir d'une requête, parce que le <xref:System.Data.DataView> construit un index pour prendre en charge les opérations de filtrage et de tri. Le paramétrage de la propriété <xref:System.Data.DataView.RowFilter%2A> ou <xref:System.Data.DataView.Sort%2A> entraîne une nouvelle génération de l'index des données, ce qui accroît la charge pour votre application et, par voie de conséquence, fait baisser les performances. Dans la mesure du possible, il est préférable de spécifier les informations de filtrage et de tri dès la création du <xref:System.Data.DataView> et d'éviter de les modifier par la suite.  
  
## <a name="see-also"></a>Voir aussi  
 [Liaison de données et LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 [Filtrage avec DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 [Tri avec DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
