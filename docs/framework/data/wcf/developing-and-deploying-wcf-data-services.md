---
title: "D&#233;velopper et d&#233;ployer WCF Data Services | Microsoft Docs"
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
  - "WCF Data Services, développement"
  - "WCF Data Services, déploiement"
  - "déploiement [WCF Data Services"
  - "développement d'applications [WCF Data Services]"
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# D&#233;velopper et d&#233;ployer WCF Data Services
Cette rubrique fournit des informations sur le développement et le déploiement de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Pour des informations générales sur [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], consultez [Mise en route](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md) et [Vue d'ensemble](../../../../docs/framework/data/wcf/wcf-data-services-overview.md).  
  
## Développement de WCF Data Services  
 Lorsque vous utilisez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour créer un service de données qui prend en charge [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], vous devez exécuter les tâches de base suivantes dans le cadre du développement :  
  
1.  **Définir le modèle de données**  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] prend en charge plusieurs fournisseurs de service de données qui vous permettent de définir un modèle basé sur des données provenant de plusieurs sources, dont des bases de données relationnelles et des types de données à liaison tardive. Pour plus d'informations, consultez [fournisseurs de services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
2.  **Créer le service de données**  
  
     Le service de données le plus basique expose une classe qui hérite de la classe <xref:System.Data.Services.DataService%601>, avec un type `T` qui est le nom qualifié par l'espace de noms du conteneur d'entités. Pour plus d'informations, consultez [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
3.  **Configurer le service de données**  
  
     Par défaut, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] désactive l'accès aux ressources exposées par un conteneur d'entités. L'interface <xref:System.Data.Services.DataServiceConfiguration> vous permet de configurer l'accès aux ressources et opérations de service, de spécifier la version d'[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prise en charge et de définir d'autres comportements à l'échelle du service, tels que les comportements de traitement par lot ou le nombre maximal d'entités qui peuvent être retournées dans un flux de réponse unique. Pour plus d'informations, consultez [Configuration du service de données](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Cette rubrique traite principalement du développement et du déploiement des services de données à l'aide de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Pour plus d'informations sur la flexibilité donnée par [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour exposer vos données en tant que flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], consultez [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
### Choix d'un serveur Web de développement  
 Lorsque vous déployez un service WCF Data Service comme une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ou un site Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] à l'aide de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], vous avez le choix entre plusieurs serveurs Web sur lesquels exécuter le service de données pendant le développement. Les serveurs Web suivants s'intègrent à [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] pour faciliter le test et le débogage de vos services de données sur l'ordinateur local.  
  
1.  **Serveur IIS local**  
  
     Lorsque vous créez un service de données qui est une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ou un site Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] exécuté sur Internet Information Services \(IIS\), nous vous recommandons de développer et tester votre service de données à l'aide d'IIS sur l'ordinateur local. L'exécution du service de données sur IIS facilite le suivi des demandes HTTP pendant le débogage. Elle permet également de prédéfinir les droits requis par IIS pour accéder aux fichiers, aux bases de données et aux autres ressources requises par le service de données. Pour exécuter votre service de données sur IIS, vous devez vous assurer qu'IIS et [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sont installés et configurés correctement et accorder aux comptes IIS l'accès au système de fichiers et aux bases de données. Pour plus d'informations, consultez [Procédure : développer un WCF Data Service qui fonctionne sur IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
    > [!NOTE]
    >  Vous devez exécuter [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] avec des droits d'administration afin que l'environnement de développement puisse configurer le serveur IIS local.  
  
