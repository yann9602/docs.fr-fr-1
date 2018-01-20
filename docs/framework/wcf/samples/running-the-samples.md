---
title: "Exécution des exemples Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 603a6dce17d527a3f14e408da19006509514df52
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="running-the-windows-communication-foundation-samples"></a>Exécution des exemples Windows Communication Foundation
Les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] peuvent être exécutés sur un ou plusieurs ordinateurs. Tels qu'ils sont fournis, les exemples sont configurés pour être exécutés sur un ordinateur unique. Pour les exécuter sur plusieurs ordinateurs, il est nécessaire de modifier les paramètres de leur fichier de configuration. Les procédures suivantes permettent d'exécuter les exemples sur un même ordinateur ou sur plusieurs ordinateurs. Notez que ces procédures ne sont pas tout à fait les mêmes pour les exemples hébergés dans les services IIS et les exemples auto-hébergés. La plupart des exemples sont hébergés dans les services IIS. Consultez les informations contenues dans leur fichier lisezmoi respectif pour connaître leurs modalités d'hébergement.  
  
 Sur [!INCLUDE[wv](../../../../includes/wv-md.md)], les exemples non hébergés dans les services IIS nécessitent l'utilisation de droits d'administrateur pour permettre l'enregistrement d'un écouteur à l'aide de Http.sys. Utilisez Httpcfg.exe pour enregistrer les adresses d'écoute du service à l'aide du compte sous lequel le service s'exécute, ou lancez ce même service depuis une invite de commandes s'exécutant sous un compte d'administrateur.  
  
> [!NOTE]
>  Avant la construction ou d’exécution de toute la [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exemples, assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Pour exécuter l'exemple sur le même ordinateur  
  
1.  Si le service est hébergé par IIS, vérifiez son accessibilité à l'aide d'un navigateur en tapant http://localhost/servicemodelsamples/service.svc dans un navigateur. Une page de confirmation doit s'afficher en réponse. Si la page de confirmation n’est pas affichée, consultez [conseils de dépannage](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
2.  Si le service est auto-hébergé, exécutez Service.exe à partir du répertoire \service\bin, situé dans le dossier correspondant à votre langue. L'activité du service s'affiche dans sa fenêtre de console.  
  
3.  Exécutez Client.exe à partir de \client\bin\\, figurant dans le dossier de langue. L'activité du client s'affiche dans sa fenêtre de console.  
  
4.  Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-machines"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1.  Si le service est hébergé par IIS :  
  
    1.  Créez un répertoire virtuel nommé ServiceModelSamples sur l'ordinateur de service. Le fichier de commandes Setupvroot.bat inclus avec [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) peut être utilisé pour créer le répertoire de disque et le répertoire virtuel.  
  
    2.  Copiez les fichiers du programme de service depuis %SystemDrive%\Inetpub\wwwroot\servicemodelsamples vers le répertoire virtuel ServiceModelSamples. Assurez-vous de copier les fichiers dans le répertoire \bin.  
  
    3.  Assurez-vous que le service est accessible depuis l'ordinateur du client en utilisant un navigateur.  
  
     Si le service est auto-hébergé :  
  
    1.  Sur l'ordinateur du service, créez un répertoire afin d'y stocker les fichiers lui correspondant.  
  
    2.  Copiez les fichiers de programme du service figurant dans le dossier \service\bin\ (situé dans le dossier correspondant à votre langue) sur l'ordinateur de service.  
  
    3.  Dans le fichier de configuration du service, modifiez l'adresse de la définition du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service. Remplacez toutes les occurrences de « localhost » de l'adresse par un nom de domaine complet.  
  
    4.  Lancez Service.exe depuis une invite de commandes.  
  
2.  Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l'ordinateur client.  
  
3.  Définissez l'adresse de point de terminaison.  
  
    1.  Si le service ne s'exécute pas sous un compte de domaine, ouvrez le fichier de configuration du client, puis modifiez l'adresse du point de terminaison en fonction de la nouvelle adresse de votre service. Remplacez toutes les occurrences de « localhost » de l'adresse par un nom de domaine complet.  
  
    2.  Si le service s'exécute sous un compte de domaine, régénérez la configuration du client en exécutant Svcutil.exe par rapport au service. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Exécutez Svcutil.exe, consultez [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Utilisez le fichier généré au lieu du fichier de configuration utilisé dans l'exemple. Le fichier de configuration généré contient des informations d'identité supplémentaires et contient tous les paramètres nécessaires à la connexion au point de terminaison du service bien qu'il s'agisse de paramètres par défaut. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]informations d’identité, consultez [l’identité du Service et l’authentification](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), et [ \<identité >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).  
  
4.  Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.  
  
### <a name="to-debug-a-service"></a>Pour déboguer un service  
  
1.  Générer la solution (client et service) à l’aide de la **générer** menu ou CTRL + MAJ + B.  
  
2.  Si le service est hébergé par IIS :  
  
    1.  Activez le service à l'aide d'un navigateur en tapant http://localhost/servicemodelsamples/service.svc.  
  
    2.  Dans la solution, choisissez le **déboguer** menu et **attacher au processus** élément de menu.  
  
    3.  Sélectionnez le **afficher les processus de tous les utilisateurs** case à cocher.  
  
    4.  Sélectionnez le processus de traitement W3wp.exe hôte afin de procéder au débogage (sélectionnez ASPNet_wp.exe sur Windows XP).  
  
3.  Vous pouvez à présent définir des points d'arrêt dans le code de service et activer ces points pour les exceptions.  
  
4.  Cliquez sur l’élément de projet de client et choisissez **déboguer**, **démarrer une nouvelle instance**.  
  
### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
-   Si le service est hébergé par IIS, pour des raisons de sécurité, supprimez la définition du répertoire virtuel ainsi que les autorisations accordées au cours des étapes d'installation (une fois l'exécution des exemples terminée).  
  
## <a name="see-also"></a>Voir aussi  
 [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)  
 [Exécution des exemples dans un groupe de travail et sur plusieurs ordinateurs](http://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113)  
 [Conseils de dépannage](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)
