---
title: "Fournisseurs de services de donn&#233;es personnalis&#233;s (WCF Data Services) | Microsoft Docs"
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
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Fournisseurs de services de donn&#233;es personnalis&#233;s (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclut un ensemble de fournisseurs qui vous permet de définir un modèle de données basé sur des types de données à liaison tardive.  
  
|Fournisseur|Description|  
|-----------------|-----------------|  
|Fournisseur de métadonnées|Il s'agit du fournisseur de services de données personnalisé principal qui vous permet de définir pendant l'exécution un modèle de données personnalisé en implémentant l'interface <xref:System.Data.Services.Providers.IDataServiceMetadataProvider>.|  
|Fournisseur de requête|Ce fournisseur vous permet d'exécuter des requêtes sur un modèle de données personnalisé défini à l'aide de l'interface <xref:System.Data.Services.Providers.IDataServiceMetadataProvider>.  Le fournisseur de requête est créé en implémentant l'interface <xref:System.Data.Services.Providers.IDataServiceQueryProvider>.|  
|Fournisseur de mise à jour|Ce fournisseur vous permet d'effectuer des mises à jour sur les types exposés dans un fournisseur de services de données personnalisé et de gérer l'accès concurrentiel.  Un fournisseur de mise à jour est créé en implémentant l'interface <xref:System.Data.Services.Providers.IDataServiceUpdateProvider>|  
|Fournisseur de pagination|Ce fournisseur est utilisé avec le fournisseur de services de données personnalisé pour permettre la prise en charge de la pagination pilotée par le serveur.  Un fournisseur de pagination pour un service de données personnalisé est créé en implémentant l'interface <xref:System.Data.Services.Providers.IDataServicePagingProvider>.|  
|Fournisseur de diffusion en continu|Ce fournisseur vous permet d'exposer des types de données d'objet blob \(binary large object\) sous forme de flux en continu.  Un fournisseur de diffusion en continu est créé en implémentant l'interface <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.  Le fournisseur de diffusion en continu peut également être utilisé avec Entity Framework et des fournisseurs de source de données de réflexion.  Pour plus d'informations, consultez [Fournisseur de diffusion en continu](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).|  
  
 Pour plus d'informations, consultez l'article [Fournisseurs de service de données personnalisé](http://go.microsoft.com/fwlink/?LinkID=186850) et le kit de ressources des fournisseurs [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] dans le [Kit de développement logiciel \(SDK\) OData](http://go.microsoft.com/fwlink/?LinkId=186069).  
  
## Voir aussi  
 [fournisseurs de services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)   
 [Fournisseur Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)   
 [Fournisseur de réflexion](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)