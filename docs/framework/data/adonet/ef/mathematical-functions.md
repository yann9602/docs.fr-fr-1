---
title: "Fonctions mathématiques"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ea933d1e6c0245f3bc6cc2a0767b593957b0598a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="mathematical-functions"></a>Fonctions mathématiques
Le fournisseur de données .NET Framework pour SQL Server (SqlClient) propose des fonctions mathématiques qui effectuent des calculs sur des valeurs d’entrée qui sont fournies comme arguments, et retournent une valeur numérique comme résultat. Ces fonctions se trouvent dans l'espace de noms SqlServer, lequel est disponible lorsque vous utilisez SqlClient. La propriété d'espace de noms d'un fournisseur permet à Entity Framework de découvrir le préfixe attribué par ce fournisseur à des constructions spécifiques, telles que des types et des fonctions. Le tableau suivant décrit les fonctions mathématiques SqlClient.  
  
|Fonction|Description|  
|--------------|-----------------|  
|`ABS(` `expression` `)`|Effectue la fonction de valeur absolue.<br /><br /> **Arguments**<br /><br /> `expression` :`Int32`,`Int64`, `Double` ou `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> Valeur absolue de l'expression spécifiée.<br /><br /> **Exemple**<br /><br /> `SqlServer.ABS(-2)`|  
|`ACOS(` `expression` `)`|Retourne la valeur d'arc cosinus de l'expression spécifiée.<br /><br /> **Arguments**<br /><br /> `expression` : `Double`.<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> `SqlServer.ACOS(.9)`|  
|`ASIN(` `expression` `)`|Retourne la valeur d'arcsinus de l'expression spécifiée.<br /><br /> **Arguments**<br /><br /> `expression` : `Double`.<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> `SqlServer.ASIN(.9)`|  
|`ATAN(` `expression` `)`|Retourne la valeur d'arctangente de l'expression numérique spécifiée.<br /><br /> **Arguments**<br /><br /> `expression` : `Double`.<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> `SqlServer.ATAN(9)`|  
|`ATN2(` `expression`, `expression``)`|Retourne l'angle, en radians, dont la tangente est comprise entre les deux expressions numériques spécifiées.<br /><br /> **Arguments**<br /><br /> `expression` : `Double`.<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> `SqlServer.ATN2(9, 8)`|  
|`CEILING(` `expression` `)`|Convertit l'expression spécifiée en plus petit entier supérieur ou égal à cette expression.<br /><br /> **Arguments**<br /><br /> `expression` :`Int32`,`Int64`, `Double` ou `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> Un `Int32`, `Int64`, `Double`, ou `Decimal`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]|  
|`COS(` `expression` `)`|Calcule le cosinus trigonométrique de l'angle spécifié, en radians.<br /><br /> **Arguments**<br /><br /> `expression` : `Double`.<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> `SqlServer.COS(45)`|  
|`COT(` `expression` `)`|Calcule la cotangente trigonométrique de l'angle spécifié, en radians.<br /><br /> **Arguments**<br /><br /> `expression` : `Double`.<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> `SqlServer.COT(60)`|  
|`DEGREES(` `radians` `)`|Retourne l'angle correspondant, en degrés.<br /><br /> **Arguments**<br /><br /> `expression` :`Int32`,`Int64`, `Double` ou `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> Un `Int32`, `Int64`, `Double`, ou `Decimal`.<br /><br /> **Exemple**<br /><br /> `SqlServer.DEGREES(3.1)`|  
|`EXP(` `expression` `)`|Calcule la valeur exponentielle d'une expression numérique spécifiée.<br /><br /> **Arguments**<br /><br /> `expression` : `Double`.<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> `SqlServer.EXP(1)`|  
|`FLOOR(` `expression` `)`|Convertit l'expression spécifiée en plus grand entier inférieur ou égal à cette expression.<br /><br /> **Arguments**<br /><br /> `expression` : `Double`.<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]|  
|`LOG(` `expression` `)`|Calcule le logarithme népérien de l'expression `float` spécifiée.<br /><br /> **Arguments**<br /><br /> `expression` : `Double`.<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> `SqlServer.LOG(100)`|  
|`LOG10(` `expression` `)`|Retourne le logarithme en base 10 de l'expression `Double` spécifiée.<br /><br /> **Arguments**<br /><br /> `expression` : `Double`.<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> `SqlServer.LOG10(100)`|  
|`PI()`|Retourne la valeur constante de pi sous la forme d'une valeur `Double`.<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> `SqlServer.PI()`|  
|`POWER(` `numeric_expression, power_expression` `)`|Calcule la valeur d'une expression donnée élevée à une puissance spécifiée.<br /><br /> **Arguments**<br /><br /> `numeric_expression` :`Int32`,`Int64`, `Double` ou `Decimal`.<br /><br /> `power_expression` : `Double` qui représente la puissance à laquelle doit être élevé le `numeric_expression`.<br /><br /> **Valeur de retour**<br /><br /> Valeur du paramètre `numeric_expression` donné élevé à la puissance `power_expression` spécifiée.<br /><br /> **Exemple**<br /><br /> `SqlServer.POWER(2,7)`|  
|`RADIANS(` `expression` `)`|Convertit les degrés en radians.<br /><br /> **Arguments**<br /><br /> `expression` :`Int32`,`Int64`, `Double` ou `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> Un `Int32`, `Int64`,<br /><br /> `Double` ou<br /><br /> `Decimal`.<br /><br /> **Exemple**<br /><br /> `SqlServer.RADIANS(360.0)`|  
|`RAND(`[valeur de départ]`)`|Retourne une valeur aléatoire comprise entre 0 et 1.<br /><br /> **Arguments**<br /><br /> Retourne la valeur initiale sous la forme d'un `Int32`. Si la valeur initiale n'est pas spécifiée, le moteur de base de données SQL Server affecte une valeur initiale aléatoire. Pour une valeur initiale spécifiée, le résultat retourné est toujours le même.<br /><br /> **Valeur de retour**<br /><br /> Valeur `Double` aléatoire comprise entre 0 et 1.<br /><br /> **Exemple**<br /><br /> `SqlServer.RAND()`|  
|`ROUND(` `numeric_expression, length` [ ,`function` ]`)`|Retourne une expression numérique, arrondie à la longueur ou à la précision spécifiée.<br /><br /> **Arguments**<br /><br /> `numeric_expression` :`Int32`,`Int64`, `Double` ou `Decimal`.<br /><br /> `length` : `Int32` qui représente la précision à laquelle arrondir `numeric_expression`. Lorsque `length` est un nombre positif, `numeric_expression` est arrondi au nombre de décimales indiqué par `length`. Lorsque `length` est un nombre négatif, `numeric_expression` est arrondi à gauche de la virgule décimale, selon l'indication fournie par `length`.<br /><br /> `function`: (facultatif) une `Int32` qui représente le type d’opération à effectuer. Lorsque function est omise ou a la valeur 0 (valeur par défaut), `numeric_expression` est arrondi. Lorsqu’une valeur autre que 0 est spécifiée, `numeric_expression` est tronqué.<br /><br /> **Valeur de retour**<br /><br /> Valeur du paramètre `numeric_expression` donné élevé à la puissance `power_expression` spécifiée.<br /><br /> **Exemple**<br /><br /> `SqlServer.ROUND(748.58, -3)`|  
|`SIGN(` `expression` `)`|Retourne le signe positif (+1), nul (0) ou négatif (-1) de l'expression spécifiée.<br /><br /> **Arguments**<br /><br /> `expression` : `Int32`, `Int64`, `Double` ou `Decimal`<br /><br /> **Valeur de retour**<br /><br /> Un `Int32`, `Int64`, `Double`, ou `Decimal`.<br /><br /> **Exemple**<br /><br /> `SqlServer.SIGN(-10)`|  
|`SIN(` `expression` `)`|Calcule le sinus trigonométrique de l'angle spécifié, en radians, et retourne une expression `Double`.<br /><br /> **Arguments**<br /><br /> `expression` : `Double`.<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> `SqlServer.SIN(20)`|  
|`SQRT(` `expression` `)`|Retourne la racine carrée de l'expression spécifiée.<br /><br /> **Arguments**<br /><br /> `expression` : `Double`.<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> `SqlServer.SQRT(3600)`|  
|`SQUARE(` `expression` `)`|Retourne le carré de l'expression spécifiée.<br /><br /> **Arguments**<br /><br /> `expression` : `Double`.<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> `SqlServer.SQUARE(25)`|  
|`TAN(` `expression` `)`|Calcule la tangente d'une expression spécifiée.<br /><br /> **Arguments**<br /><br /> `expression`: `Double`<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> `SqlServer.TAN(45.0)`|  
  
 Pour plus d'informations sur les fonctions mathématiques prises en charge par SqlClient, consultez la documentation correspondant à la version de SQL Server que vous avez spécifiée dans le manifeste du fournisseur SqlClient :  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Fonctions mathématiques (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115913)|[Fonctions mathématiques (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115911)|[Fonctions mathématiques (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115912)|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions SqlClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
