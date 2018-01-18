---
title: Datasets ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b9d566f99802ea80ae73132579bb3068b1ff3b28
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="adonet-datasets"></a>Datasets ADO.NET
L'objet <xref:System.Data.DataSet> est l'élément central pour la prise en charge de scénarios impliquant des données distribuées et déconnectées avec [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Le **DataSet** est une représentation résidente en mémoire de données qui fournit un modèle de programmation relationnel cohérent, quelle que soit la source de données. Il peut être utilisé avec plusieurs sources de données différentes, utilisé avec des données XML ou utilisé pour gérer des données locales de l'application. Le **DataSet** représente un jeu complet de données, y compris les tables associées, des contraintes et des relations entre les tables. L’illustration suivante montre le **DataSet** modèle objet.  
  
 ![Graphique ADO.Net](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Modèle d'objet DataSet  
  
 Les méthodes et les objets dans une **DataSet** sont cohérents avec ceux du modèle de base de données relationnelle.  
  
 Le **DataSet** peut également persister et recharger son contenu en tant que XML et son schéma en tant que schéma XML schema definition language (XSD). Pour plus d’informations, consultez [Utilisation de XML dans un DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="the-datatablecollection"></a>DataTableCollection  
 Un [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] **DataSet** contient une collection de zéro ou plusieurs tables représentées par <xref:System.Data.DataTable> objets. Le <xref:System.Data.DataTableCollection> contient tous les le **DataTable** des objets dans une **DataSet**.  
  
 A **DataTable** est défini dans le <xref:System.Data> espace de noms et représente une seule table de données résidentes en mémoire. Il contient une collection de colonnes, représentées par un <xref:System.Data.DataColumnCollection> et des contraintes représentées par un <xref:System.Data.ConstraintCollection>, qui ensemble définissent le schéma de la table. A **DataTable** contient également une collection de lignes représentées par le <xref:System.Data.DataRowCollection>, qui contient les données de la table. En plus de son état actuel, un <xref:System.Data.DataRow> conserve ses versions d'origine et actuelle afin de permettre l'identification des modifications apportées aux valeurs stockées dans la ligne.  
  
## <a name="the-dataview-class"></a>Classe DataView  
 Un objet <xref:System.Data.DataView> vous permet de créer différentes vues des données stockées dans un objet <xref:System.Data.DataTable>, possibilité qui est souvent utilisée dans les applications de liaison de données. En utilisant un <xref:System.Data.DataView>, vous pouvez présenter les données d'une table en appliquant différents ordres de tri et filtrer les données en fonction d'un état de ligne ou d'une expression de filtre. Pour plus d’informations, consultez [DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 A **DataSet** contient des relations dans son <xref:System.Data.DataRelationCollection> objet. Une relation, représentée par le <xref:System.Data.DataRelation> associe les lignes d’un objet **DataTable** avec des lignes dans une autre **DataTable**. Une relation est similaire à une jointure qui peut exister entre les colonnes clé primaire et clé étrangère dans une base de données relationnelle. A **DataRelation** identifie les colonnes identiques dans deux tables d’un **DataSet**.  
  
 Les relations permettent la navigation entre une table à l’autre dans un **DataSet**. Les éléments essentiels d’une **DataRelation** sont le nom de la relation, le nom des tables mises en relation et les colonnes connexes dans chaque table. Une relation peut être générée avec plusieurs colonnes par table en spécifiant un tableau d'objets <xref:System.Data.DataColumn> en tant que colonnes clés. Lorsque vous ajoutez une relation à la <xref:System.Data.DataRelationCollection>, vous pouvez éventuellement ajouter un **UniqueKeyConstraint** et un **ForeignKeyConstraint** pour appliquer des contraintes d’intégrité lorsque des modifications sont apportées à la colonne associée valeurs.  
  
 Pour plus d’informations, consultez [Ajout de DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>XML  
 Vous pouvez remplir un **DataSet** à partir d’un document ou flux XML. Vous pouvez utiliser le flux ou document XML pour fournir à la **DataSet** données, les informations de schéma ou les deux. Les informations fournies à partir du flux ou document XML peuvent être combinées aux données ou aux informations de schéma déjà présentes dans le **DataSet**. Pour plus d’informations, consultez [Utilisation de XML dans un DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 Le **DataSet**, **DataTable**, et **DataColumn** ont tous un **ExtendedProperties** propriété. **ExtendedProperties** est un **PropertyCollection** dans lequel vous pouvez placer des informations personnalisées, telles que l’instruction SELECT qui a été utilisée pour générer le jeu de résultats, ou l’heure à laquelle les données a été générées. Le **ExtendedProperties** collection est rendue persistante avec les informations de schéma pour le **DataSet**.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] fournit les fonctionnalités LINQ (Language Integrated Query) pour traiter les données déconnectées stockées dans un DataSet. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]utilise la norme [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] syntaxe et fournit la vérification de la syntaxe de la compilation, les types statiques et prise en charge IntelliSense lorsque vous utilisez la [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] IDE.  
  
 Pour plus d’informations, [consultez LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble d’ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [DataSets, DataTables et DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
