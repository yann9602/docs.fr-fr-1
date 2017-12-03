---
title: "Déploiement d'un service WCF hébergé dans Internet Information Services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9b19e111e11097cbb4b4af60ae0b28956a4a381
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Déploiement d'un service WCF hébergé dans Internet Information Services
Le développement et le déploiement d'un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hébergé dans les services IIS (Internet Information Services) se composent des tâches suivantes :  
  
-   Vérifier que IIS, ASP.NET, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ainsi que le composant d'activation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont installés et inscrits correctement.  
  
-   Créer une application IIS ou réutiliser une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] existante.  
  
-   Créer un fichier .svc pour le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .  
  
-   Déployer l'implémentation de service vers l'application IIS.  
  
-   Configurer le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .  
  
 Pour une procédure pas à pas détaillée de la création d’un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergé dans IIS, consultez [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Vérifier que les services IIS, ASP.NET et WCF sont installés et enregistrés correctement  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les services IIS et ASP.NET doivent être installés pour que les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés dans IIS fonctionnent correctement. Les procédures d'installation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (dans le cadre de [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]), d'ASP.NET et d'IIS varient selon la version du système d'exploitation utilisée. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l’installation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et de [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], consultez [Programme d’installation web de Microsoft .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=201185). Les instructions pour installer les services IIS se trouvent à la page [Installing IIS (Installation d’IIS)](http://go.microsoft.com/fwlink/?LinkId=201188).  
  
 Le processus d'installation pour le [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] enregistre automatiquement [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] auprès des services IIS s'ils sont déjà présents sur l'ordinateur. Si les services IIS sont installés après le [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], une étape supplémentaire est requise pour enregistrer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] auprès des services IIS et de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Pour ce faire, procédez comme suit selon votre système d'exploitation :  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], Windows 7, et [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]: utiliser le [outil d’inscription ServiceModel (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) l’outil pour inscrire [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec IIS : pour utiliser cet outil, tapez **ServiceModelReg.exe /i /x** dans l’invite de commandes Visual Studio. Pour ouvrir cette invite de commandes, cliquez sur le bouton Démarrer, sélectionnez **Tous les programmes**, **Microsoft Visual Studio 2012**, **Visual Studio Tools**et **Invite de commandes Visual Studio**.  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)]: installez le sous-composant Windows Communication Foundation Activation Components du [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]. Pour ce faire, dans le panneau de configuration, cliquez sur **Ajout / Suppression de programmes** , puis **ajouter\/supprimer des composants Windows**. Cette procédure active l' **Assistant Composants de Windows**.  
  
-   Windows 7 :  
  
 Enfin, vous devez vérifier qu'ASP.NET est configuré pour utiliser le .NET Framework version 4. Pour cela, exécutez l'outil ASPNET_Regiis avec l'option –i. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ASP.NET IIS Registration, outil](http://go.microsoft.com/fwlink/?LinkId=201186)  
  
## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Créer une nouvelle application IIS ou réutiliser une application ASP.NET existante  
 Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés dans IIS doivent résider dans une application IIS. Vous pouvez créer une nouvelle application IIS pour héberger des services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exclusivement. Sinon, déployez un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans une application existante qui héberge déjà le contenu [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] (tel que pages .aspx et services Web ASP.NET [ASMX]). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] ces options, consultez les sections « Hébergement côte à côte de WCF avec ASP.NET » et « Hébergement des services WCF en mode de compatibilité ASP.NET » dans [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
 Notez que [!INCLUDE[iis601](../../../../includes/iis601-md.md)] et les versions ultérieures redémarrent périodiquement une application de programmation orientée objet isolée. La valeur par défaut est 1740 minutes. La valeur maximale est de 71,582 minutes. Ce redémarrage peut être désactivé. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] cette propriété, consultez [PeriodicRestartTime](http://go.microsoft.com/fwlink/?LinkId=109968).  
  
## <a name="create-an-svc-file-for-the-wcf-service"></a>Créer un fichier .svc pour le service WCF  
 Les services[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés dans IIS sont représentés sous la forme de fichiers de contenu spéciaux (fichiers .svc) à l'intérieur de l'application IIS. Ce modèle est semblable à la façon dont les pages ASMX sont représentées dans une application IIS sous la forme de fichiers .asmx. Un fichier .svc contient une directive de traitement propre à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]([@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)) qui autorise l’infrastructure d’hébergement [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à activer des services hébergés en réponse à des messages entrants. La syntaxe la plus courante d'un fichier .svc se trouve dans l'instruction suivante.  
  
```  
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>  
```  
  
 Elle se compose de la directive [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) et de l’attribut unique `Service`. La valeur de l'attribut `Service` est le nom de type du Common Language Runtime (CLR) de l'implémentation de service. L'utilisation de cette directive revient essentiellement à créer un hôte de service à l'aide du code suivant :  
  
```  
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );  
```  
  
 La configuration d'hébergement supplémentaire, telle que la création d'une liste d'adresses de base pour le service peut aussi être effectuée. Vous pouvez aussi utiliser un <xref:System.ServiceModel.Activation.ServiceHostFactory> personnalisé pour étendre la directive et l'utiliser avec des solutions d'hébergement personnalisées. Les applications IIS qui hébergent les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne sont pas chargées de gérer la création et la durée de vie des instances <xref:System.ServiceModel.ServiceHost> . L'infrastructure d'hébergement [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] managée crée dynamiquement l'instance <xref:System.ServiceModel.ServiceHost> nécessaire lorsque la première demande est reçue pour le fichier .svc. L'instance n'est pas libérée tant qu'elle n'est pas fermée explicitement par le code ou que l'application est recyclée.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la syntaxe pour les fichiers .svc, consultez [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).  
  
## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Déployer l'implémentation de service vers l'application IIS  
 Les services[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés dans IIS utilisent le même modèle de compilation dynamique que [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]. Comme dans [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], vous pouvez déployer de plusieurs façons le code d'implémentation pour les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés dans IIS à différents emplacements, comme suit :  
  
-   Sous forme d'un fichier .dll précompilé situé dans le cache d'assembly global (GAC, Global Assembly Cache) ou dans le répertoire \bin de l'application. Les binaires précompilés ne sont pas mis à jour tant qu'une nouvelle version de la bibliothèque de classes n'a pas été déployée.  
  
-   Sous la forme de fichiers sources non compilés situés dans le répertoire \App_Code de l'application. Les fichiers sources situés dans ce répertoire sont requis dynamiquement lors du traitement de la première demande de l'application. Les modifications apportées aux fichiers dans le répertoire \App_Code provoque le recyclage et la recompilation de l'application toute entière lorsque la demande suivante est reçue.  
  
-   Sous la forme de code non compilé placé directement dans le fichier .svc. Code d’implémentation peut également être situé inline dans le fichier du service .svc, après la @ServiceHost directive. Les transformations apportées au code inline provoquent le recyclage et la recompilation de l'application lorsque la demande suivante est reçue.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] le modèle de compilation [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] , consultez [Vue d’ensemble de la compilation ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94773).  
  
## <a name="configure-the-wcf-service"></a>Configurer le service WCF  
 Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés dans IIS stockent leur configuration dans le fichier Web.config des applications. Les services hébergés dans IIS utilisent la même syntaxe et les mêmes éléments de configuration que les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés en dehors des services IIS. Toutefois, les contraintes suivantes sont uniques à l'environnement d'hébergement IIS :  
  
-   Adresses de base pour les services hébergés dans IIS.  
  
-   Les applications qui hébergent [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services en dehors d’IIS peuvent contrôler l’adresse de base des services qu’elles hébergent en passant un ensemble de base adresse URI pour le <xref:System.ServiceModel.ServiceHost> constructeur ou en fournissant un [ \<hôte >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) élément dans la configuration du service. Les services hébergés dans IIS n'ont pas la capacité de contrôler leur adresse de base ; l'adresse de base d'un service hébergé dans IIS est l'adresse de son fichier .svc.  
  
### <a name="endpoint-addresses-for-iis-hosted-services"></a>Adresses de point de terminaison pour les services hébergés dans IIS  
 Lorsqu'elles sont hébergées dans IIS, les adresses de point de terminaison sont toujours considérées relatives à l'adresse du fichier .svc qui représente le service. Par exemple, si l'adresse de base d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est http://localhost/Application1/MyService.svc avec la configuration de point de terminaison suivante.  
  
```xml  
<endpoint address="anotherEndpoint" .../>  
```  
  
 Cela fournit un point de terminaison qui peut être atteint à l'adresse "http://localhost/Application1/MyService.svc/anotherEndpoint."  
  
 De la même façon, l'élément de configuration de point de terminaison qui utilise une chaîne vide comme l'adresse relative fournit un point de terminaison accessible à http://localhost/Application1/MyService.svc, qui est l'adresse de base.  
  
```xml  
<endpoint address="" ... />  
```  
  
 Vous devez toujours utiliser des adresses de point de terminaison relatives pour les points de terminaison de service hébergés dans IIS. Indiquer une adresse de point de terminaison qualifiée complète (par exemple, http://localhost/MyService.svc) peut entraîner des erreurs dans le déploiement du service si l'adresse de point de terminaison ne pointe pas vers l'application IIS qui héberge le service exposant le point de terminaison. L'utilisation d'adresses de point de terminaison relatives pour les services hébergés évite ces risques de conflits.  
  
### <a name="available-transports"></a>Transports disponibles  
 Les services[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés dans IIS 5.1 et [!INCLUDE[iis601](../../../../includes/iis601-md.md)] sont limités à l'utilisation de la communication basée sur HTTP. Sur ces plateformes IIS, configurer un service hébergé pour utiliser une liaison non-HTTP entraîne une erreur pendant l'activation du service. Pour [!INCLUDE[iisver](../../../../includes/iisver-md.md)], les transports pris en charge incluent HTTP, Net.TCP, Net.Pipe, Net.MSMQ et msmq.formatname pour la compatibilité descendante avec les applications MSMQ existantes.  
  
### <a name="http-transport-security"></a>Sécurité de transport HTTP  
 Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés dans IIS peuvent utiliser la sécurité de transport HTTP (par exemple, les méthodes d'authentification HTTP et HTTPS telles que l'authentification de base, Digest et intégrée à Windows) à condition que le répertoire virtuel IIS qui contient le service prenne en charge ces paramètres. Les paramètres de la sécurité de transport HTTP sur la liaison d'un point de terminaison hébergé doivent correspondre aux paramètres de sécurité de transport sur le répertoire virtuel IIS qui la contient.  
  
 Par exemple, un point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuré pour utiliser l'authentification Digest HTTP doit résider dans un répertoire virtuel IIS qui est également configuré pour autoriser l'authentification Digest HTTP. Les combinaisons non appariées de paramètres IIS et de paramètres de point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provoquent une erreur pendant l'activation de service.  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement dans Internet Information Services](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Internet Information Services d’hébergement des meilleures pratiques](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Fonctionnalités d’hébergement de Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
