---
title: DataSets, DataTables et DataViews
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fb8cf2c9f763ea32bb7c7907111fea80e542a7f7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="datasets-datatables-and-dataviews"></a>DataSets, DataTables et DataViews
L'objet <xref:System.Data.DataSet> ADO.NET est une représentation de données résidente en mémoire qui propose un modèle de programmation relationnel cohérent, quelle que soit la source des données qu'il contient. Un objet <xref:System.Data.DataSet> représente un jeu de données complet, y compris les tables qui contiennent et organisent les données et y appliquent des contraintes, ainsi que les relations entre les tables.  
  
 L'utilisation d'un objet <xref:System.Data.DataSet> peut se faire via différentes méthodes qui peuvent être appliquées indépendamment les unes des autres ou combinées. Vous pouvez :  
  
-   Créer par programmation un objet <xref:System.Data.DataTable>, <xref:System.Data.DataRelation> et <xref:System.Data.Constraint> dans un objet <xref:System.Data.DataSet>, puis remplir les tables de données.  
  
-   Remplir l'objet <xref:System.Data.DataSet> de tables de données provenant d'une source de données relationnelles existante à l'aide d'un objet `DataAdapter`.  
  
-   Charger et rendre persistent le contenu de l'objet <xref:System.Data.DataSet> à l'aide de XML. Pour plus d’informations, consultez [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
 Un objet <xref:System.Data.DataSet> fortement typé peut aussi être transporté au moyen d'un service Web XML. Le design de l'objet <xref:System.Data.DataSet> le rend idéal pour le transport de données à l'aide des services Web XML. Pour une vue d’ensemble des services web XML, consultez [Vue d’ensemble des services web XML](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d). Pour obtenir un exemple d’utilisation d’un <xref:System.Data.DataSet> à partir d’un service web XML, consultez [Consommation d’un DataSet à partir d’un service web XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Création d’un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 Décrit la syntaxe permettant de créer une instance d'un objet <xref:System.Data.DataSet>.  
  
 [Ajout d’un DataTable à un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 Explique comment créer et ajouter des tables et des colonnes à un objet <xref:System.Data.DataSet>.  
  
 [Ajout de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 Explique comment créer des relations entre différentes tables d'un objet <xref:System.Data.DataSet>.  
  
 [Parcours des DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 Explique comment utiliser les relations entre différentes tables d'un objet <xref:System.Data.DataSet> afin de retourner les lignes enfants ou parentes d'une relation parent-enfant.  
  
 [Fusion de contenu de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 Décrit comment fusionner le contenu d'un tableau <xref:System.Data.DataSet>, <xref:System.Data.DataTable> ou <xref:System.Data.DataRow> dans un autre objet <xref:System.Data.DataSet>.  
  
 [Copie de contenu de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 Explique comment créer une copie d'un objet <xref:System.Data.DataSet> susceptible de contenir un schéma et des données spécifiées.  
  
 [Gestion des événements de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 Décrit les événements d'un objet <xref:System.Data.DataSet> et comment les utiliser.  
  
 [Datasets typés](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 Explique ce qu'est un objet <xref:System.Data.DataSet> typé et comment en créer un et l'utiliser.  
  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 Explique comment créer un objet <xref:System.Data.DataTable>, définir le schéma et manipuler les données.  
  
 [DataTableReaders](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 Explique comment créer et utiliser un <xref:System.Data.DataTableReader>.  
  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 Décrit la façon de créer et d'utiliser des `DataViews` et d'utiliser des événements <xref:System.Data.DataView>.  
  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Explique comment l'objet <xref:System.Data.DataSet> interagit avec XML en tant que source de données, notamment en ce qui concerne le chargement et la persistance du contenu d'un objet <xref:System.Data.DataSet> en tant que données XML.  
  
 [Consommation d’un DataSet à partir d’un service web XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 Explique comment créer un service Web XML qui utilise un <xref:System.Data.DataSet> pour le transport des données.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Nouveautés d’ADO.NET](../../../../../docs/framework/data/adonet/whats-new.md)  
 Introduit des fonctionnalités nouvelles dans ADO.NET.  
  
 [Vue d’ensemble d’ADO.NET](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 Propose une introduction à la conception et aux composants de la technologie ADO.NET.  
  
 [Remplissage d’un DataSet à partir d’un DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 Explique comment charger un **DataSet** avec des données provenant d’une source de données.  
  
 [Mise à jour de sources de données avec des DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 Explique comment répercuter à la source de données les modifications apportées aux données d’un **DataSet**.  
  
 [Ajout de contraintes existantes à un DataSet](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 Explique comment remplir un **DataSet** avec les informations de clé primaire d’une source de données.  
  
## <a name="see-also"></a>Voir aussi  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
