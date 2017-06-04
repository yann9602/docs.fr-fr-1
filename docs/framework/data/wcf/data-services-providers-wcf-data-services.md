---
title: "Fournisseurs de services de donn&#233;es (WCF Data Services) | Microsoft Docs"
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
  - "Services de données WCF, fournisseurs"
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Fournisseurs de services de donn&#233;es (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] prend en charge plusieurs modèles de fournisseur pour exposer des données en tant que flux [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)].  Cette rubrique fournit les informations pour vous permettre de choisir le meilleur fournisseur [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour votre source de données.  
  
## Fournisseurs de sources de données  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] prend en charge les fournisseurs suivants pour définir le modèle de données d'un service de données.  
  
|Fournisseur|Description|  
|-----------------|-----------------|  
|Fournisseur Entity Framework|Ce fournisseur utilise ADO.NET Entity Framework pour vous permettre d'utiliser des données relationnelles avec un service de données en définissant un modèle de données qui est mappé aux données relationnelles.  Votre source de données peut être SQL Server ou toute autre source de données avec un support de fournisseur tiers pour Entity Framework.  Vous devez utiliser le fournisseur Entity Framework lorsque vous avez une source de données relationnelles, telle qu'une base de données SQL Server.  Pour plus d'informations, consultez [Fournisseur Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).|  
|Fournisseur de réflexion|Ce fournisseur utilise la réflexion pour vous permettre de définir un modèle de données basé sur des classes de données existantes qui peuvent être exposées comme des instances de l'interface <xref:System.Linq.IQueryable%601>.  Les mises à jour sont activées en implémentant l'interface <xref:System.Data.Services.IUpdatable>.  Vous devez utiliser ce fournisseur lorsque vous avez des classes de données statiques définies pendant l'exécution, telles que celles générées par LINQ to SQL ou définies par un DataSet typé.  Pour plus d'informations, consultez [Fournisseur de réflexion](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).|  
|Fournisseurs de services de données personnalisés|[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclut un jeu de fournisseurs qui vous permet de définir dynamiquement  un modèle de données basé sur des types de données à liaison tardive.  Vous devez implémenter ces interfaces lorsque les données exposées sont inconnues au moment de la conception de l'application ou lorsque les fournisseurs d'Entity Framework ou de réflexion ne sont pas suffisants.  Pour plus d'informations, consultez [Fournisseurs de services de données personnalisés](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).|  
  
## Autres fournisseurs de services de données  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] possède le fournisseur de services de données supplémentaire suivant qui améliore les performances d'une source de données définie à l'aide de l'un des autres fournisseurs.  
  
|Fournisseur|Description|  
|-----------------|-----------------|  
|Fournisseur de diffusion en continu|Ce fournisseur vous permet d'exposer des types de données d'objet blob \(binary large object\) à l'aide d'[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  Un fournisseur de diffusion en continu est créé en implémentant l'interface <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.  Ce fournisseur peut être implémenté avec n'importe quel fournisseur de sources de données.  Pour plus d'informations, consultez [Fournisseur de diffusion en continu](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).|  
  
## Voir aussi  
 [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [Configuration du service de données](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)   
 [Hébergement du service de données](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)