---
title: DataTables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3803d550fe345c6f485dd204cc119f8a927a3501
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="datatables"></a>DataTables
Un objet <xref:System.Data.DataSet> est constitué d'une collection de tables, de relations et de contraintes. Dans ADO.NET, <xref:System.Data.DataTable> objets sont utilisés pour représenter les tables dans un **DataSet**. A **DataTable** représente une table de données relationnelles de la mémoire ; les données seront locales pour le. Application basée sur le réseau dans lequel il réside, mais peut être rempli à partir d’une source de données telles que Microsoft SQL Server à l’aide un **DataAdapter** pour plus d’informations, consultez [remplissage d’un DataSet à partir d’un DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) .  
  
 Le **DataTable** classe est un membre de la **System.Data** espace de noms dans la bibliothèque de classes .NET Framework. Vous pouvez créer et utiliser un **DataTable** indépendamment ou en tant que membre d’un **DataSet**, et **DataTable** objets peuvent également être utilisés conjointement avec d’autres objets .NET Framework, y compris le <xref:System.Data.DataView>. Accéder à la collection de tables dans un **DataSet** via la **Tables** propriété de la **DataSet** objet.  
  
 Le schéma, ou structure, d'une table est représenté par des colonnes et des contraintes. Vous définissez le schéma d’un **DataTable** à l’aide de <xref:System.Data.DataColumn> objets ainsi que <xref:System.Data.ForeignKeyConstraint> et <xref:System.Data.UniqueConstraint> objets. Les colonnes d'une table peuvent mapper aux colonnes d'une source de données. Elles contiennent des valeurs calculées à partir d'expressions, incrémentent automatiquement leurs valeurs ou contiennent des valeurs de clé primaire.  
  
 Outre un schéma, un **DataTable** doit également avoir des lignes pour contenir et trier les données. La classe <xref:System.Data.DataRow> représente les données en cours contenues dans une table. Vous utilisez la **DataRow** et ses propriétés et méthodes pour extraire, évaluer et manipuler les données dans une table. Comme vous accéder et modifier les données dans une ligne, la **DataRow** objet conserve son état d’origine et actuelle.  
  
 Vous pouvez créer des relations parent-enfant entre des tables à l'aide d'une ou plusieurs colonnes connexes de ces tables. Vous créez une relation entre **DataTable** à l’aide des objets un <xref:System.Data.DataRelation>. **DataRelation** objets peuvent ensuite être utilisés pour retourner les lignes connexes enfants ou parentes d’une ligne particulière. Pour plus d’informations, consultez [Ajout de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Création d’un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 Explique comment créer un **DataTable** et ajoutez-le à un **DataSet**.  
  
 [Définition de schéma de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 Fournit des informations sur la création et à l’aide de **DataColumn** contraintes et objets.  
  
 [Manipulation des données dans un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 Explique comment ajouter, modifier et supprimer des données dans une table. Explique comment utiliser **DataTable** événements pour examiner les modifications apportées aux données dans la table.  
  
 [Gestion des événements de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 Fournit des informations sur les événements disponibles pour une utilisation avec un **DataTable**, y compris les événements lorsque les valeurs de colonne sont modifiées et les lignes sont ajoutées ou supprimées.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 Décrit l'architecture et les composants d'ADO.NET ainsi que la façon de les utiliser pour accéder à des sources de données existantes et pour gérer des données d'application.  
  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Fournit des informations sur l’ADO.NET **DataSet** , notamment comment créer des relations entre les tables.  
  
 <xref:System.Data.Constraint>  
 Fournit des informations de référence sur les **contrainte** objet.  
  
 <xref:System.Data.DataColumn>  
 Fournit des informations de référence sur les **DataColumn** objet.  
  
 <xref:System.Data.DataSet>  
 Fournit des informations de référence sur les **DataSet** objet.  
  
 <xref:System.Data.DataTable>  
 Fournit des informations de référence sur les **DataTable** objet.  
  
 [Présentation des bibliothèques de classes .NET](../../../../../docs/standard/class-library-overview.md)  
 Fournit une vue d’ensemble de la bibliothèque de classes .NET Framework, y compris le **système** espace de noms, ainsi que son espace de noms de deuxième niveau, **System.Data**.  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
