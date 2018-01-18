---
title: "Comment : utiliser des procédures stockées mappées pour plusieurs formes de résultats"
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
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fde4dd9044ff2bc6d781d7ceafec2bde3df7e14d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>Comment : utiliser des procédures stockées mappées pour plusieurs formes de résultats
Lorsqu’une procédure stockée peut retourner plusieurs formes de résultats, le type de retour ne peut pas être fortement typé en une forme de projection unique. Bien que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] peut générer tous les types de projection possibles, il ne peut pas connaître l’ordre dans lequel ils seront retournés.  
  
 Comparez ce scénario avec les procédures stockées qui produisent plusieurs formes de résultats de manière séquentielle. Pour plus d’informations, consultez [Comment : utiliser procédures stockées mappées pour des formes de résultats séquentielles](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).  
  
 L'attribut <xref:System.Data.Linq.Mapping.ResultTypeAttribute> est appliqué aux procédures stockées qui retournent plusieurs types de résultats pour spécifier l'ensemble de types que la procédure peut retourner.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple de code SQL suivant, la forme du résultat dépend de l'entrée (`shape =1` ou `shape = 2`). Vous ne savez pas quelle sera la première projection retournée.  
  
```  
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a>Exemple  
 Vous pouvez utiliser un code semblable à celui qui suit pour exécuter cette procédure stockée.  
  
> [!NOTE]
>  Vous devez utiliser le modèle <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pour obtenir un énumérateur du type approprié, basé sur votre connaissance de la procédure stockée.  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
