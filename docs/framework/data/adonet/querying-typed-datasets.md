---
title: "Interrogation de DataSets typ&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Interrogation de DataSets typ&#233;s
Si le schéma du <xref:System.Data.DataSet> est connu au moment du design de l'application, nous vous recommandons d'utiliser un <xref:System.Data.DataSet> typé lors de l'utilisation de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  Un <xref:System.Data.DataSet> typé est dérivé d'un <xref:System.Data.DataSet>.  De ce fait, il hérite de l'ensemble des méthodes, événements et propriétés d'un <xref:System.Data.DataSet>.  En outre, un <xref:System.Data.DataSet> typé fournit des méthodes, événements et propriétés fortement typés.  Cela signifie que vous pouvez accéder à des tables et à des colonnes par leur nom au lieu d'utiliser les méthodes associées à des collections.  Cela rend les requêtes plus simples et plus lisibles.  Pour plus d'informations, consultez [DataSets typés](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] prend également en charge l'interrogation sur un <xref:System.Data.DataSet> typé.  Avec un <xref:System.Data.DataSet> typé, vous n'avez pas besoin d'utiliser la méthode générique <xref:System.Data.DataRowExtensions.Field%2A> ou la méthode <xref:System.Data.DataRowExtensions.SetField%2A> pour accéder aux données de colonne.  Les noms de propriétés sont disponibles au moment de la compilation parce que les informations de type sont incluses dans le <xref:System.Data.DataSet>. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] donne accès aux valeurs de colonne avec le type approprié, ce qui fait que les erreurs d'incompatibilité de types sont interceptées non pas à l'exécution, mais dès la compilation.  
  
 Avant de procéder à l'interrogation d'un <xref:System.Data.DataSet> typé, vous devez générer la classe à l'aide du Concepteur de DataSet dans [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  Pour plus d'informations, consultez [Comment : créer un groupe de données typé](../Topic/Create%20and%20configure%20datasets%20in%20Visual%20Studio.md).  
  
## Exemple  
 L'exemple suivant montre une requête sur un <xref:System.Data.DataSet> typé :  
  
```csharp  
var query = from o in orders  
            where o.OnlineOrderFlag == true  
            select new { o.SalesOrderID,  
                         o.OrderDate,  
                         o.SalesOrderNumber };  
  
foreach(var order in query)   
{  
    Console.WriteLine("{0}\t{1:d}\t{2}",   
order.SalesOrderID,   
order.OrderDate,   
order.SalesOrderNumber);  
}  
```  
  
```vb  
Dim orders = ds.Tables("SalesOrderHeader")  
  
Dim query = _  
       From o In orders _  
       Where o.OnlineOrderFlag = True _  
       Select New {SalesOrderID := o.SalesOrderID, _  
                   OrderDate := o.OrderDate, _  
                   SalesOrderNumber := o.SalesOrderNumber}  
  
For Each Dim onlineOrder In query  
 Console.WriteLine("{0}\t{1:d}\t{2}", _  
 onlineOrder.SalesOrderID, _  
 onlineOrder.OrderDate, _  
 onlineOrder.SalesOrderNumber)  
Next  
```  
  
## Voir aussi  
 [Interrogation de DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)   
 [Requêtes d'analyse croisée](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)   
 [Requêtes d'analyse unique](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)