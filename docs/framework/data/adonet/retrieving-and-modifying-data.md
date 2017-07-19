---
title: "Extraction et modification de donn&#233;es dans ADO.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Extraction et modification de donn&#233;es dans ADO.NET
Une fonction principale de toute application de base de données consiste à se connecter à une source de données et extraire les données qu'elle contient.  Les fournisseurs de données .NET Framework d'ADO.NET font office de passerelle entre une application et une source de données, ce qui vous permet d'exécuter des commandes et d'extraire des données à l'aide d'un **DataReader** ou d'un **DataAdapter**.  Une fonction clé de toute application de base de données est la capacité à mettre à jour les données stockées dans la base de données.  Dans ADO.NET, la mise à jour de données implique l'utilisation des objets **DataAdapter**, <xref:System.Data.DataSet> et **Command** ; elle peut également impliquer l'utilisation de transactions.  
  
## Dans cette section  
 [Connexion à une source de données](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 Décrit comment établir une connexion à une source de données et comment travailler avec des événements de connexion.  
  
 [Chaînes de connexion](../../../../docs/framework/data/adonet/connection-strings.md)  
 Contient des rubriques qui décrivent divers aspects de l'utilisation de chaînes de connexion, y compris des mots clés de chaîne de connexion, des informations de sécurité, ainsi que de leur stockage et leur extraction.  
  
 [Regroupement de connexions](../../../../docs/framework/data/adonet/connection-pooling.md)  
 Décrit le regroupement de connexions pour les fournisseurs de données .NET Framework.  
  
 [Commandes et paramètres](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 Contient des rubriques qui décrivent comment créer des commandes et des générateurs de commande, configurer des paramètres et exécuter des commandes pour extraire et modifier des données.  
  
 [DataAdapters et DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 Contient des rubriques qui décrivent les objets DataReader et DataAdapter, les paramètres, la gestion des événements DataAdapter et l'exécution d'opérations par lots.  
  
 [Transactions et concurrence](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 Contient des rubriques qui décrivent comment effectuer des transactions locales, des transactions distribuées et travailler avec l'accès concurrentiel optimiste.  
  
 [Extraction des valeurs de champs Identité ou NuméroAuto](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 Propose un exemple de mappage des valeurs générées pour une colonne **Identity** d'une table [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] ou pour un champ **Autonumber** d'une table Microsoft Access, à une colonne d'une ligne insérée dans une table.  Traite de la fusion de valeurs d'identité dans un `DataTable`.  
  
 [Récupération de données binaires](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 Décrit comment extraire des données binaires ou de grosses structures de données à l'aide d'un `CommandBehavior`.`SequentialAccess` afin de modifier le comportement par défaut d'un `DataReader`.  
  
 [Modification de données à l'aide de procédures stockées\)](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 Décrit comment utiliser des paramètres d'entrée et sortie de procédure stockée afin d'insérer une ligne dans une base de données et retourner une nouvelle valeur d'identité.  
  
 [Récupération d'informations de schéma de base de données](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 Décrit la manière d'obtenir des bases de données ou des catalogues disponibles, des tables et des vues dans une base de données, des contraintes existantes pour des tables et d'autres informations de schéma à partir d'une source de données.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Décrit le modèle fabrique de fournisseurs et illustre l'utilisation des classes de base dans l'espace de noms `System.Data.Common`.  
  
 [Traçage de données dans ADO.NET](../../../../docs/framework/data/adonet/data-tracing.md)  
 Décrit la manière dont ADO.NET offre une fonctionnalité intégrée de traçage de données.  
  
 [Compteurs de performance](../../../../docs/framework/data/adonet/performance-counters.md)  
 Décrit les compteurs de performance disponibles pour `SqlClient` et `OracleClient`.  
  
 [Programmation asynchrone](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 Décrit la prise en charge [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] de la programmation asynchrone.  
  
 [Prise en charge de la diffusion en continu pour SqlClient](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 Explique comment écrire des applications qui diffusent en continu les données provenant de [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] sans avoir à les charger complètement en mémoire.  
  
## Voir aussi  
 [Mappages de types de données dans ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)   
 [Objets DataSet, DataTable et DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Sécurisation des applications ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)   
 [SQL Server et ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)