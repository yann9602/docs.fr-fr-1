---
title: "Tri et filtre de données"
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
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 01c09d94fd3224e8fd875b7f6eea06b2d2c35cca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-and-filtering-data"></a>Tri et filtre de données
L'objet <xref:System.Data.DataView> offre plusieurs méthodes de tri et de filtrage de données dans un objet <xref:System.Data.DataTable> :  
  
-   Vous pouvez utiliser la propriété <xref:System.Data.DataView.Sort%2A> pour spécifier un ordre de tri en fonction d'une ou de plusieurs colonnes et inclure des paramètres ASC (ordre croissant) et DESC (ordre décroissant).  
  
-   Vous pouvez utiliser la propriété <xref:System.Data.DataView.ApplyDefaultSort%2A> pour créer automatiquement un ordre de tri, croissant, basé sur la ou les colonnes de clé primaire de la table. <xref:System.Data.DataView.ApplyDefaultSort%2A>s’applique uniquement lorsque le **tri** propriété est une référence null ou une chaîne vide, et lorsque la table a une clé primaire définie.  
  
-   Vous pouvez utiliser la propriété <xref:System.Data.DataView.RowFilter%2A> pour spécifier des sous-ensembles de lignes basés sur les valeurs de colonne. Pour plus d’informations sur les expressions valides pour la **RowFilter** propriété, consultez les informations de référence pour le <xref:System.Data.DataColumn.Expression%2A> propriété de la <xref:System.Data.DataColumn> classe.  
  
     Si vous souhaitez retourner les résultats d’une requête particulière exécutée sur les données, au lieu de fournir une vue dynamique d’un sous-ensemble des données, utilisez la <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> méthodes de la **DataView** pour obtenir des performances optimales au lieu de définition de la **RowFilter** propriété. Définition de la **RowFilter** propriété reconstruit l’index des données, ce qui accroît la charge pour votre application et de diminuer les performances. Le **RowFilter** propriété est mieux utilisée dans une application de liaison de données où un contrôle lié affiche des résultats filtrés. Le **trouver** et **FindRows** méthodes tirer parti de l’index en cours sans nécessiter de l’index à reconstruire. Pour plus d’informations sur la **trouver** et **FindRows** méthodes, consultez [recherche les lignes](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
-   Vous pouvez utiliser la propriété <xref:System.Data.DataView.RowStateFilter%2A> pour spécifier les versions de ligne à afficher. Le **DataView** gère implicitement la version de ligne à exposer en fonction de la **RowState** de la ligne sous-jacente. Par exemple, si le **RowStateFilter** a la valeur **DataViewRowState.Deleted**, le **DataView** expose le **d’origine** version de ligne de tous les **Deleted** lignes, car il n’est pas **actuel** version de ligne. Vous pouvez déterminer quelle version de ligne d’une ligne est affichée à l’aide de la **RowVersion** propriété de la **DataRowView**.  
  
     Le tableau suivant montre les options pour **DataViewRowState**.  
  
    |Options DataViewRowState|Description|  
    |------------------------------|-----------------|  
    |**CurrentRows**|Le **actuel** version de ligne de toutes les **Unchanged**, **Added**, et **modifié** lignes. Il s'agit de la valeur par défaut.|  
    |**Ajouté**|Le **actuel** version de ligne de toutes les **Added** lignes.|  
    |**Supprimé**|Le **d’origine** version de ligne de toutes les **Deleted** lignes.|  
    |**ModifiedCurrent**|Le **actuel** version de ligne de toutes les **modifié** lignes.|  
    |**ModifiedOriginal**|Le **d’origine** version de ligne de toutes les **modifié** lignes.|  
    |**Aucun**|Aucune ligne.|  
    |**OriginalRows**|Le **d’origine** version de ligne de toutes les **Unchanged**, **modifié**, et **Deleted** lignes.|  
    |**Non modifié**|Le **actuel** version de ligne de toutes les **Unchanged** lignes.|  
  
 Pour plus d’informations sur les États et les versions de ligne, consultez [état des lignes et des Versions de ligne](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 L'exemple de code suivant crée une vue faisant apparaître tous les produits pour lesquels la quantité en stock est inférieure ou égale au niveau de passage d'une nouvelle commande, triés d'abord par ID de fournisseur, puis par nom de produit.  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
