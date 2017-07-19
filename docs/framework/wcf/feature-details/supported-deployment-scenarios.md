---
title: "Sc&#233;narios de d&#233;ploiement pris en charge | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
caps.latest.revision: 20
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 20
---
# Sc&#233;narios de d&#233;ploiement pris en charge
Le sous\-ensemble des fonctionnalités [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] prises en charge pour une utilisation dans des applications d'un niveau de confiance partiel est conçu pour répondre aux spécifications de certains, mais pas tous, scénarios destinés à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Sur le serveur, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] répond aux spécifications des fournisseurs d'hébergement partagé à l'échelle d'Internet qui exécutent des applications tierces dans le jeu d'autorisations de confiance moyenne [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] définies pour des raisons de sécurité. Sur le client, la prise en charge de la confiance partielle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est conçue pour répondre aux spécifications des technologies de déploiement telles que le [ClickOnce Deployment](http://go.microsoft.com/fwlink/?LinkId=83712) \(Déploiement ClickOnce\) ou la technologie d’application du navigateur XAML de [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] qui autorise un déploiement transparent et sécurisé d’applications bureautiques à partir de sites non fiables.  
  
## Autorisations minimales requises  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge un sous\-ensemble de fonctionnalités dans les applications qui s'exécutent sous les jeux d'autorisations nommés standard suivants :  
  
-   Autorisations de confiance moyenne  
  
-   Autorisations de la zone Internet  
  
 Toute tentative d'utilisation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans des applications d'un niveau de confiance partiel avec des autorisations plus restrictives peut provoquer des exceptions de sécurité au cours de l'exécution.  
  
 Pour plus d’informations sur les fonctionnalités prises en charge dans ces jeux d’autorisations, consultez [Compatibilité des fonctionnalités dans un environnement de confiance partielle](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## Confiance partielle sur le serveur  
 De nombreux fournisseurs commerciaux de services d'hébergement d'application Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] exigent que les applications qui s'exécutent sur leurs serveurs s'exécutent dans le jeu d'autorisations de confiance moyenne [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]. Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent s'exécuter dans ces environnements s'ils utilisent <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WebHttpBinding> ou <xref:System.ServiceModel.WsHttpBinding> avec la sécurité au niveau du transport.  
  
 Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui s'exécutent dans les environnements d'hébergement de confiance moyenne peuvent également fonctionner comme services de couche intermédiaire en envoyant des messages à d'autres serveurs en réponse aux demandes du client. Les scénarios de couche intermédiaire sur le serveur sont pris en charge si l'environnement d'hébergement a accordé le <xref:System.Net.WebPermission> approprié à l'application pour effectuer des demandes sortantes vers le serveur souhaité.  
  
 En plus de la messagerie SOAP qui utilise l'une des liaisons SOAP prises en charge, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge le <xref:System.ServiceModel.WebHttpBinding> pour construire des services de style Web dans des applications d'un niveau de confiance partiel. Les fonctionnalités [Modèle de programmation HTTP Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md), [Syndication WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md) et [Intégration d'AJAX et prise en charge de JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md) de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont toutes prises en charge dans la confiance partielle.  
  
 Les services de workflow requièrent des autorisations de confiance totale et ne peuvent pas être utilisés dans les applications de confiance partielle.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [How to: Use Medium Trust in ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=84603) \(Comment : utiliser la confiance moyenne dans ASP.NET 2.0\).  
  
## Confiance partielle sur le client  
 Certaines précautions de sécurité doivent être prises lors du téléchargement et de l'exécution du code à partir de sites Internet non fiables. La technologie [ClickOnce Deployment](http://go.microsoft.com/fwlink/?LinkId=83712) \(Déploiement ClickOnce\) et la technologie d’application du navigateur XAML \(XBAP\) de [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] utilisent la confiance de niveau partiel pour accorder des autorisations limitées \(zone Internet\) au code non fiable.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut être utilisé pour communiquer avec des serveurs distants à partir d’applications d’un niveau de confiance partiel déployées par l’une et l’autre technologie [ClickOnce Deployment](http://go.microsoft.com/fwlink/?LinkId=83712) \(Déploiement ClickOnce\) ou XBAP. Le jeu d’autorisations de la zone Internet inclut <xref:System.Net.WebPermission> pour l’hôte d’origine, ce qui autorise ces applications à communiquer avec leur serveur d’origine à l’aide de n’importe laquelle des liaisons [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prises en charge décrites dans [Compatibilité des fonctionnalités dans un environnement de confiance partielle](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## Voir aussi  
 [Sécurité d'accès du code](http://go.microsoft.com/fwlink/?LinkId=83717)   
 [Vue d’ensemble des applications Windows Presentation Foundation hébergées par un navigateur](http://go.microsoft.com/fwlink/?LinkId=98397)   
 [Confiance partielle](../../../../docs/framework/wcf/feature-details/partial-trust.md)   
 [Confiance moyenne ASP.Net](http://go.microsoft.com/fwlink/?LinkId=69328)