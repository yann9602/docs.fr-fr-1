---
title: KEY (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: aa18efd32998f881d49d7ebd71bad0cdf8122457
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="key-entity-sql"></a>KEY (Entity SQL)
Extrait la clé d'une référence ou d'une expression d'entité.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Notes  
 Une clé d'entité contient les valeurs de clés dans l'ordre correct de l'entité ou de la référence d'entité spécifiée. Plusieurs jeux d'entités pouvant être basés sur le même type d'entité, la même clé peut apparaître dans chaque jeu d'entités. Pour obtenir une référence unique, utilisez `REF`. Le type de retour de l'opérateur KEY est un type de ligne qui inclut un champ pour chaque clé de l'entité, dans le même ordre.  
  
 Dans l'exemple suivant, une référence à l'entité BadOrder est passée à l'opérateur Key, lequel retourne la partie clé de cette référence. Dans le cas présent, un type d'enregistrement ayant exactement un champ correspondant à la propriété `Id` .  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL suivante utilise l'opérateur KEY pour extraire la partie clé d'une expression avec référence de type. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
