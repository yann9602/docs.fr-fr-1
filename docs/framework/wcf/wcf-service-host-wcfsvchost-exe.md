---
title: "Hôte de service WCF (WcfSvcHost.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 495088463a6a7463ce1452588dc55d35110f0092
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-service-host-wcfsvchostexe"></a>Hôte de service WCF (WcfSvcHost.exe)
L'Hôte de service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] (WcfSvcHost.exe) vous permet de lancer le débogueur [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] (F5) pour héberger et tester automatiquement un service que vous avez implémenté. Vous pouvez ensuite tester le service à l'aide du client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (WcfTestClient.exe) ou de votre propre client, afin de rechercher et de résoudre les erreurs potentielles.  
  
## <a name="wcf-service-host"></a>Hôte de service WCF  
 L'hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] énumère les services contenus dans un projet de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], charge la configuration du projet et effectue l'instanciation d'un hôte pour chaque service trouvé. Cet outil est intégré à [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] via le modèle Service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et est appelé lorsque vous commencez le débogage de votre projet.  
  
 Grâce à l'utilisation de l'hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], vous pouvez héberger un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (dans un projet de bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]) sans écrire de code supplémentaire ou se limiter à un hôte spécifique pendant le développement.  
  
> [!NOTE]
>  L'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ne prend pas en charge la confiance partielle. Si vous souhaitez utiliser un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] en confiance partielle, n'utilisez pas le modèle de projet de la bibliothèque de services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] pour générer votre service. À la place, créez un nouveau site Web dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] en choisissant le modèle de site Web de service de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] qui peut héberger le service dans un serveur Web sur lequel la confiance partielle [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est prise en charge.  
  
## <a name="project-types-hosted-by-wcf-service-host"></a>Types de projet hébergés par l'hôte de service WCF  
 L'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] peut héberger les types de projets Bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] suivants : Bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], Bibliothèque du service de workflow séquentiel, Bibliothèque du service de workflow de l'ordinateur d'état et Bibliothèque du service de syndication. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Hôte de service peut également héberger les services qui peuvent être ajoutés à un projet de bibliothèque de service à l’aide du **ajouter un élément** fonctionnalité. Parmi ces services, on compte le service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], le service de l'ordinateur d'état WF, le service séquentiel WF, le service de l'ordinateur d'état WF XAML et le service séquentiel WF XAML.  
  
 Toutefois, il est à noter que l'outil ne vous aidera pas à configurer un hôte. Pour cette tâche, vous devez modifier le fichier App.config manuellement. L'outil ne permet pas non plus de valider les fichiers de configuration définis par l'utilisateur.  
  
> [!CAUTION]
>  Vous ne devez pas utiliser l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pour héberger des services au sein d'un environnement de production, car il n'a pas été conçu dans ce but.  L'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ne prend pas en charge la fiabilité, la sécurité et les exigences de facilité de gestion propres à ce type d'environnement. Utilisez plutôt IIS car cette solution présente une fiabilité et des fonctionnalités de surveillance plus élevées ; elle constitue en outre la solution recommandée pour les services d'hébergement. Une fois que vous avez terminé le développement de vos services, vous devez effectuer une migration de ceux-ci depuis l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] vers IIS.  
  
## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>Scénarios d'utilisation de l'hôte de service WCF dans Visual Studio  
 Le tableau suivant répertorie tous les paramètres dans le **arguments de ligne de commande** boîte de dialogue, qui se trouve en double-cliquant sur votre projet dans **l’Explorateur de Solutions** dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], en sélectionnant  **Propriétés**, puis en sélectionnant le **déboguer** onglet et en cliquant sur **démarrer le projet**. Ces paramètres sont utiles pour configurer l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
|Paramètre|Signification|  
|---------------|-------------|  
|`/client`|Paramètre facultatif qui spécifie le chemin d’accès à un fichier exécutable à utiliser une fois les services hébergés. Il permet de lancer le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] une fois l'hébergement effectué.|  
|`/clientArg`|Spécifie une chaîne en tant qu’argument passé à l’application cliente personnalisée.|  
|`/?`|Affiche le texte de l'aide.|  
  
#### <a name="using-wcf-test-client"></a>Utilisation du client test WCF  
 Après avoir créé un projet de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et appuyé sur la touche F5 pour démarrer le débogueur, l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] commence à héberger tous les services trouvés dans votre projet. Ensuite, le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ouvre et affiche automatiquement une liste de points de terminaison de service définis dans le fichier de configuration. Dans la fenêtre principale, vous pouvez tester les paramètres et appeler votre service.  
  
 Pour vous assurer que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Client de Test est utilisé, avec le bouton droit de votre projet dans **l’Explorateur de Solutions** dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], sélectionnez **propriétés**, puis sélectionnez le **déboguer**onglet. Cliquez sur **démarrer le projet** et assurez-vous que les éléments suivants apparaissent dans le **arguments de ligne de commande** boîte de dialogue.  
  
 `/client:WcfTestClient.exe`  
  
