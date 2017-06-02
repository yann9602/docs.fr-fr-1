---
title: "Exploration des DataRelations | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Exploration des DataRelations
L'une des principales fonctions d'un objet <xref:System.Data.DataRelation> est de permettre de passer d'un objet <xref:System.Data.DataTable> à un autre à l'intérieur d'un objet <xref:System.Data.DataSet>.  Cela vous permet d'extraire tous les objets <xref:System.Data.DataRow> associés dans un **DataTable** lorsqu'un **DataRow** est fourni à partir d'un **DataTable** associé.  Par exemple, après avoir créé un **DataRelation** entre une table de clients et une table de commandes, vous pouvez extraire toutes les lignes de commandes pour une ligne de client donnée à l'aide de **GetChildRows**.  
  
 L'exemple de code suivant crée un **DataRelation** entre les tables **Customers** \(clients\) et **Orders** \(commandes\) d'un **DataSet** et retourne toutes les commandes de chaque client.  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 L'exemple suivant s'appuie sur le précédent, en créant des relations entre quatre tables et en explorant ces relations.  Comme dans l'exemple précédent, **CustomerID** lie la table **Customers** à la table **Orders**.  Pour chaque client de la table **Customers**, toutes les lignes enfants de la table **Orders** sont déterminées, afin de retourner le nombre de commandes passées par un client et la valeur **OrderID** de chaque commande.  
  
 L'exemple enrichi retourne aussi les valeurs des tables **OrderDetails** et **Products**.  La table **Orders** est associée à la table **OrderDetails** au moyen de **OrderID** afin de déterminer, pour chaque client, les produits qui ont été commandés et en quelle quantité.  La table **OrderDetails** ne contenant que le **ProductID** d'un produit commandé, une relation est créée entre **OrderDetails** et **Products**, au moyen de **ProductID**, afin de retourner le **ProductName**.  Dans cette relation, **Products** est la table parente et **OrderDetails** la table enfant.  Ainsi, lors de l'itération sur la table **OrderDetails**, la méthode **GetParentRow** est appelée pour extraire la valeur **ProductName** associée.  
  
 Notez que lorsque le **DataRelation** est créé pour les tables **Customers** et **Orders**, aucune valeur n'est spécifiée pour l'indicateur **createConstraints** \(la valeur par défaut est **true**\).  Cela suppose que toutes les lignes de la table **Orders** ont une valeur **CustomerID** qui existe dans la table parente **Customers**.  Si un **CustomerID** existe dans la table **Orders**, mais pas dans la table **Customers**, un objet <xref:System.Data.ForeignKeyConstraint> entraîne la levée d'une exception.  
  
 Lorsque la colonne enfant est susceptible de contenir des valeurs qui ne figurent pas dans la colonne parente, attribuez à l'indicateur **createConstraints** la valeur **false** lorsque vous ajoutez le **DataRelation**.  Dans l'exemple, l'indicateur **createConstraints** a la valeur **false** pour le **DataRelation** établi entre les tables **Orders** et **OrderDetails**.  L'application peut ainsi retourner tous les enregistrements de la table **OrderDetails** et seulement un sous\-ensemble de la table **Orders** sans qu'une exception runtime ne soit levée.  La sortie de l'exemple se présente comme suit.  
  
```  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 L'exemple de code suivant est enrichi pour que soient retournées les valeurs des tables **OrderDetails** et **Products** et seulement un sous\-ensemble des enregistrements de la table **Orders**.  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## Voir aussi  
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)