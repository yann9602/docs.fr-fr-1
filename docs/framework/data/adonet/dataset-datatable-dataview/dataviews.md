---
title: "DataViews | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataViews
Un objet <xref:System.Data.DataView> vous permet de créer différentes vues des données stockées dans un objet <xref:System.Data.DataTable>, possibilité qui est souvent utilisée dans les applications de liaison de données.  En utilisant un **DataView**, vous pouvez présenter les données d'une table en appliquant différents ordres de tri et filtrer les données en fonction d'un état de ligne ou d'une expression de filtre.  
  
 Un **DataView** fournit une vue dynamique des données du **DataTable**sous\-jacent : le contenu, le classement et l'appartenance reflètent les modifications à mesure qu'elles se produisent.  Ce comportement diffère de la méthode **Select** du **DataTable**, qui retourne un tableau <xref:System.Data.DataRow> depuis une table selon un filtre et\/ou un ordre de tri particulier : ce contenu reflète les modifications de la table sous\-jacente, mais son appartenance et son ordre de tri restent statiques.  Les fonctionnalités dynamiques du **DataView** le rendent idéal pour les applications de liaison de données.  
  
 Un **DataView** vous propose une vue dynamique d'un seul groupe de données, similaire à la vue de base de données, auquel vous pouvez appliquer différents critères de tri et de filtre.  Toutefois, à la différence d'une vue de base de données, un **DataView** ne peut pas être traité comme une table et ne peut pas fournir une vue de tables jointes.  Vous ne pouvez pas non plus exclure des colonnes si elles existent dans la table source, ou ajouter des colonnes, telles que des colonnes de calcul qui n'existent pas dans la table source.  
  
 Vous pouvez utiliser une propriété <xref:System.Data.DataView.DataViewManager%2A> pour gérer les paramètres de vue pour toutes les tables d'un **DataSet**.  Le **DataViewManager** vous fournit un moyen pratique de gérer les paramètres de vue par défaut pour chaque table.  Lorsque vous souhaitez lier un contrôle à plusieurs tables d'un **DataSet**, l'idéal consiste à établir une liaison avec un **DataViewManager**.  
  
## Dans cette section  
 [Création d'un DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 Explique comment créer un **DataView** pour un **DataTable**.  
  
 [Tri et filtrage de données](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 Explique comment définir les propriétés d'un **DataView** afin de retourner des sous\-ensembles de lignes de données en fonction de critères de filtre spécifiques ou de retourner des données selon un ordre de tri particulier.  
  
 [DataRows et DataRowViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 Explique comment accéder aux données exposées par le **DataView**.  
  
 [Recherche de lignes](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 Explique comment trouver une ligne particulière dans un **DataView**.  
  
 [Vues et relations enfants](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 Explique comment créer des vues de données à partir d'une relation parent\-enfant à l'aide d'un **DataView**.  
  
 [Modification des objets DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 Explique comment modifier les données du **DataTable** sous\-jacent via le **DataView** et activer ou désactiver les mises à jour.  
  
 [Gestion des événements DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 Explique comment utiliser l'événement **ListChanged** pour qu'une notification soit émise lorsque le contenu ou l'ordre d'un **DataView** est mis à jour.  
  
 [Gestion des objets DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 Explique comment utiliser un **DataViewManager** pour gérer les paramètres du **DataView** pour chaque table d'un **DataSet**.  
  
## Rubriques connexes  
 [ASP.NET Web Applications](http://msdn.microsoft.com/fr-fr/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 Propose des vues d'ensemble et des procédures détaillées qui vous aident, étape par étape, à créer des applications ASP.NET, des Web Forms et des services Web.  
  
 [Windows Applications](http://msdn.microsoft.com/fr-fr/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 Fournit des informations détaillées sur l'utilisation de Windows Forms et d'applications console.  
  
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Décrit l'objet **DataSet** et explique comment vous pouvez l'utiliser pour gérer des données d'application.  
  
 [DataTable, objets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 Décrit l'objet **DataTable** et explique comment vous pouvez l'utiliser pour qu'il gère des données d'application de façon autonome ou comme partie intégrante d'un **DataSet**.  
  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 Décrit l'architecture et les composants d'ADO.NET ainsi que la façon d'utiliser ADO.NET pour accéder à des sources de données existantes et gérer des données d'application.  
  
## Voir aussi  
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)