#### <a name="using-a-custom-client"></a>Utilisation d'un client personnalisé  
 Pour utiliser un client personnalisé, cliquez sur votre projet dans **l’Explorateur de Solutions** dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], sélectionnez **propriétés**, puis sélectionnez le **déboguer** onglet. Cliquez sur **démarrer le projet** et de modifier le `/client` paramètre dans le **arguments de ligne de commande** boîte de dialogue pour pointer vers votre client personnalisé, comme indiqué dans l’exemple suivant.  
  
 `/client:"path/CustomClient.exe"`  
  
 Lorsque vous appuyez sur la touche F5 pour redémarrer le service, l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] démarre automatiquement votre client personnalisé quand vous lancez le débogueur.  
  
 Vous pouvez également utiliser le paramètre `/clientArg:` pour spécifier une chaîne en tant qu'argument qui est passé à l'application cliente personnalisée, comme indiqué dans l'exemple suivant.  
  
 `/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`  
  
 Par exemple, si vous utilisez le modèle de bibliothèque du service de syndication, vous pouvez utiliser les arguments de la ligne de commandes suivante :  
  
 `/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`  
  
#### <a name="specifying-no-client"></a>Spécification d'aucun client  
 Pour spécifier qu’aucun client ne sera utilisé après [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] d’hébergement du service, avec le bouton droit de votre projet dans **l’Explorateur de Solutions** dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], sélectionnez **propriétés**, puis sélectionnez le **Déboguer** onglet. Cliquez sur **démarrer le projet** et laisser le **arguments de ligne de commande** boîte de dialogue.  
  
#### <a name="using-a-custom-host"></a>Utilisation d'un hôte personnalisé  
 Pour utiliser un hôte personnalisé, cliquez sur votre projet dans **l’Explorateur de Solutions** dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], sélectionnez **propriétés**, puis sélectionnez le **déboguer** onglet. Cliquez sur **démarrer le programme externe** et entrez le chemin d’accès complet à l’hôte personnalisé. Vous pouvez également utiliser le **arguments de ligne de commande** boîte de dialogue pour spécifier des arguments à passer à l’ordinateur hôte.  
  
## <a name="wcf-service-host-user-interface"></a>Interface utilisateur de l'Hôte de service WCF  
 Quand vous appelez initialement [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hôte de Service (en appuyant sur F5 dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]), la **hôte de Service WCF** fenêtre s’ouvre automatiquement. Lorsque l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est en cours d'exécution, l'icône du programme apparaît dans la zone de notification. Double-cliquez sur l’icône pour ouvrir la **hôte de Service WCF** fenêtre  
  
 Lorsque des erreurs surviennent pendant l'hébergement de service, la boîte de dialogue de l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] s'ouvre et affiche les informations correspondantes.  
  
 Le **hôte de Service WCF** fenêtre principale contient deux menus :  
  
-   **Fichier**: contient le **fermer** et **Exit** commandes. Lorsque vous cliquez sur **fermer**, le **hôte de Service WCF** boîte de dialogue se ferme, mais les services continuent d’être hébergés. Lorsque vous cliquez sur **Exit**, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hôte de Service est également arrêté. Cela arrête également tous les services hébergés.  
  
-   **Aide**: contient le **sur** commande qui contient les informations de version. Il contient également le **aide** commande capable d’ouvrir un fichier d’aide.  
  
 Le principal **hôte de Service WCF** fenêtre contient deux zones :  
  
-   La première zone est **Service**. Elle contient une liste qui affiche des informations de base sur tous les services. Ces informations incluent :  
  
    -   **Service**: répertorie tous les services.  
  
    -   **État**: répertorie l’état du service. Les valeurs valides sont « Démarré », « Stopped » et « Erreur ».  
  
    -   **Adresse des métadonnées**: affiche l’adresse des métadonnées des services.  
  
-   La deuxième zone est **des informations supplémentaires**. Il affiche une explication détaillée de l’état du service lorsque la ligne de service spécifique est sélectionnée dans le **Service** zone. Si l'état est Erreur, vous pouvez consulter le message d'erreur complet qui s'affiche à l'écran.  
  
## <a name="stopping-wcf-service-host"></a>Arrêt de l'Hôte de service WCF  
 Vous pouvez arrêter l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] en utilisant l'une des quatre méthodes suivantes :  
  
-   Arrêtez la session de débogage dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
-   Sélectionnez **Exit** à partir de la **fichier** menu dans le **hôte de Service WCF** fenêtre.  
  
-   Sélectionnez **Exit** à partir du menu contextuel de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] icône hôte de Service dans la zone de notification système.  
  
-   Quittez le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] s'il est en cours d'utilisation.  
  
## <a name="using-service-host-without-administrator-privilege"></a>Utilisation de l'hôte de service sans privilège d'administrateur  
 Pour permettre aux utilisateurs qui ne disposent pas de privilèges d'administrateur de développer des services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], une liste de contrôle d'accès (ACL, Access Control List) est créée pour l'espace de noms http://+:8731/Design_Time_Addresses pendant l'installation de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. La liste ACL a la valeur (UI), qui inclut tous les utilisateurs interactifs ayant ouvert une session sur l'ordinateur. Les administrateurs peuvent ajouter ou supprimer des utilisateurs de cette liste ou ouvrir des ports supplémentaires. Cette liste ACL permet aux utilisateurs d'exécuter l'hôte de service auto [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (wcfSvcHost.exe) sans devoir obtenir au préalable des privilèges d'administrateur.  
  
 Vous pouvez modifier l'accès grâce à l'outil netsh.exe dans [!INCLUDE[wv](../../../includes/wv-md.md)], via le compte d'administrateur avec élévation de privilèges. Ceci est un exemple d'utilisation de netsh.exe .  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Pour plus d’informations sur netsh.exe, consultez «[comment utiliser l’outil Netsh.exe et les commutateurs de ligne de commande](http://go.microsoft.com/fwlink/?LinkId=97877)».  
  
## <a name="see-also"></a>Voir aussi  
 [Client test WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
