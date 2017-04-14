---
title: "Fournisseur EntityClient pour Entity Framework | Microsoft Docs"
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
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Fournisseur EntityClient pour Entity Framework
Le fournisseur EntityClient est un fournisseur de données utilisé par les applications Entity Framework pour accéder à des données décrites dans un modèle conceptuel.  Pour obtenir des informations sur les modèles conceptuels, consultez [Modélisation et mappage](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md).  EntityClient utilise d'autres fournisseurs de données .NET Framework pour accéder à la source de données.  Par exemple, EntityClient utilise le fournisseur de données .NET Framework pour SQL Server \(SqlClient\) lors de l'accès à une base de données SQL Server.  Pour plus d'informations sur le fournisseur SqlClient, voir [SqlClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md).  Le fournisseur EntityClient est implémenté dans l'espace de noms <xref:System.Data.EntityClient>.  
  
## Gestion des connexions  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] s'appuie sur des données [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] spécifiques au stockage en fournissant un objet <xref:System.Data.EntityClient.EntityConnection> à un fournisseur de données et à une base de données relationnelle sous\-jacents.  Pour construire un objet <xref:System.Data.EntityClient.EntityConnection>, vous devez faire référence à un ensemble de métadonnées contenant les modèles et le mappage requis, ainsi qu'à un nom de fournisseur de données spécifique au stockage et à une chaîne de connexion.  Une fois l'objet <xref:System.Data.EntityClient.EntityConnection> en place, les entités sont accessibles par le biais des classes générées à partir du modèle conceptuel.  
  
 Vous pouvez spécifier une chaîne de connexion dans le fichier app.config.  
  
 <xref:System.Data.EntityClient> comprend également la classe <xref:System.Data.EntityClient.EntityConnectionStringBuilder>.  Cette classe permet aux développeurs de créer par programme des chaînes de connexion correctes du point de vue syntaxique, et d'analyser et régénérer les chaînes de connexion existantes, à l'aide des propriétés et des méthodes de la classe.  Pour plus d'informations, consultez [Procédure : générer une chaîne de connexion pour EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).  
  
## Création de requêtes  
 Le langage [!INCLUDE[esql](../../../../../includes/esql-md.md)] est un dialecte SQL indépendant du stockage qui fonctionne directement avec les schémas d'entité conceptuels et qui prend en charge certains concepts Entity Data Model, tels que l'héritage et les relations.  La classe <xref:System.Data.EntityClient.EntityCommand> permet d'exécuter une commande [!INCLUDE[esql](../../../../../includes/esql-md.md)] sur un modèle d'entité.  Au moment de la construction d'objets <xref:System.Data.EntityClient.EntityCommand>, vous pouvez spécifier un nom de procédure stockée ou un texte de requête.  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] utilise des fournisseurs de données de stockage pour traduire le langage [!INCLUDE[esql](../../../../../includes/esql-md.md)] générique en requêtes de stockage.  Pour plus d'informations sur l'écriture de requêtes [!INCLUDE[esql](../../../../../includes/esql-md.md)], consultez [Langage Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
 L'exemple suivant crée un objet <xref:System.Data.EntityClient.EntityCommand> et affecte un texte de requête [!INCLUDE[esql](../../../../../includes/esql-md.md)] à sa propriété <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=fullName>.  Cette requête [!INCLUDE[esql](../../../../../includes/esql-md.md)] demande les produits classés par prix courant à partir du modèle conceptuel.  Le code suivant fait une totale abstraction du modèle de stockage.  
  
 `EntityCommand cmd = conn.CreateCommand();`  
  
 `cmd.CommandText = @"` `SELECT VALUE p`  
  
 `FROM AdventureWorksEntities.Product AS p`  
  
 `ORDER BY p.ListPrice ";`  
  
## Exécution de requêtes  
 Lorsqu'une requête est exécutée, elle est analysée et convertie en arborescence de commandes canonique.  Tous les traitements ultérieurs sont exécutés sur l'arborescence de commandes.  L'arborescence de commandes est le moyen de communication entre <xref:System.Data.EntityClient> et le fournisseur de données [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] sous\-jacent, tel que <xref:System.Data.SqlClient>.  
  
 <xref:System.Data.EntityClient.EntityDataReader> expose les résultats de l'exécution d'un objet <xref:System.Data.EntityClient.EntityCommand> sur un modèle conceptuel.  Pour exécuter la commande qui retourne l'objet <xref:System.Data.EntityClient.EntityDataReader>, appelez la méthode <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.  <xref:System.Data.EntityClient.EntityDataReader> implémente <xref:System.Data.IExtendedDataRecord> pour décrire des résultats structurés et enrichis.  
  
## Gestion des transactions  
 Dans Entity Framework, il existe deux modes d'utilisation des transactions : automatique et explicite.  Les transactions automatiques utilisent l'espace de noms <xref:System.Transactions>, tandis que les transactions explicites utilisent la classe <xref:System.Data.EntityClient.EntityTransaction>.  
  
 Pour mettre à jour des données exposées via un modèle conceptuel, consultez [How to: Manage Transactions in the Entity Framework](http://msdn.microsoft.com/fr-fr/4a55eb7f-f826-4a48-9df1-aebe2352ebef).  
  
## Dans cette section  
 [Procédure : générer une chaîne de connexion pour EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Procédure : exécuter une requête qui retourne des résultats PrimitiveType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Procédure : exécuter une requête qui retourne des résultats RefType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Procédure : exécuter une requête qui retourne des types complexes](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Procédure : exécuter une requête qui retourne des collections imbriquées](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Procédure : exécuter une requête Entity SQL paramétrable à l'aide d'EntityCommand](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Procédure : exécuter une procédure stockée paramétrable à l'aide d'EntityCommand](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Procédure : exécuter une requête polymorphe](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Procédure : explorer des relations à l'aide de l'opérateur Navigate](../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## Voir aussi  
 [Managing Connections and Transactions](http://msdn.microsoft.com/fr-fr/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)   
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)   
 [Référence du langage](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)