---
title: "Fonctions d’agrégation (SqlClient pour Entity Framework)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 804acd77887c1cf05caa2004e75ef01110909490
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Fonctions d’agrégation (SqlClient pour Entity Framework)
Le fournisseur de données .NET Framework pour SQL Server (SqlClient) fournit des fonctions d'agrégation. Les fonctions d'agrégation effectuent des calculs sur un ensemble de valeurs d'entrée et retournent une valeur. Ces fonctions se trouvent dans l'espace de noms SqlServer, lequel est disponible lorsque vous utilisez SqlClient. La propriété d'espace de noms d'un fournisseur permet à Entity Framework de découvrir le préfixe attribué par ce fournisseur à des constructions spécifiques, telles que des types et des fonctions.  
  
 Le tableau suivant présente les fonctions d'agrégation SqlClient.  
  
|Fonction|Description|  
|--------------|-----------------|  
|`AVG(` `expression` `)`|Retourne la moyenne des valeurs d’une collection.<br /><br /> Les valeurs NULL sont ignorées.<br /><br /> **Arguments**<br /><br /> Un `Int32`, `Int64`, `Double`, et `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> Type d'élément `expression`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]|  
|`CHECKSUM_AGG(` `collection` `)`|Retourne la somme de contrôle des valeurs d’une collection.<br /><br /> Les valeurs NULL sont ignorées.<br /><br /> **Arguments**<br /><br /> Collection (`Int32`).<br /><br /> **Valeur de retour**<br /><br /> Élément `Int32`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]|  
|`COUNT(` `expression` `)`|Retourne le nombre d'éléments d'une collection sous la forme d'une valeur `Int32`.<br /><br /> **Arguments**<br /><br /> Collection (T) où T est l’un des types suivants :<br /><br /> `Guid` (non retourné dans SQL Server 2000),<br /><br /> `Boolean`, `Double`, `DateTime`, `DateTimeOffset`, `Time`, `String` ou `Binary`.<br /><br /> **Valeur de retour**<br /><br /> Élément `Int32`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]|  
|`COUNT_BIG(` `expression` `)`|Retourne le nombre d'éléments d'une collection sous la forme d'une valeur `bigint`.<br /><br /> **Arguments**<br /><br /> Collection (T) où T est l’un des types suivants :<br /><br /> `Guid` (non retourné dans SQL Server 2000), `Boolean`, `Double`, `DateTime`, `DateTimeOffset`, `Time`, `String` ou `Binary`.<br /><br /> **Valeur de retour**<br /><br /> Élément `Int64`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]|  
|`MAX(` `expression` `)`|Retourne la valeur maximale contenue dans la collection.<br /><br /> **Arguments**<br /><br /> Collection (T) où T est l'un des types suivants : `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String` ou `Binary`.<br /><br /> **Valeur de retour**<br /><br /> Type d'élément `expression`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]|  
|`MIN(` `expression` `)`|Retourne la valeur minimale contenue dans une collection.<br /><br /> **Arguments**<br /><br /> Collection (T) où T est l'un des types suivants : `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`,<br /><br /> `Binary`.<br /><br /> **Valeur de retour**<br /><br /> Type d'élément `expression`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]|  
|`STDEV(` `expression` `)`|Retourne l'écart type statistique de toutes les valeurs de l'expression spécifiée.<br /><br /> **Arguments**<br /><br /> Collection (`Double`).<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]|  
|`STDEVP(` `expression` `)`|Retourne l'écart type statistique du remplissage de toutes les valeurs de l'expression spécifiée.<br /><br /> **Arguments**<br /><br /> Collection (`Double`).<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]|  
|`SUM(` `expression` `)`|Retourne la somme de toutes les valeurs de la collection.<br /><br /> **Arguments**<br /><br /> Collection (T) où T est l'un des types suivants : `Int32`, `Int64`, `Double`, `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> Type d'élément `expression`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]|  
|`VAR(` `expression` `)`|Retourne la variance statistique de toutes les valeurs dans l'expression spécifiée.<br /><br /> **Arguments**<br /><br /> Collection (`Double`).<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]|  
|`VARP(` `expression` `)`|Retourne la variance statistique de remplissage pour toutes les valeurs de l'expression spécifiée.<br /><br /> **Arguments**<br /><br /> Collection (`Double`).<br /><br /> **Valeur de retour**<br /><br /> `Double`<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]|  
  
 Pour plus d'informations sur les fonctions d'agrégation prises en charge par SqlClient, voir la documentation correspondant à la version de SQL Server que vous avez spécifiée dans le manifeste du fournisseur SqlClient :  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Fonctions d’agrégation (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115906)|[Fonctions d’agrégation (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=115903)|[Fonctions d’agrégation (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115907)|  
  
## <a name="see-also"></a>Voir aussi  
 [Langage Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [Fonctions canoniques d’agrégation](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
