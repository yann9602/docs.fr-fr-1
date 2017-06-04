---
title: "Langage Entity SQL | Microsoft Docs"
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
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Langage Entity SQL
Entity SQL est un langage de requête indépendant du stockage et semblable à SQL.  Entity SQL vous permet d'interroger des données d'entité, en tant qu'objets ou sous une forme tabulaire.  Vous devez envisager d'utiliser Entity SQL dans les cas suivants :  
  
-   Lorsqu'une requête doit être construite dynamiquement au moment de l'exécution.  Dans ce cas, vous devez également envisager d'utiliser les méthodes du Générateur de requêtes d'<xref:System.Data.Objects.ObjectQuery%601> au lieu de construire une chaîne de requête Entity SQL au moment de l'exécution.  
  
-   Lorsque vous voulez définir une requête dans le cadre de la définition du modèle.  Seul Entity SQL est pris en charge dans un modèle de données.  Pour plus d'informations, consultez [QueryView Element \(MSL\)](http://msdn.microsoft.com/fr-fr/f0426b34-45cb-4fd7-9777-e0570c5e0e80)  
  
-   Lorsque vous utilisez EntityClient pour retourner des données d'entité en lecture seule sous la forme d'ensembles de lignes à l'aide d'un <xref:System.Data.EntityClient.EntityDataReader>.  Pour plus d'informations, consultez [Fournisseur EntityClient pour Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
-   Si vous êtes déjà un expert des langages de requête basés sur SQL, Entity SQL peut vous sembler le choix le plus naturel.  
  
## Utilisation de Entity SQL avec le fournisseur EntityClient  
 Pour plus d'informations sur l'utilisation de Entity SQL avec le fournisseur EntityClient, consultez les rubriques suivantes :  
  
 [Fournisseur EntityClient pour Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [Procédure : générer une chaîne de connexion pour EntityConnection](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Procédure : exécuter une requête qui retourne des résultats PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Procédure : exécuter une requête qui retourne des résultats RefType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Procédure : exécuter une requête qui retourne des types complexes](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Procédure : exécuter une requête qui retourne des collections imbriquées](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Procédure : exécuter une requête Entity SQL paramétrable à l'aide d'EntityCommand](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Procédure : exécuter une procédure stockée paramétrable à l'aide d'EntityCommand](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Procédure : exécuter une requête polymorphe](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Procédure : explorer des relations à l'aide de l'opérateur Navigate](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## Utilisation de Entity SQL avec des requêtes d'objet  
 Pour plus d'informations sur l'utilisation de Entity SQL avec des requêtes d'objet, consultez les rubriques suivantes :  
  
 [How to: Execute a Query that Returns Entity Type Objects](http://msdn.microsoft.com/fr-fr/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [How to: Execute a Parameterized Query](http://msdn.microsoft.com/fr-fr/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [How to: Navigate Relationships Using Navigation Properties](http://msdn.microsoft.com/fr-fr/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [How to: Call a User\-Defined Function](http://msdn.microsoft.com/fr-fr/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [How to: Filter Data](http://msdn.microsoft.com/fr-fr/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [How to: Sort Data](http://msdn.microsoft.com/fr-fr/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [How to: Group Data](http://msdn.microsoft.com/fr-fr/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [How to: Aggregate Data](http://msdn.microsoft.com/fr-fr/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [How to: Execute a Query that Returns Anonymous Type Objects](http://msdn.microsoft.com/fr-fr/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [How to: Execute a Query that Returns a Collection of Primitive Types](http://msdn.microsoft.com/fr-fr/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [How to: Query Related Objects in an EntityCollection](http://msdn.microsoft.com/fr-fr/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [How to: Order the Union of Two Queries](http://msdn.microsoft.com/fr-fr/853c583a-eaba-4400-830d-be974e735313)  
  
 [How to: Page Through Query Results](http://msdn.microsoft.com/fr-fr/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## Dans cette section  
 [Vue d'ensemble d'Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## Voir aussi  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)   
 [Référence du langage](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)