2.  **Serveur de développement Visual Studio**  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] inclut un serveur Web intégré, le serveur de développement [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] qui est le serveur Web par défaut des projets [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Ce serveur Web est conçu pour exécuter les projets [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sur l'ordinateur local pendant le développement. Le [démarrage rapide de WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) explique comment créer un service de données qui s'exécute dans le serveur de développement [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
     Vous devez tenir compte des limitations suivantes lorsque vous utilisez le serveur de développement [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] pour développer le service de données :  
  
    -   Ce serveur est uniquement accessible sur l'ordinateur local.  
  
    -   Ce serveur écoute sur `localhost` et sur un port spécifique, non sur le port 80, qui est le port par défaut des messages HTTP. Pour plus d'informations, voir [Serveurs web dans Visual Studio pour les projets web ASP.NET](http://msdn.microsoft.com/fr-fr/31d4f588-df59-4b7e-b9ea-e1f2dd204328).  
  
    -   Ce serveur exécute le service de données dans le contexte de votre compte utilisateur actuel. Par exemple, si vous êtes un utilisateur avec un niveau d'administrateur, un service de données s'exécutant dans le serveur de développement [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] aura des privilèges d'administrateur. Par conséquent, le service de données pourra accéder à des ressources pour lesquelles il ne possède pas de droits d'accès si déployé sur un serveur IIS.  
  
    -   Ce serveur n'inclut pas les fonctionnalités supplémentaires d'IIS, telles que l'authentification.  
  
    -   Il ne peut pas gérer les flux HTTP envoyés par défaut par le client [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] lors de l'accès à des volumes de données binaires importants à partir du service de données. Pour plus d'informations, consultez [Fournisseur de diffusion en continu](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
    -   Ce serveur a des difficultés à traiter le caractère « point » \(`.`\) dans une URL, même si ce caractère est pris en charge par [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dans les valeurs clés.  
  
    > [!TIP]
    >  Même si vous pouvez utiliser le serveur de développement [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] pour tester vos services de données pendant le développement, vous devez à nouveau les tester après leur déploiement sur un serveur Web qui exécute IIS.  
  
3.  **Environnement de développement Microsoft Azure**  
  
     Microsoft Azure Tools pour [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] inclut un ensemble intégré d'outils pour développer les services Microsoft Azure dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Avec ces outils, vous pouvez développer un service de données pouvant être déployé sur Microsoft Azure, et vous pouvez le tester sur l'ordinateur local avant son déploiement. Utilisez ces outils si vous vous servez de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] pour développer un service de données qui s'exécute sur la plateforme Microsoft Azure. Vous pouvez télécharger les outils Microsoft Azure pour [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] à partir du [Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkID=201848).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] le développement d’un service de données qui s’exécute sur Microsoft Azure, consultez la publication [Deploying an OData Service in Windows Azure](http://go.microsoft.com/fwlink/?LinkId=201847)\(Déploiement d’un service OData sur Microsoft Azure\).  
  
### Conseils de développement  
 Vous devez tenir compte de ce qui suit lorsque vous développez un service de données :  
  
-   Définissez les conditions de sécurité de votre service de données si vous planifiez d'utiliser des utilisateurs authentifiés ou un accès restreint pour des utilisateurs spécifiques. Pour plus d'informations, consultez [Sécurisation de WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
-   Un programme d'inspection HTTP peut être très utile pour le débogage d'un service de données, car il vous permet d'inspecter le contenu des messages de demande et de réponse. N'importe quel analyseur de paquets réseau en mesure d'afficher des paquets bruts peut être utilisé pour inspecter des demandes et des réponses HTTP à partir du service de données.  
  
-   Lorsque vous déboguez un service de données, il est plus utile d'obtenir des informations sur l'erreur à partir du service de données que dans le cadre d'un fonctionnement normal. Pour obtenir davantage d'informations sur l'erreur à partir du service de données, affectez à la propriété <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> dans <xref:System.Data.Services.DataServiceConfiguration> la valeur `true` et affectez à la propriété <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> de l'attribut <xref:System.ServiceModel.Description.ServiceDebugBehavior> sur la classe de service de données la valeur `true`.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] sur la publication [Debugging WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=201868) \(Débogage de WCF Data Services\). Vous pouvez aussi activer le traçage dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour afficher les exceptions levées dans la couche de messages HTTP. Pour plus d'informations, consultez [Configuration du suivi](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
-   Un service de données est généralement développé comme un projet d'application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], mais vous pouvez également créer votre service de données comme un projet de site Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Pour plus d’informations sur les différences entre les deux types de projets, consultez la page [NIB : Projets d’application web et projets de site web dans Visual Studio](http://msdn.microsoft.com/fr-fr/2861815e-f5a2-4378-a2f8-b8a86dc012f5).  
  
-   Lorsque vous créez un service de données à l'aide de la boîte de dialogue **Ajouter un nouvel élément** dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], le service de données est hébergé par [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dans IIS. Tandis que [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et IIS sont l'hôte par défaut d'un service de données, d'autres options d'hébergement sont prises en charge. Pour plus d'informations, consultez [Hébergement du service de données](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md).  
  
## Déploiement de WCF Data Services  
 WCF Data Service permet de choisir le processus qui héberge le service de données. Vous pouvez utiliser [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] pour déployer un service de données sur les plateformes suivantes :  
  
-   **Serveur Web hébergé par IIS**  
  
     Lorsqu'un service de données est développé en tant que projet [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], il peut être déployé sur un serveur Web IIS à l'aide des processus de déploiement standard [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] fournit les technologies suivantes de déploiement pour [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], selon le type de projet [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] qui héberge le service de données que vous déployez.  
  
    -   **Technologies de déploiement des applications Web ASP.NET**  
  
        -   [Package de déploiement Web](http://msdn.microsoft.com/fr-fr/1f9713c8-9540-494c-b80d-9893b970ad6f)  
  
        -   [publication en un clic](http://msdn.microsoft.com/fr-fr/59226246-99ad-4aec-975d-7c61e8a8911c)  
  
    -   **Technologies de déploiement des sites Web ASP.NET**  
  
        -   [Outil Copier le site Web](../Topic/How%20to:%20Deploy%20a%20Web%20Site%20Project%20by%20using%20the%20Copy%20Web%20Site%20Tool.md)  
  
        -   [Outil Publier le site Web](../Topic/How%20to:%20Deploy%20a%20Web%20Site%20Project%20by%20Using%20the%20Publish%20Web%20Site%20Tool.md)  
  
        -   [XCopy](../Topic/Walkthrough:%20Deploying%20a%20Web%20Site%20Project%20by%20Using%20XCOPY.md)  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les options de déploiement associées à une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], consultez la page [Vue d’ensemble sur le déploiement de projet d’application web pour Visual Studio et ASP.NET](http://msdn.microsoft.com/fr-fr/99bd1927-b59f-4e02-87b4-55c6ba2adbc3).  
  
    > [!TIP]
    >  Avant de tenter de déployer le service de données sur IIS, testez le déploiement sur un serveur Web qui exécute IIS. Pour plus d'informations, consultez [Procédure : développer un WCF Data Service qui fonctionne sur IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
-   **Windows Azure**  
  
     Vous pouvez déployer un service de données sur Microsoft Azure à l'aide de Microsoft Azure Tools pour [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Vous pouvez télécharger les outils Microsoft Azure pour [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] à partir du [Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkID=201848).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] le déploiement d’un service de données sur Microsoft Azure, consultez la publication [Deploying an OData Service in Windows Azure](http://go.microsoft.com/fwlink/?LinkId=201847)\(Déploiement d’un service OData sur Microsoft Azure\).  
  
### Points à prendre en considération pour le déploiement  
 Vous devez tenir compte de ce qui suit lorsque vous déployez un service de données :  
  
-   Lorsque vous déployez un service de données qui utilise le fournisseur [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] pour accéder à une base de données SQL Server, vous devrez peut\-être propager des structures de données, des données, ou les deux à votre déploiement de service de données.[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] peut créer automatiquement des scripts \(fichiers .sql\) pour faire cela dans la base de données de destination, et ces scripts peuvent être inclus dans le package de déploiement Web d'une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Pour plus d’informations, consultez la page [NIB : Comment : déployer une base de données avec un projet d’application web](http://msdn.microsoft.com/fr-fr/683b33f1-8a3d-45cf-af6e-61ab50fc518b). Pour un site Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], vous pouvez utiliser l'**Assistant Publication de base de données** dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Pour plus d'informations, consultez [Deploying a Database by Using the Database Publishing Wizard](../Topic/Deploying%20a%20Database%20by%20Using%20the%20Database%20Publishing%20Wizard.md).  
  
-   Étant donné que [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclut une implémentation de base d'[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous pouvez utiliser Windows Server AppFabric pour surveiller un service de données déployé sur IIS qui s'exécute sur Windows Server.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] l’utilisation de Windows Server AppFabric pour surveiller un service de données, consultez la publication [Tracking WCF Data Services with Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=202005)\(Suivi de WCF Data Services avec Windows Server AppFabric\).  
  
## Voir aussi  
 [Hébergement du service de données](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)   
 [Sécurisation de WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)   
 [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)