---
title: EXISTS (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 225487f6a0d7ec29689c01dd6355e7ba1aa6883e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="exists-entity-sql"></a>EXISTS (Entity SQL)
Détermine si une collection est vide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression valide qui retourne une collection.  
  
 NOT  
 Indique que la valeur du résultat de l'opérateur EXISTS est inversée.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` si la collection n'est pas vide ; sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 EXISTS est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite. Pour plus d’informations de priorité pour la [!INCLUDE[esql](../../../../../../includes/esql-md.md)] opérateurs de jeu, consultez [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL ci-dessous utilise l’opérateur EXISTS pour déterminer si la collection est vide. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
