---
title: "H&#233;bergement du service de donn&#233;es (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "HTML"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Services de données WCF, configuration"
  - "Services de données WCF, Windows Communication Foundation"
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# H&#233;bergement du service de donn&#233;es (WCF Data Services)
En utilisant [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez créer un service qui expose des données sous forme de flux [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)].  Ce service de données est défini comme une classe qui hérite de <xref:System.Data.Services.DataService%601>.  Cette classe fournit les fonctionnalités requises pour traiter les messages de demande, exécuter des mises à jour par rapport à la source de données, et générer des messages de réponses, comme demandé par [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Toutefois, un service de données ne peut pas effectuer la liaison et écouter des requêtes HTTP entrantes sur un socket de réseau.  Pour ces fonctionnalités requises, le service de données s'appuie sur un composant d'hébergement.  
  
 L'hôte du service de données effectue les tâches suivantes pour le compte du service de données :  
  
-   Écoute les demandes et les transmet au service de données.  
  
-   Crée une instance du service de données pour chaque demande.  
  
-   Demande au service de données de traiter la requête entrante.  
  
-   Envoie la réponse de la part du service de données.  
  
 Pour simplifier l'hébergement d'un service de données, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] est conçu pour s'intégrer avec Windows Communication Foundation \(WCF\).  Le service de données fournit une implémentation WCF par défaut qui fait office d'hôte de service de données dans une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  Vous pouvez donc héberger un service de données de l'une des façons suivantes :  
  
-   Dans une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
-   Dans une application managée qui prend en charge des services WCF auto\-hébergés.  
  
-   Dans un autre hôte de service de données personnalisé.  
  
## Hébergement de services de données dans une application ASP.NET  
 Lorsque vous utilisez la boîte de dialogue **Ajouter un nouvel élément** de Visual Studio pour définir un service de données dans une application ASP.NET, l'outil génère deux nouveaux fichiers dans le projet.  Le premier fichier a une extension `.svc` et indique à l'exécution WCF comment instancier le service de données.  Voici un exemple de ce fichier pour le service de données d'exemple Northwind créé lorsque vous effectuez le [démarrage rapide](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) :  
  
```  
<%@ ServiceHost Language="C#"   
    Factory="System.Data.Services.DataServiceHostFactory,   
            System.Data.Services, Version=4.0.0.0,   
            Culture=neutral, PublicKeyToken=b77a5c561934e089"   
    Service="NorthwindService.Northwind" %>   
```  
  
 Cette directive dit à l'application de créer l'hôte de service pour la classe de service de données nommée en utilisant la classe <xref:System.Data.Services.DataServiceHostFactory>.  
  
 La page code\-behind du fichier `.svc` contient la classe constituant l'implémentation du service de données lui\-même, défini comme suit dans le cas de l'exemple de service de données Northwind :  
  
 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
 Puisqu'un service de données se comporte comme un service WCF, le service de données s'intègre avec [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et suit le modèle de programmation Web WCF. Pour plus d'informations, consultez [Services WCF et ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) et [Modèle de programmation HTTP Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).  
  
## Services WCF auto\-hébergés  
 Puisqu'il intègre une implémentation WCF, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] peut auto\-héberger un service de données sous forme de service WCF.  Un service peut être auto\-hébergé dans une application [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], par exemple une application console.  La classe <xref:System.Data.Services.DataServiceHost>, qui hérite de <xref:System.ServiceModel.Web.WebServiceHost>, est utilisée pour instancier le service de données à une adresse spécifique.  
  
 L'auto\-hébergement peut être utilisé pour le développement et les tests parce qu'elle permet de simplifier le déploiement et le dépannage du service.  Toutefois, ce type d'hébergement ne comporte pas les fonctionnalités d'hébergement et de gestion avancées fournies par [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ou Internet Information Services \(IIS\). Pour plus d'informations, consultez [Hébergement dans une application managée](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).  
  
## Définition d'un hôte de service de données personnalisé  
 Dans les cas où l'implémentation hôte de WCF est trop restrictive, vous pouvez également définir un hôte personnalisé pour un service de données.  Toute classe qui implémente l'interface <xref:System.Data.Services.IDataServiceHost> peut être utilisée comme hôte de réseau pour un service de données.  Un hôte personnalisé doit implémenter l'interface <xref:System.Data.Services.IDataServiceHost> et pouvoir gérer les responsabilités de base suivantes de l'hôte de service de données :  
  
-   Fournir le service de données avec le chemin d'accès racine du service.  
  
-   Traiter les informations d'en\-tête de demande et de réponse à l'implémentation appropriée du membre <xref:System.Data.Services.IDataServiceHost>.  
  
-   Gérer les exceptions déclenchées par le service de données.  
  
-   Valider les paramètres de la chaîne de requête.  
  
## Voir aussi  
 [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [Exposition de vos données comme un service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)   
 [Configuration du service de données](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)