---
title: "Publication du service WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e3d86153d4192e04e55fb9e99ef588b45511560
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-service-publishing"></a>Publication du service WCF
La Publication de service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] vous aide à progresser de l'environnement des premières phases de développement fourni par l'hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] au déploiement proprement dit de l'application dans un environnement de production aux fins de test. Avant de vous engager dans un plan de déploiement final, vous pouvez utiliser la Publication de service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] pour vérifier que votre service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] s'exécute correctement et est prêt à être publié. Vous pouvez également choisir de déployer vos bibliothèques de services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] à différents emplacements cibles en vue de les tester.  
  
## <a name="supported-services-and-target-locations"></a>Services pris en charge et emplacements cibles  
 La Publication de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] prend en charge la publication des services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] créés à partir du jeu de modèles de la bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et leurs modèles d'élément correspondants, dont :  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Modèle de bibliothèque du service avec le modèle d'élément.  
  
-   Bibliothèque du service de syndication.  
  
 Vous trouverez ces modèles de service en choisissant **fichier** -> **nouveau projet** -> **Visual Basic** ou **Visual C#**  ->  **WCF**. Pour les autres modèles WCF dans cet emplacement (y compris l’Application de Service de Workflow WCF et d’Application de Service WCF), vous pouvez publier à l’aide de [pour les applications web de publication en un clic](https://msdn.microsoft.com/en-us/library/dd465337\(v=vs.110\).aspx).  
  
 Le service peut être publié aux emplacements cibles suivants.  
  
-   IIS local  
  
-   Système de fichiers  
  
-   Site FTP  
  
## <a name="using-wcf-service-publishing"></a>Utilisation de la publication de service WCF  
 Pour déployer une implémentation de service, procédez comme suit :  
  
1.  Ouvrez Visual Studio avec des privilèges élevés (cliquez sur le fichier exécutable et utiliser « Exécuter en tant qu’administrateur » pour le lancer).  Si vous utilisez IIS 7.0 ou version ultérieure, assurez-vous que vous avez installé le composant de « IIS avec la métabase et compatibilité IIS 6 Configuration » à l’aide de « » ou désactiver des fonctionnalités activer Windows » dans le panneau de configuration.  
  
2.  Ouvrez un projet de service, sélectionnez **générer**->**publier \<nom du projet >** dans le menu principal, ou cliquez sur le projet dans **l’Explorateur de solutions**sur **publier**.  
  
3.  Le **publier** fenêtre s’affiche. Cliquez sur le **...** . pour spécifier l'emplacement cible où doit être déployé le service. Vous pouvez sélectionner pour déployer l’application à IIS local, système de fichiers ou FTP Site. Si vous déployez l’application sur le serveur IIS local, vous pouvez sélectionner votre site Web et créez votre application web au-dessous, en cliquant sur le **créer une Application Web** icône dans l’angle supérieur droit.  
  
4.  Après avoir cliqué sur **publier** dans la fenêtre principale, Visual Studio déploie l’application à l’emplacement cible indiqué et copie les fichiers Web.config, .svc et l’assembly dans le répertoire cible. . Le nom du fichier .svc doit être « ProjectName.ServiceName.svc ». Une fois que le service est publié avec succès, vous trouverez un lien hypertexte dans la fenêtre Sortie de Visual Studio, qui est similaire à « Connexion au lien hypertexte « http://localhost/WebApplicationFolderName » http://localhost/WebApplicationFolderName... ». Vous pouvez appuyer sur Ctrl et cliquer sur le lien pour ouvrir une page du navigateur dans Visual Studio afin d'afficher la structure des répertoires du service.  
  
     S'il est impossible de visiter le site, l'explorateur de répertoires n'est peut-être pas activé dans IIS. Suivez les conseils fournis dans la section « Choses à essayer » pour l’activer. Ou bien, vous pouvez taper directement » lien hypertexte « http://localhost/WebApplicationFolderName » http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc » pour afficher la page de votre service.  
  
 Vous pouvez utiliser **publier** pour spécifier si vous souhaitez copier l’assembly, la configuration et le fichier .svc pour tous les services définis dans le projet à l’emplacement cible et remplace les fichiers existants dans la destination.  
  
 Si vous choisissez de déployer votre application sur le serveur IIS local, vous pouvez rencontrer des erreurs liées à l'installation d'IIS. Vérifiez que IIS est installé correctement. Vous pouvez taper « Lien hypertexte « http://localhost » http://localhost » dans votre navigateur et vérifier si la page par défaut IIS ne s’affichent.  Dans certains cas, les problèmes peuvent aussi être causés par l'inscription incorrecte d'ASP.NET ou de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] dans IIS. Vous pouvez ouvrir l’invite de commandes Visual Studio et exécutez la commande « aspnet_regiis.exe - ir » pour résoudre les problèmes d’inscription ASP.NET ou exécuter la commande « ServiceModelReg.exe – ia » pour corriger les problèmes de l’inscription WCF.  
  
## <a name="files-generated-for-publishing"></a>Fichiers générés en vue de leur publication  
 Avant qu'une bibliothèque de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] puisse être hébergée sur le Web, les fichiers suivants sont générés par l'outil : fichiers d'assembly, fichier Web.config et fichier .svc. Tous les fichiers sont copiés à l'emplacement cible. Le service est ensuite publié.  
  
### <a name="assembly-files"></a>Fichiers d'assembly  
 Lorsque vous publiez un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] à l'aide de cet outil, il est construit automatiquement dans un premier temps, puis les fichiers d'assembly sont générés dans le projet de service.  
  
### <a name="svc-file"></a>Fichier .SVC  
 L'opération de publication génère un fichier *.svc pour chaque service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], que le fichier existe ou non, pour vérifier la validité de la version. Il existe deux types de fichiers svc différents : un pour la bibliothèque du service de syndication et la bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et un autre pour la bibliothèque du service de workflow séquentiel et de l'ordinateur d'état. Le texte généré \*fichier .svc est copié dans le dossier racine dans l’emplacement cible.  
  
### <a name="webconfig-file"></a>Fichier Web.config  
 Chaque fois qu'un projet de service est publié à un emplacement cible spécifique, un fichier Web.config est créé.  
  
 Le fichier Web.config généré contient des sections Web qui sont utiles pour l'hébergement Web et le contenu d'App.config pour la bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] avec les modifications suivantes :  
  
-   L'adresse de base est exclue.  
  
-   Les paramètres dans l'élément `<diagnostics>` sont exclus pour préserver les paramètres de suivi de la plateforme cible.  
  
## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>Publication sur IIS de services WCF avec des liaisons non-HTTP  
 Si vous utilisez IIS 7.0 ou version ultérieure, vous pouvez publier sur IIS des services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] avec des liaisons non-HTTP. Vous devez effectuer plusieurs tâches de préconfiguration. Pour plus d’informations, consultez les rubriques à [hébergement dans le Service d’Activation des processus Windows](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
## <a name="security"></a>Sécurité  
 La publication sur le serveur IIS local requiert des privilèges d'administrateur car IIS doit être exécuté sous un compte Administrateur. Si un utilisateur sans privilège d'administrateur ouvre la Publication de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], IIS n'est pas disponible parmi les emplacements cibles. La publication sur le système de fichiers ou le FTP Site fonctionne sans privilège d’administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles Visual Studio WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Client test WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
