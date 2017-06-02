---
title: "Tri et filtrage de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Tri et filtrage de donn&#233;es
L'objet <xref:System.Data.DataView> offre plusieurs méthodes de tri et de filtrage de données dans un objet <xref:System.Data.DataTable> :  
  
-   Vous pouvez utiliser la propriété <xref:System.Data.DataView.Sort%2A> pour spécifier un ordre de tri en fonction d'une ou de plusieurs colonnes et inclure des paramètres ASC \(ordre croissant\) et DESC \(ordre décroissant\).  
  
-   Vous pouvez utiliser la propriété <xref:System.Data.DataView.ApplyDefaultSort%2A> pour créer automatiquement un ordre de tri, croissant, basé sur la ou les colonnes de clé primaire de la table.  <xref:System.Data.DataView.ApplyDefaultSort%2A> s'applique seulement lorsque la propriété **Sort** est une référence null ou une chaîne vide et lorsque la table a une clé primaire définie.  
  
-   Vous pouvez utiliser la propriété <xref:System.Data.DataView.RowFilter%2A> pour spécifier des sous\-ensembles de lignes basés sur les valeurs de colonne.  Pour plus d'informations sur les expressions pouvant être utilisées pour la propriété **RowFilter**, voir les informations de référence relatives à la propriété <xref:System.Data.DataColumn.Expression%2A> de la classe <xref:System.Data.DataColumn>.  
  
     Si vous souhaitez retourner les résultats d'une requête particulière exécutée sur les données, au lieu de fournir une vue dynamique d'un sous\-ensemble des données, utilisez l'une des méthodes <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> du **DataView** pour obtenir des performances optimales au lieu de définir la propriété **RowFilter**.  Le paramétrage de la propriété **RowFilter** entraîne une nouvelle génération de l'index des données, ce qui accroît la charge pour votre application et, par voie de conséquence, fait baisser les performances.  L'utilisation de la propriété **RowFilter** est optimale dans une application de liaison de données où un contrôle lié affiche des résultats filtrés.  Les méthodes **Find** et **FindRows** mettent à jour l'index en cours sans qu'il soit nécessaire de le reconstruire.  Pour plus d'informations sur les méthodes **Find** et **FindRows**, voir [Recherche de lignes](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
-   Vous pouvez utiliser la propriété <xref:System.Data.DataView.RowStateFilter%2A> pour spécifier les versions de ligne à afficher.  Le **DataView** gère implicitement la version de ligne à exposer en fonction du **RowState** de la ligne sous\-jacente.  Par exemple, si la propriété **RowStateFilter** a la valeur **DataViewRowState.Deleted**, le **DataView** expose la version **Original** de toutes les lignes **Deleted** car ces lignes n'ont plus de version **Current**.  Vous pouvez déterminer quelle version de ligne est exposée à l'aide de la propriété **RowVersion** du **DataRowView**.  
  
     Le tableau suivant présente les options de **DataViewRowState**.  
  
    |Options DataViewRowState|Description|  
    |------------------------------|-----------------|  
    |**CurrentRows**|La version de ligne **Current** de toutes les lignes **Unchanged**, **Added** et **Modified**.  Il s'agit de la valeur par défaut.|  
    |**Added**|Version de ligne **Current** de toutes les lignes **Added**.|  
    |**Supprimé**|Version de ligne **Original** de toutes les lignes **Deleted**.|  
    |**ModifiedCurrent**|Version de ligne **Current** de toutes les lignes **Modified**.|  
    |**ModifiedOriginal**|Version de ligne **Original** de toutes les lignes **Modified**.|  
    |**None**|Aucune ligne.|  
    |**OriginalRows**|Version de ligne **Original** de toutes les lignes **Unchanged**, **Modified** et **Deleted**.|  
    |**Inchangé**|Version de ligne **Current** de toutes les lignes **Unchanged**.|  
  
 Pour plus d'informations sur les états et les versions de lignes, voir [États et versions de ligne](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
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
  
## Voir aussi  
 <xref:System.Data.DataViewRowState>   
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataView>   
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)