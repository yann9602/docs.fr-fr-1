---
title: REF (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1836b91876ac3c993f07902a644c130dda76f158
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ref-entity-sql"></a>REF (Entity SQL)
Retourne une référence à une instance d'entité.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression valide qui produit une instance d'un type d'entité.  
  
## <a name="return-value"></a>Valeur de retour  
 Référence à l'instance d'entité spécifiée.  
  
## <a name="remarks"></a>Notes  
 Une référence d'entité se compose de la clé d'entité et d'un nom de jeu d'entités. Des jeux d'entités différents pouvant être basés sur le même type d'entité, une clé d'entité particulière peut apparaître dans plusieurs jeux d'entités. Toutefois, une référence d'entité est toujours unique. Si l'expression d'entrée représente une entité rendue persistante, une référence à cette entité est retournée. Si l'expression d'entrée n'est pas une entité rendue persistante, une référence Null à cette entité est retournée.  
  
 Si l'opérateur d'extraction de propriété (.) est utilisé pour accéder à une propriété d'une entité, la référence est automatiquement supprimée.  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL suivante utilise l'opérateur REF pour retourner la référence d'un argument d'entité d'entrée. La même requête supprime la référence car nous utilisons une opération d'extraction de propriété (.) pour accéder à une propriété de l'entité Product. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure de [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a>Voir aussi  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Définitions de type](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
