---
title: "Publication du service&#160;WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
caps.latest.revision: 22
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# Publication du service&#160;WCF
La Publication de service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] vous aide à progresser de l'environnement des premières phases de développement fourni par l'hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] au déploiement proprement dit de l'application dans un environnement de production aux fins de test.  Avant de vous engager dans un plan de déploiement final, vous pouvez utiliser la Publication de service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] pour vérifier que votre service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] s'exécute correctement et est prêt à être publié.  Vous pouvez également choisir de déployer vos bibliothèques de services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] à différents emplacements cibles en vue de les tester.  
  
## Services pris en charge et emplacements cibles  
 La Publication de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] prend en charge la publication des services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] créés à partir du jeu de modèles de la bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et leurs modèles d'élément correspondants, dont :  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Modèle de bibliothèque du service avec le modèle d'élément.  
  
-   Modèle de bibliothèque du service de workflow séquentiel avec le modèle d'élément.  
  
-   Modèle de bibliothèque du service de workflow de l'ordinateur d'état avec le modèle d'élément.  
  
-   Bibliothèque du service de syndication.  
  
 Vous trouverez ces modèles de service en choisissant **Fichier** \-\> **Nouveau projet** \-\> **Visual Basic** ou **Visual C\#** \-\> **WCF**.  
  
 Le service peut être publié aux emplacements cibles suivants.  
  
-   IIS local  
  
-   Système de fichiers  
  
-   Site FTP  
  
-   Site distant  
  
## Utilisation de la publication de service WCF  
 Pour déployer une implémentation de service, procédez comme suit :  
  
1.  Ouvrez Visual Studio avec des privilèges élevés \(cliquez avec le bouton droit sur l'exécutable, puis cliquez sur Exécuter en tant qu'administrateur\).  Si vous utilisez IIS 7.0 ou version ultérieure, assurez\-vous que le composant Compatibilité avec la métabase IIS et la configuration IIS 6 est installé à l'aide de Activer ou désactiver des fonctionnalités Windows dans le Panneau de configuration.  
  
2.  Ouvrez un projet de service, sélectionnez **Génération**\-\>**Publier \<Nom du projet\>** dans le menu principal ou cliquez avec le bouton droit sur le projet dans l'**Explorateur de solutions** et cliquez sur **Publier**.  
  
3.  La fenêtre **Publier** apparaît.  Cliquez sur le bouton **…** pour spécifier l'emplacement cible où doit être déployé le service.  Vous pouvez choisir de déployer l'application sur le serveur IIS local, le système de fichiers, un site FTP ou un site distant.  Si vous déployez l'application sur le serveur IIS local, vous pouvez sélectionner votre site Web et votre application Web au\-dessous, en cliquant sur l'icône **Créer une application Web** dans l'angle supérieur droit.  
  
4.  Après que vous avez cliqué sur **Publier** dans la fenêtre principale, Visual Studio déploie l'application sur IIS à l'emplacement cible indiqué et copie les fichiers Web.config, .svc et d'assembly dans le répertoire cible.  .  Le nom du fichier .svc est « “ProjectName.ServiceName.svc ».  Une fois le service publié, un lien est disponible dans la fenêtre Sortie Visual Studio, semblable à « Connexion à http:\/\/localhost\/WebApplicationFolderName en cours... ».  Vous pouvez appuyer sur Ctrl et cliquer sur le lien pour ouvrir une page du navigateur dans Visual Studio afin d'afficher la structure des répertoires du service.  
  
     S'il est impossible de visiter le site, l'explorateur de répertoires n'est peut\-être pas activé dans IIS.  Suivez les conseils fournis dans la section Solutions possibles pour l'activer.  Vous pouvez aussi taper directement « http:\/\/localhost\/WebApplicationFolderName\/ProjectName.ServiceName.svc » pour afficher votre page de service.  
  
 Vous pouvez indiquer dans la fenêtre **Publier** si vous souhaitez copier à l'emplacement cible les fichiers d'assembly, de configuration et .svc de tous les services définis dans le projet, et remplacer les fichiers existants dans ce dossier.  
  
 Si vous choisissez de déployer votre application sur le serveur IIS local, vous pouvez rencontrer des erreurs liées à l'installation d'IIS.  Vérifiez que IIS est installé correctement.  Vous pouvez taper « http:\/\/localhost » dans votre navigateur et vérifier si la page par défaut d'IIS s'affiche.  Dans certains cas, les problèmes peuvent aussi être causés par l'inscription incorrecte d'ASP.NET ou de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] dans IIS.  Ouvrez une invite de commandes de Visual Studio et exécutez la commande « aspnet\_regiis.exe \-ir » pour corriger les problèmes d'inscription fix ASP.NET, ou exécutez la commande « ServiceModelReg.exe –ia » pour corriger les problèmes d'inscription WCF.  
  
## Fichiers générés en vue de leur publication  
 Avant qu'une bibliothèque de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] puisse être hébergée sur le Web, les fichiers suivants sont générés par l'outil : fichiers d'assembly, fichier Web.config et fichier .svc.  Tous les fichiers sont copiés à l'emplacement cible.  Le service est ensuite publié.  
  
### Fichiers d'assembly  
 Lorsque vous publiez un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] à l'aide de cet outil, il est construit automatiquement dans un premier temps, puis les fichiers d'assembly sont générés dans le projet de service.  
  
### Fichier .SVC  
 L'opération de publication génère un fichier \*.svc pour chaque service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], que le fichier existe ou non, pour vérifier la validité de la version.  Il existe deux types de fichiers svc différents : un pour la bibliothèque du service de syndication et la bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et un autre pour la bibliothèque du service de workflow séquentiel et de l'ordinateur d'état.  Le fichier \*.svc généré est copié dans le dossier racine de l'emplacement cible.  
  
### Fichier Web.config  
 Chaque fois qu'un projet de service est publié à un emplacement cible spécifique, un fichier Web.config est créé.  
  
 Le fichier Web.config généré contient des sections Web qui sont utiles pour l'hébergement Web et le contenu d'App.config pour la bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] avec les modifications suivantes :  
  
-   L'adresse de base est exclue.  
  
-   Les paramètres dans l'élément `<diagnostics>` sont exclus pour préserver les paramètres de suivi de la plateforme cible.  
  
## Publication sur IIS de services WCF avec des liaisons non\-HTTP  
 Si vous utilisez IIS 7.0 ou version ultérieure, vous pouvez publier sur IIS des services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] avec des liaisons non\-HTTP.  Vous devez effectuer plusieurs tâches de préconfiguration.  Pour plus d'informations, consultez les rubriques de [Hébergement dans le service d'activation de processus de Windows \(WAS, Windows Process Activation Service\)](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
## Sécurité  
 La publication sur le serveur IIS local requiert des privilèges d'administrateur car IIS doit être exécuté sous un compte Administrateur.  Si un utilisateur sans privilège d'administrateur ouvre la Publication de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], IIS n'est pas disponible parmi les emplacements cibles.  En revanche, il n'est pas nécessaire d'avoir des privilèges d'administrateur pour la publication sur le système de fichiers, un site FTP ou un site distant.  
  
## Voir aussi  
 [Modèles Visual Studio WCF](../../../docs/framework/wcf/wcf-vs-templates.md)   
 [Hôte de service WCF \(WcfSvcHost.exe\)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)   
 [Client test WCF \(WcfTestClient.exe\)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)