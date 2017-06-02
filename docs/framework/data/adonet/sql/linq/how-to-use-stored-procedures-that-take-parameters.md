---
title: "Proc&#233;dure&#160;: utiliser des proc&#233;dures stock&#233;es qui prennent des param&#232;tres | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: utiliser des proc&#233;dures stock&#233;es qui prennent des param&#232;tres
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mappe des paramètres de sortie à des paramètres de référence et, pour les types valeur, déclare le paramètre comme Nullable.  
  
 Pour obtenir un exemple d'utilisation d'un paramètre d'entrée dans une requête qui retourne un jeu de lignes, consultez [Procédure : retourner des jeux de lignes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).  
  
## Exemple  
 L'exemple suivant prend un paramètre d'entrée unique \(ID client\) et retourne un paramètre de sortie \(total des ventes pour ce client\).  
  
```  
CREATE PROCEDURE [dbo].[CustOrderTotal]   
@CustomerID nchar(5),  
@TotalSales money OUTPUT  
AS  
SELECT @TotalSales = SUM(OD.UNITPRICE*(1-OD.DISCOUNT) * OD.QUANTITY)  
FROM ORDERS O, "ORDER DETAILS" OD  
where O.CUSTOMERID = @CustomerID AND O.ORDERID = OD.ORDERID  
```  
  
 [!code-csharp[DLinqSprox#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#2)]
 [!code-vb[DLinqSprox#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#2)]  
  
## Exemple  
 Vous appelleriez cette procédure stockée comme suit :  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## Voir aussi  
 [Procédures stockées](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)   
 [Téléchargement d'exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)   
 [Utilisation de types Nullable](../Topic/Using%20Nullable%20Types%20\(C%23%20Programming%20Guide\).md)   
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)