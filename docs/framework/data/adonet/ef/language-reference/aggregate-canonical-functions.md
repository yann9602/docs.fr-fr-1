---
title: "Fonctions canoniques d&#39;agr&#233;gation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Fonctions canoniques d&#39;agr&#233;gation
Les agrégats sont des expressions qui réduisent une série de valeurs d'entrée en, par exemple, une seule valeur.  Ils sont normalement utilisés avec la clause GROUP BY de l'expression SELECT et leur utilisation est sujette à certaines contraintes.  
  
 Le tableau suivant présente les fonctions canoniques [!INCLUDE[esql](../../../../../../includes/esql-md.md)] d'agrégation.  
  
|Fonction|Description|  
|--------------|-----------------|  
|`Avg(` `expression` `)`|Retourne la moyenne des valeurs non Null.<br /><br /> **Arguments**<br /><br /> `Int32`, `Int64`, `Double` et `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> Type d'élément `expression`.  `Null` si toutes les valeurs d'entrée sont `null`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
 [!code-sql[DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]|  
|`BigCount(` `expression` `)`|Retourne la taille de l'agrégat, y compris les valeurs Null et dupliquées.<br /><br /> **Arguments**<br /><br /> N'importe quel type.<br /><br /> **Valeur de retour**<br /><br /> Objet `Int64`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
 [!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]|  
|`Count(` `expression` `)`|Retourne la taille de l'agrégat, y compris les valeurs Null et dupliquées.<br /><br /> **Arguments**<br /><br /> N'importe quel type.<br /><br /> **Valeur de retour**<br /><br /> Objet `Int32`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
 [!code-sql[DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]|  
|`Max(` `expression` `)`|Retourne la valeur maximale des valeurs non\-Null.<br /><br /> **Arguments**<br /><br /> `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.<br /><br /> **Valeur de retour**<br /><br /> Type d'élément `expression`.  `Null` si toutes les valeurs d'entrée sont `null`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
 [!code-sql[DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]|  
|`Min(` `expression` `)`|Retourne la valeur minimale des valeurs non Null.<br /><br /> **Arguments**<br /><br /> `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.<br /><br /> **Valeur de retour**<br /><br /> Type d'élément `expression`.  `Null` si toutes les valeurs d'entrée sont `null`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
 [!code-sql[DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]|  
|`StDev(` `expression` `)`|Retourne l'écart type des valeurs non Null.<br /><br /> **Arguments**<br /><br /> `Int32`, `Int64`, `Double`, `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> `Double` `Null` si toutes les valeurs d'entrée sont `null`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
 [!code-sql[DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]|  
|`StDevP(` `expression` `)`|Retourne l'écart type pour le remplissage de toutes les valeurs.<br /><br /> **Arguments**<br /><br /> `Int32`, `Int64`, `Double`, `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> `Double` `Null` si toutes les valeurs d'entrée sont `null`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
 [!code-sql[DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]|  
|`Sum(` `expression` `)`|Retourne la somme des valeurs non\-Null.<br /><br /> **Arguments**<br /><br /> `Int32`, `Int64`, `Double`, `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> `Double` `Null` si toutes les valeurs d'entrée sont `null`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
 [!code-sql[DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]|  
|`Var(` `expression` `)`|Retourne la variance de toutes les valeurs non\-Null.<br /><br /> **Arguments**<br /><br /> `Int32`, `Int64`, `Double`, `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> `Double` `Null` si toutes les valeurs d'entrée sont `null`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
 [!code-sql[DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]|  
|`VarP(` `expression` `)`|Retourne la variance pour le remplissage de toutes les valeurs non\-Null.<br /><br /> **Arguments**<br /><br /> `Int32`, `Int64`, `Double`, `Decimal`.<br /><br /> **Valeur de retour**<br /><br /> `Double` `Null` si toutes les valeurs d'entrée sont `null`.<br /><br /> **Exemple**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
 [!code-sql[DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]|  
  
 Des fonctionnalités équivalentes sont disponibles dans le fournisseur managé Client Microsoft SQL.  Pour plus d'informations, consultez [SqlClient pour les fonctions Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## Agrégats basés sur des collections  
 Les agrégats basés sur des collections \(fonctions de collection\) opèrent sur des collections et retournent une valeur.  Par exemple, si ORDERS est une collection de toutes les commandes, vous pouvez calculer la première date d'expédition \(ship date\) grâce à l'expression suivante :  
  
```  
min(select value o.ShipDate from LOB.Orders as o)  
```  
  
 Les expressions figurant dans des agrégats basés sur des collections sont évalués dans l'étendue de résolution de noms ambiante actuelle.  
  
## agrégats basés sur des groupes  
 Les agrégats basés sur des groupes sont calculés sur un groupe défini par la clause GROUP BY.  Pour chaque groupe du résultat, un agrégat distinct est calculé en utilisant les éléments de chaque groupe fourni en entrée pour le calcul.  Lorsqu'une clause group\-by est utilisée dans une expression select, seuls des noms d'expressions de regroupement, des agrégats ou des expressions constantes peuvent figurer dans la projection ou la clause order\-by.  
  
 L'exemple suivant calcule la quantité moyenne commandée pour chaque produit :  
  
```  
select p, avg(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 Un agrégat basé sur un groupe peut ne pas avoir de clause group\-by explicite dans l'expression SELECT.  Dans ce cas, tous les éléments seront traités comme un même groupe.  Cela revient à spécifier un regroupement basé sur une constante.  L'expression suivante, par exemple :  
  
```  
select avg(ol.Quantity) from LOB.OrderLines as ol  
```  
  
 est équivalente à celle\-ci :  
  
```  
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1  
```  
  
 Les expressions figurant dans des agrégats basés sur des groupes sont évalués dans l'étendue de résolution de noms qui serait visible pour l'expression de la clause WHERE.  
  
 Comme dans [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], les agrégats basés sur des groupes peuvent aussi spécifier un modificateur ALL ou DISTINCT.  Si le modificateur DISTINCT est spécifié, les doublons sont éliminés de la collection d'entrée de l'agrégat, avant que celui\-ci ne soit calculé.  Si le modificateur ALL est spécifié \(ou si aucun modificateur ne l'est\), les doublons ne sont pas éliminés.  
  
## Voir aussi  
 [Fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)