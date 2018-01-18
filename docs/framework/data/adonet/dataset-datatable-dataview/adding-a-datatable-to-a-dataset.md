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
# <a name="adding-a-datatable-to-a-dataset"></a>Ajout d'un nouveau DataTable à un DataSet
ADO.NET vous permet de créer des objets <xref:System.Data.DataTable> et de les ajouter à un objet <xref:System.Data.DataSet> existant. Vous pouvez définir des informations de contrainte pour un objet <xref:System.Data.DataTable> en utilisant les propriétés <xref:System.Data.DataTable.PrimaryKey%2A> et <xref:System.Data.DataColumn.Unique%2A>.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant construit un objet <xref:System.Data.DataSet>, ajoute un nouvel objet <xref:System.Data.DataTable> à l'objet <xref:System.Data.DataSet>, puis ajoute trois objets <xref:System.Data.DataColumn> à la table. Enfin, ce code définit une colonne en tant que colonne clé primaire.  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>Respect de la casse  
 Un objet <xref:System.Data.DataSet> peut contenir plusieurs tables ou relations dont les noms ne diffèrent que par la casse. Dans ces cas, les références par nom aux tables et relations respectent la casse. Par exemple, si le <xref:System.Data.DataSet> **dataSet** contient des tables **Table1** et **table1**, vous devez référencer **Table1** par nom en tant que **dataSet.Tables["Table1 »]**, et **table1** en tant que **dataSet.Tables["table1 »]**. Tentative de référencer une des tables comme **dataSet.Tables["TABLE1 »]** génèrent une exception.  
  
 Le comportement de respect de la casse ne s'applique pas s'il n'existe qu'une seule table ou relation ayant un nom particulier. Par exemple, si le <xref:System.Data.DataSet> a uniquement **Table1**, vous pouvez faire référence à l’aide de **dataSet.Tables["TABLE1 »]**.  
  
> [!NOTE]
>  La propriété <xref:System.Data.DataSet.CaseSensitive%2A> de l'objet <xref:System.Data.DataSet> n'affecte pas ce comportement. La propriété <xref:System.Data.DataSet.CaseSensitive%2A> s'applique aux données de l'objet <xref:System.Data.DataSet> et affecte les contraintes de tri, de recherche, de filtrage, d'application, etc.  
  
## <a name="namespace-support"></a>Prise en charge des espaces de noms  
 Dans les versions d'ADO.NET antérieures à 2.0, deux tables ne pouvaient pas porter le même nom, même si elles se trouvaient dans des espaces de noms différents. Cette limite a été supprimée dans ADO.NET 2.0. Un objet <xref:System.Data.DataSet> peut contenir deux tables avec la même valeur de propriété <xref:System.Data.DataTable.TableName%2A> mais des valeurs de propriété <xref:System.Data.DataTable.Namespace%2A> différentes.  
  
## <a name="see-also"></a>Voir aussi  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
