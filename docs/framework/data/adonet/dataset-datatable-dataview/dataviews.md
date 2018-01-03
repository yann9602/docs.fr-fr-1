---
title: DataViews
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 26fbae0474253dc9792a0290a36dd52044d148b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="dataviews"></a>DataViews
Un objet <xref:System.Data.DataView> vous permet de créer différentes vues des données stockées dans un objet <xref:System.Data.DataTable>, possibilité qui est souvent utilisée dans les applications de liaison de données. À l’aide un **DataView**, vous pouvez présenter les données dans une table avec différents ordres de tri et vous pouvez filtrer les données par état de ligne ou en fonction d’une expression de filtre.  
  
 A **DataView** fournit une vue dynamique des données dans l’objet sous-jacent **DataTable**: le contenu, de classement et l’appartenance reflètent les modifications qu’ils se produisent. Ce comportement diffère de la **sélectionnez** méthode de la **DataTable**, qui retourne un <xref:System.Data.DataRow> tableau à partir d’une table selon un ordre de tri et/ou de filtre particulier : thiscontent reflète les modifications apportées à la sous-jacente table, mais son appartenance et de tri restent statiques. Les fonctionnalités dynamiques de la **DataView** rendent idéal pour les applications de liaison de données.  
  
 A **DataView** vous offre une vue dynamique d’un jeu unique de données, similaire à une vue de base de données à laquelle vous pouvez appliquer différents de tri et de critères de filtrage. Contrairement à une vue de base de données, cependant, un **DataView** ne peut pas être traitée comme une table et ne peut pas fournir une vue de tables jointes. Vous ne pouvez pas non plus exclure des colonnes si elles existent dans la table source, ou ajouter des colonnes, telles que des colonnes de calcul qui n'existent pas dans la table source.  
  
 Vous pouvez utiliser un <xref:System.Data.DataView.DataViewManager%2A> pour gérer les paramètres de vue pour toutes les tables dans un **DataSet**. Le **DataViewManager** vous offre un moyen pratique de gérer les paramètres d’affichage par défaut pour chaque table. Lors de la liaison d’un contrôle à plusieurs tables d’un **DataSet**, la liaison à un **DataViewManager** est la solution idéale.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Création d’un DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 Décrit comment créer un **DataView** pour un **DataTable**.  
  
 [Tri et filtre de données](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 Décrit comment définir les propriétés d’un **DataView** pour retourner des sous-ensembles de lignes de données répondant à des critères filtre spécifique, ou pour retourner des données dans un ordre de tri particulier.  
  
 [DataRows et DataRowViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 Décrit comment accéder aux données exposées par le **DataView**.  
  
 [Recherche de lignes](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 Explique comment rechercher une ligne particulière dans une **DataView**.  
  
 [Vues et relations enfants](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 Décrit comment créer des vues de données à partir d’une relation parent-enfant à l’aide un **DataView**.  
  
 [Modification des DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 Décrit comment modifier les données sous-jacentes **DataTable** via la **DataView**, y compris l’activation ou désactivation des mises à jour.  
  
 [Gestion des événements de DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 Décrit comment utiliser le **ListChanged** événement pour recevoir une notification lorsque le contenu ou l’ordre d’un **DataView** est en cours de mise à jour.  
  
 [Gestion des DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 Décrit comment utiliser un **DataViewManager** pour gérer les **DataView** paramètres pour chaque table dans un **DataSet**.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Applications Web ASP.NET](http://msdn.microsoft.com/en-us/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 Propose des vues d'ensemble et des procédures détaillées qui vous aident, étape par étape, à créer des applications ASP.NET, des Web Forms et des services Web.  
  
 [Applications Windows](http://msdn.microsoft.com/en-us/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 Fournit des informations détaillées sur l'utilisation de Windows Forms et d'applications console.  
  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Décrit la **DataSet** objet et la façon dont vous pouvez l’utiliser pour gérer les données d’application.  
  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 Décrit la **DataTable** objet et la façon dont vous pouvez l’utiliser pour gérer les données de l’application autonome ou comme partie d’un **DataSet**.  
  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 Décrit l'architecture et les composants d'ADO.NET ainsi que la façon d'utiliser ADO.NET pour accéder à des sources de données existantes et gérer des données d'application.  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
