---
title: "&gt;= (Supérieur ou égal à) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b176e1efdc17b58083234d0437033bd43775f604
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="gt-greater-than-or-equal-to-entity-sql"></a>&gt;= (Supérieur ou égal à) (Entity SQL)
Compare deux expressions pour déterminer si la valeur de l'expression de gauche est supérieure ou égale à celle de l'expression de droite.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression valide. Les deux expressions doivent posséder des types de données implicitement convertibles.  
  
## <a name="result-types"></a>Types de résultats  
 `true` si la valeur de l'expression de gauche est supérieure ou égale à celle de l'expression de droite ; sinon, `false`.  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL ci-dessous utilise l'opérateur de comparaison >= pour comparer deux expressions afin de déterminer si la valeur de l'expression de gauche est supérieure ou égale à celle de l'expression de droite. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
