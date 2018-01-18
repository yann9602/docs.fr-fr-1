---
title: Vue d'ensemble d'Entity SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 37390d97325d6532624cd6ffe14c2d6c37ba2084
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="entity-sql-overview"></a>Vue d'ensemble d'Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] est un langage similaire à SQL qui vous permet d'interroger des modèles conceptuels dans [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Des modèles conceptuels représentent des données en tant qu’entités et de relations, et [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vous permet d’interroger les entités et les relations dans un format familier pour ceux qui ont utilisé SQL.  
  
 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] utilise des fournisseurs de données de stockage pour traduire le langage [!INCLUDE[esql](../../../../../../includes/esql-md.md)] générique en requêtes de stockage. Le fournisseur EntityClient fournit une méthode pour exécuter une commande [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sur un modèle d'entité et retourner des types de données enrichis, y compris des résultats scalaires, des jeux de résultats et des graphiques d'objets. Lorsque vous construisez des objets <xref:System.Data.EntityClient.EntityCommand>, vous pouvez spécifier un nom de procédure stockée ou le texte d'une requête en assignant une chaîne de requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] à sa propriété <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType>. <xref:System.Data.EntityClient.EntityDataReader> expose les résultats de l'exécution d'un <xref:System.Data.EntityClient.EntityCommand> sur un modèle EDM. Pour exécuter la commande qui retourne l'objet <xref:System.Data.EntityClient.EntityDataReader>, appelez la méthode <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.  
  
 Outre le fournisseur EntityClient, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] vous permet d'utiliser [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pour exécuter des requêtes sur un modèle conceptuel et retourner des données sous forme d'objets CLR fortement typés qui sont des instances de types d'entités. Pour plus d’informations, consultez [utilisation des objets](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Cette section fournit des informations conceptuelles sur [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Différences entre Entity SQL et Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
  
 [Aide-mémoire Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-quick-reference.md)  
  
 [Système de type](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)  
  
 [Définitions de type](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)  
  
 [Construction de types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
  
 [Mise en cache d’un plan de requête](../../../../../../docs/framework/data/adonet/ef/language-reference/query-plan-caching-entity-sql.md)  
  
 [Espaces de noms](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
  
 [Identificateurs](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 [Paramètres](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
  
 [Variables](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)  
  
 [Expressions non prises en charge](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)  
  
 [Littéraux](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)  
  
 [Littéraux null et inférence de type](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)  
  
 [Jeu de caractères en entrée](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)  
  
 [Expressions de requête](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
  
 [Fonctions](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)  
  
 [Priorité des opérateurs](../../../../../../docs/framework/data/adonet/ef/language-reference/operator-precedence-entity-sql.md)  
  
 [Pagination](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
  
 [Sémantique de comparaison](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-semantics-entity-sql.md)  
  
 [Composition de requêtes Entity SQL imbriquées](../../../../../../docs/framework/data/adonet/ef/language-reference/composing-nested-entity-sql-queries.md)  
  
 [Types structurés autorisant la valeur null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Langage Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [Spécifications CSDL, SSDL et MSL](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
