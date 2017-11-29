---
title: "Fonctions mathématiques canoniques"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b6e69a9dbc204cfa8f0abc7e641b0784a08d747c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="math-canonical-functions"></a>Fonctions mathématiques canoniques
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] intègre des fonctions canoniques mathématiques.  
  
 Le tableau ci-dessous présente les fonctions canoniques mathématiques [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Fonction|Description|  
|--------------|-----------------|  
|`Abs(` `value` `)`|Retourne la valeur absolue de `value`.<br /><br /> **Arguments**<br /><br /> Un `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, et `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> Type d'élément `value`.<br /><br /> **Exemple**<br /><br /> `Abs(-2)`|  
|`Ceiling(` `value` `)`|Retourne le plus petit entier qui n'est pas inférieur à `value`.<br /><br /> **Arguments**<br /><br /> A `Single`, `Double`, et `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> Type d'élément `value`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
 [!code-sql[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]|  
|`Floor(` `value` `)`|Retourne le plus grand entier qui n'est pas supérieur à `value`.<br /><br /> **Arguments**<br /><br /> A `Single`, `Double`, et `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> Type d'élément `value`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
 [!code-sql[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]|  
|`Power(` `value`, `exponent``)`|Retourne le résultat de `value` à l'exposant `exponent` spécifié.<br /><br /> **Arguments**<br /><br /> `value`: Une `Int32, Int64, Double`, ou `Decimal`.<br /><br /> `exponent`: Une `Int64``, Double`, ou `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> Type d'élément `value`.<br /><br /> **Exemple**<br /><br /> `Power(748.58,2)`|  
|`Round(` `value` `)`|Retourne la partie entière de `value`, arrondie à l'entier le plus proche.<br /><br /> **Arguments**<br /><br /> A `Single`, `Double`, et `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> Type d'élément `value`.<br /><br /> **Exemple**<br /><br /> `Round(748.58)`|  
|`Round(` `value`, `digits``)`|Retourne `value`, arrondi aux `digits` spécifiés les plus proches.<br /><br /> **Arguments**<br /><br /> `value` : `Double` ou `Decimal`.<br /><br /> `digits` : `Int16` ou `Int32`.<br /><br /> **Valeur de retour**<br /><br /> Type d'élément `value`.<br /><br /> **Exemple**<br /><br /> `Round(748.58,1)`|  
|`Truncate(` `value`, `digits``)`|Retourne `value`, tronqué aux `digits` spécifiés les plus proches.<br /><br /> **Arguments**<br /><br /> `value` : `Double` ou `Decimal`.<br /><br /> `digits` : `Int16` ou `Int32`.<br /><br /> **Valeur de retour**<br /><br /> Type d'élément `value`.<br /><br /> **Exemple**<br /><br /> `Truncate(748.58,1)`|  
  
 Ces fonctions retournent `null` si une entrée de valeur `null` est fournie.  
  
 Des fonctionnalités équivalentes sont disponibles dans le fournisseur managé Client Microsoft SQL. Pour plus d’informations, consultez [fonctions SqlClient pour Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
