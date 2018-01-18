---
title: "Comment : utiliser des procédures stockées qui prennent des paramètres"
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
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 505c99b262f4762d5965789688236b22e74bdaeb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Comment : utiliser des procédures stockées qui prennent des paramètres
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mappe des paramètres de sortie à des paramètres de référence et, pour les types valeur, déclare le paramètre comme Nullable.  
  
 Pour obtenir un exemple montrant comment utiliser un paramètre d’entrée dans une requête qui retourne un ensemble de lignes, consultez [Comment : retourner des jeux de lignes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant prend un paramètre d'entrée unique (ID client) et retourne un paramètre de sortie (total des ventes pour ce client).  
  
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
  
## <a name="example"></a>Exemple  
 Vous appelleriez cette procédure stockée comme suit :  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [Téléchargement d’exemples de base de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Utilisation de types Nullable](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [Types valeur Nullable](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
