---
title: "Génération des exemples Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d5de916aa5825625f29efe316571ad5085afb431
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="building-the-windows-communication-foundation-samples"></a>Génération des exemples Windows Communication Foundation
Le [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] exemples peuvent être construites à l’aide de Visual Studio 2010 ou à l’aide de la **msbuild** commande à partir de la ligne de commande. Les deux procédures sont décrites dans cette rubrique.  
  
> [!NOTE]
>  Avant la construction ou d’exécution de toute la [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exemples, assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-build-the-sample-using-a-command-prompt"></a>Pour générer l'exemple à partir d'une invite de commandes  
  
1.  Ouvrez l'invite de commandes de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] avec des privilèges d'administrateur et accédez au sous-répertoire spécifique aux langues situé sous le répertoire d'installation de l'exemple.  
  
2.  Type `msbuild` à la ligne de commande. Les fichiers de programme du client sont générés dans client\bin, et les fichiers de programme du service sont générés dans service\bin. Si le service est hébergé par IIS (Internet Information Services), les fichiers programme du service sont également copiés dans le répertoire servicemodelsamples et dans son sous-répertoire \bin.  
  
> [!NOTE]
>  Vous devez affecter %systemdrive%\inetpub\wwwroot aux listes de contrôle d'accès (ACL) pour accorder des autorisations de modification au compte sous lequel vous vous êtes connecté. Sinon, certains des événements post-build échoueront. Vous pouvez également laisser les listes de contrôle d'accès telles quelles et exécuter l'invite de commandes du Kit de développement logiciel (SDK) en tant qu'administrateur.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Pour générer l'exemple à l'aide de Visual Studio  
  
1.  Si vous utilisez [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 ou Windows Server 2008 R2 et exécutez [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], vous devez exécuter [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] avec des autorisations élevées. Pour ce faire, cliquez sur l’icône dans le menu Démarrer, puis cliquez sur **exécuter en tant qu’administrateur**.  
  
2.  À partir de la **fichier** menu [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], cliquez sur **ouvrir**, puis cliquez sur **projet/Solution**. Accédez au sous-répertoire spécifique aux langues situé sous le répertoire d'installation de l'exemple, puis double-cliquez sur l'icône du fichier .sln pour ouvrir la solution dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  
  
3.  Dans le **générer** menu, sélectionnez **régénérer la Solution**. Les fichiers de programme du client sont générés dans client\bin, et les fichiers de programme du service sont générés dans service\bin. Si le service est hébergé par IIS (Internet Information Services), les fichiers programme du service sont également copiés dans le répertoire servicemodelsamples et dans son sous-répertoire \bin.  
  
> [!NOTE]
>  Vous devez affecter %systemdrive%\inetpub\wwwroot aux listes de contrôle d'accès (ACL) pour accorder des autorisations de modification au compte sous lequel vous vous êtes connecté. Sinon, certains des événements post-build échoueront. Vous pouvez également laisser les listes de contrôle d'accès telles quelles et exécuter l'invite de commandes du Kit de développement logiciel (SDK) ou Visual Studio en tant qu'administrateur. Certaines actions de Visual Studio (tel que l'attachement d'un débogueur au processus de travail ASP.NET) requièrent également des privilèges d'administrateur.  
  
## <a name="setup-batch-files-and-scripts"></a>Scripts et fichiers de commandes d'installation  
 Les fichiers de commandes Setup.exe et Cleanup.exe et les scripts doivent être exécutés à partir d'une invite de commandes de Visual Studio. Plusieurs fichiers d’installation et de nettoyage effectuent des tâches qui requièrent des privilèges d’administrateur et doivent être lancés avec des privilèges d’administrateur.  
  
## <a name="important-security-information-about-metadata-endpoints"></a>Informations de sécurité importantes à propos des points de terminaison de métadonnées  
 Pour empêcher la divulgation involontaire de métadonnées de service potentiellement sensibles, la publication de métadonnées est désactivée par défaut dans la configuration des services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Ce comportement est sécurisé par défaut, mais il signifie également que vous ne pouvez pas utiliser d'outil d'importation de métadonnées (tel que Svcutil.exe) pour générer le code client requis pour appeler le service, à moins que le comportement de publication des métadonnées du service soit activé explicitement dans la configuration. Pour faciliter l’utilisation des exemples, pratiquement tous les exemples exposent un point de terminaison de publication de métadonnées non sécurisé. De tels points de terminaison sont potentiellement disponibles aux consommateurs non authentifiés anonymes et il est nécessaire de se montrer vigilant et de s'assurer que la divulgation publique des métadonnées d'un service est appropriée avant de déployer de tels points de terminaison. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]publication des métadonnées de service, consultez le [comportement de publication de métadonnées](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md) exemple. Consultez le [personnalisé sécuriser les métadonnées de point de terminaison](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample pour obtenir un exemple de sécurisation d’un point de terminaison de métadonnées.  
  
## <a name="exception-handling"></a>Gestion des exceptions  
 En général, ces exemples n'incluent pas la gestion des exceptions pour que le code reste axé sur le sujet de l'exemple. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]gestion des exceptions, consultez la [attendu des Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) exemple.  
  
## <a name="regenerating-clients-and-configuration-with-svcutil"></a>Régénération des clients et de la configuration avec Svcutil  
 Vous pouvez utiliser la [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour régénérer le code client et configuration pour la plupart des exemples. Certains exemples nécessitent une modification manuelle de la configuration. Par exemple, si vous utilisez Svcutil.exe pour régénérer la configuration d'un exemple qui utilise des informations d'identification de certificat client, vous devez spécifier manuellement les informations d'identification précédemment configurées. Certains exemples utilisent des options Svcutil.exe spécifiques pour affecter le code généré ; ces options sont spécifiées dans les rubriques d'exemple spécifiques.  
  
#### <a name="to-regenerate-the-client-and-configuration-files"></a>Pour régénérer les fichiers du client et les fichiers de configuration  
  
1.  Ouvrez une invite de commandes du Kit de développement SDK et accédez au sous-répertoire spécifique aux langues situé sous l'emplacement d'installation de l'exemple.  
  
2.  Si le service est un type hébergé sur le Web, utilisez la commande suivante.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     Si le service est un type auto-hébergé, utilisez la commande suivante.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     Remplacez http://localhost:8000/ServiceModelSamples/service.svc/mex par l'adresse du point de terminaison mex du service auto-hébergé.  
  
     Pour générer le client dans un type Visual Basic, utilisez la commande suivante.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
     Si le service est un type auto-hébergé, utilisez la commande suivante.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
    > [!NOTE]
    >  Pour ignorer la génération de la configuration du client ajouter la **/noConfig** option.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md)  
 [Outil ServiceModel Metadata Utility (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
