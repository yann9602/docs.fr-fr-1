---
title: "Exposition de vos données comme service (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 122d05d5e4bd7690f32b22453dccbfaab2fb7f13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="exposing-your-data-as-a-service-wcf-data-services"></a>Exposition de vos données comme service (services de données WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]s’intègre à Visual Studio pour vous permettre de définir plus facilement des services permettant d’exposer vos données en tant que [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] flux. Création d’un service de données qui expose un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux implique les étapes de base suivantes :  
  
1.  **Définir** **le modèle de données**. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]en mode natif prend en charge les modèles de données qui sont basées sur les [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md). Pour plus d’informations, consultez [procédure : création d’un Service de données à l’aide d’une Source de données ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] prend en charge également des modèles de données basés sur les objets du common language runtime (CLR) qui retournent une instance de l'interface <xref:System.Linq.IQueryable%601>. Vous pouvez ainsi déployer des services de données basés sur les listes, les tableaux et les collections du .NET Framework. Pour permettre les opérations de création, lecture, mise à jour et suppression sur ces structures de données, vous devez également implémenter l'interface <xref:System.Data.Services.IUpdatable>. Pour plus d’informations, consultez [Comment : créer un Service de données à l’aide du fournisseur de réflexion](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
     Pour des scénarios plus avancés, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclut un ensemble de fournisseurs qui vous permettent de définir un modèle de données basé sur les types de données de la liaison tardive. Pour plus d’informations, consultez [fournisseurs de services de données personnalisé](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
2.  **Créer le service de données.** Le service de données le plus basique expose une classe qui hérite de la classe <xref:System.Data.Services.DataService%601> , avec un type `T` qui est le nom qualifié par l'espace de noms du conteneur d'entités. Pour plus d'informations, consultez [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
3.  **Configurer le service de données.** Par défaut, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] désactive l'accès aux ressources exposées par un conteneur d'entités. L'interface <xref:System.Data.Services.DataServiceConfiguration> vous permet de configurer l'accès aux ressources et opérations de service, de spécifier la version d'[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prise en charge et de définir d'autres comportements à l'échelle du service, tels que les comportements de traitement par lot ou le nombre maximal d'entités qui peuvent être retournés dans une réponse unique. Pour plus d’informations, consultez [configuration du Service de données](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Pour obtenir un exemple montrant comment créer un service de données simple qui repose sur la base de données Northwind, consultez [Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [Vue d’ensemble](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)
