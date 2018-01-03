---
title: "Interrogation de DataSets typés"
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
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c232ca2888c957bea33d06c84a62b00fdc7fd80c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="querying-typed-datasets"></a>Interrogation de DataSets typés
Si le schéma du <xref:System.Data.DataSet> est connu au moment du design de l'application, nous vous recommandons d'utiliser un <xref:System.Data.DataSet> typé lors de l'utilisation de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Typé <xref:System.Data.DataSet> est une classe qui dérive d’un <xref:System.Data.DataSet>. De ce fait, il hérite de l'ensemble des méthodes, événements et propriétés d'un <xref:System.Data.DataSet>. En outre, un typé <xref:System.Data.DataSet> fournit des méthodes fortement typées, propriétés et événements. Cela signifie que vous pouvez accéder à des tables et à des colonnes par leur nom au lieu d’utiliser les méthodes associées à des collections. Cela rend les requêtes plus simples et plus lisibles. Pour plus d’informations, consultez [typés](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]prend en charge l’interrogation sur typé également <xref:System.Data.DataSet>. Avec un typé <xref:System.Data.DataSet>, vous n’avez pas à utiliser le type générique <xref:System.Data.DataRowExtensions.Field%2A> méthode ou <xref:System.Data.DataRowExtensions.SetField%2A> méthode pour accéder aux données de colonne.  Noms de propriété sont disponibles au moment de la compilation, car les informations de type sont incluses dans le <xref:System.Data.DataSet>. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]fournit l’accès aux valeurs de colonne avec le type approprié, afin que les erreurs d’incompatibilité de type sont interceptées lorsque le code est compilé à la place de l’exécution.  
  
 Avant de procéder à l'interrogation d'un <xref:System.Data.DataSet> typé, vous devez générer la classe à l'aide du Concepteur de DataSet dans [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  Pour plus d’informations, consultez [Créer et configurer des datasets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).  
  
## <a name="example"></a>Exemple  
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
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation de DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [Requêtes de table croisée](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 [Requêtes de table unique](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
