---
title: "Exposition de vos donn&#233;es comme un service (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mise en route, Services de données WCF"
  - "Services de données WCF, configuration"
  - "Services de données WCF, mise en route"
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Exposition de vos donn&#233;es comme un service (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] s'intègre à Visual Studio pour vous permettre de définir plus facilement des services permettant d'exposer vos données sous forme de flux [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)].  La création d'un service de données qui expose un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] implique les étapes fondamentales suivantes :  
  
1.  **Définir** **le modèle de données**.  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] prend en charge en natif les modèles de données basés sur [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  Pour plus d'informations, consultez [Procédure : créer un service de données à l'aide d'une source de données ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] prend en charge également des modèles de données basés sur les objets du common language runtime \(CLR\) qui retournent une instance de l'interface <xref:System.Linq.IQueryable%601>.  Cela vous permet de déployer des services de données qui sont basés sur des listes, des tableaux et des collections dans .NET Framework. Pour activer la création, la mise à jour et la suppression d'opérations sur ces structures de données, vous devez également implémenter l'interface <xref:System.Data.Services.IUpdatable>.  Pour plus d'informations, consultez [Procédure : créer un service de données à l'aide du fournisseur de réflexion](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
     Pour répondre à des scénarios plus évolués, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclut aussi un jeu de fournisseurs qui vous permet de définir un modèle de données basé sur des types de données à liaison tardive.  Pour plus d'informations, consultez [Fournisseurs de services de données personnalisés](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
2.  **Création du service de données.** Le service de données le plus simple expose une classe qui hérite de la classe <xref:System.Data.Services.DataService%601>, avec un type `T` qui est le nom qualifié par l'espace de noms du conteneur d'entités.  Pour plus d'informations, consultez [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
3.  **Configurer le service de données.** Par défaut, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] désactive l'accès aux ressources exposées par un conteneur d'entités. L'interface <xref:System.Data.Services.DataServiceConfiguration> vous permet de configurer l'accès aux ressources et aux opérations de service, de spécifier la version d'[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prise en charge et de définir d'autres comportements à l'échelle du service, comme les comportements du traitement par lots ou le nombre maximal d'entités qui peuvent être retournées dans une seule réponse. Pour plus d'informations, consultez [Configuration du service de données](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Pour obtenir un exemple sur la manière de créer un service de données simple basé sur l'exemple de base de données Northwind, consultez [Démarrage rapide](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## Voir aussi  
 [Mise en route](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)   
 [Vue d'ensemble](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)