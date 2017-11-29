---
title: "Hébergement du service de données (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6a11e7e499f705f4aace791320057e04205db58c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="hosting-the-data-service-wcf-data-services"></a>Hébergement du service de données (services de données WCF)
À l’aide de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez créer un service qui expose des données en tant qu’un [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] de flux. Ce service de données est défini comme une classe qui hérite de <xref:System.Data.Services.DataService%601>. Cette classe fournit la fonctionnalité requise pour traiter les messages de demande, effectuer des mises à jour par rapport à la source de données et générer des messages de réponses, comme requis par [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Toutefois, un service de données ne peut pas lier à et écouter sur un socket de réseau pour les requêtes HTTP entrantes. Pour ces fonctionnalités requises, le service de données s'appuie sur un composant d'hébergement.  
  
 L'hôte du service de données effectue les tâches suivantes pour le compte du service de données :  
  
-   Écoute les demandes et les transmet au service de données.  
  
-   Crée une instance du service de données pour chaque demande.  
  
-   Demande au service de données de traiter la requête entrante.  
  
-   Envoie la réponse de la part du service de données.  
  
 Pour simplifier l’hébergement d’un service de données, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] est conçu pour s’intégrer avec Windows Communication Foundation (WCF). Le service de données fournit une implémentation WCF par défaut qui sert à l’hôte de service de données dans un [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application. Vous pouvez donc héberger un service de données de l'une des façons suivantes :  
  
-   Dans une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
-   Dans une application managée qui prend en charge des services WCF auto-hébergés.  
  
-   Dans un autre hôte de service de données personnalisé.  
  
## <a name="hosting-a-data-service-in-an-aspnet-application"></a>Hébergement de services de données dans une application ASP.NET  
 Lorsque vous utilisez la **ajouter un nouvel élément** boîte de dialogue dans Visual Studio pour définir un service de données dans une application ASP.NET, l’outil génère deux nouveaux fichiers dans le projet. Le premier fichier a une extension `.svc` et indique à l'exécution WCF comment instancier le service de données. Voici un exemple de ce fichier pour le service de données exemple Northwind créé lorsque vous effectuez la [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):  
  
```  
<%@ ServiceHost Language="C#"   
    Factory="System.Data.Services.DataServiceHostFactory,   
            System.Data.Services, Version=4.0.0.0,   
            Culture=neutral, PublicKeyToken=b77a5c561934e089"   
    Service="NorthwindService.Northwind" %>   
```  
  
 Cette directive dit à l'application de créer l'hôte de service pour la classe de service de données nommée en utilisant la classe <xref:System.Data.Services.DataServiceHostFactory>.  
  
 La page code-behind du fichier `.svc` contient la classe constituant l'implémentation du service de données lui-même, défini comme suit dans le cas de l'exemple de service de données Northwind :  
  
 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
 Puisqu'un service de données se comporte comme un service WCF, le service de données s'intègre avec [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et suit le modèle de programmation Web WCF. Pour plus d’informations, consultez [Services WCF et ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) et [modèle de programmation WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).  
  
## <a name="self-hosted-wcf-services"></a>Services WCF auto-hébergés  
 Car il intègre une implémentation WCF, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] auto-héberger un service de données comme un service WCF. Un service peut être auto-hébergé dans une application [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], par exemple une application console. La classe <xref:System.Data.Services.DataServiceHost>, qui hérite de <xref:System.ServiceModel.Web.WebServiceHost>, est utilisée pour instancier le service de données à une adresse spécifique.  
  
 L'auto-hébergement peut être utilisé pour le développement et les tests parce qu'elle permet de simplifier le déploiement et le dépannage du service. Toutefois, ce type d'hébergement ne fournit pas les fonctionnalités avancées d'hébergement et de gestion offertes par [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ou par les services Internet (IIS). Pour plus d’informations, consultez [hébergement dans une Application gérée](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).  
  
## <a name="defining-a-custom-data-service-host"></a>Définition d'un hôte de service de données personnalisé  
 Dans les cas où l'implémentation hôte de WCF est trop restrictive, vous pouvez également définir un hôte personnalisé pour un service de données. Toute classe qui implémente l'interface <xref:System.Data.Services.IDataServiceHost> peut être utilisée comme hôte de réseau pour un service de données. Un hôte personnalisé doit implémenter l'interface <xref:System.Data.Services.IDataServiceHost> et pouvoir gérer les responsabilités de base suivantes de l'hôte de service de données :  
  
-   Fournir le service de données avec le chemin d'accès racine du service.  
  
-   Traiter les informations d'en-tête de demande et de réponse à l'implémentation appropriée du membre <xref:System.Data.Services.IDataServiceHost>.  
  
-   Gérer les exceptions déclenchées par le service de données.  
  
-   Valider les paramètres de la chaîne de requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Exposition de vos données en tant que Service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)  
 [Configuration du Service de données](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
