---
title: "H&#244;te de service WCF (WcfSvcHost.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
caps.latest.revision: 27
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 27
---
# H&#244;te de service WCF (WcfSvcHost.exe)
L'Hôte de service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] \(WcfSvcHost.exe\) vous permet de lancer le débogueur [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] \(F5\) pour héberger et tester automatiquement un service que vous avez implémenté.Vous pouvez ensuite tester le service à l'aide du client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \(WcfTestClient.exe\) ou de votre propre client, afin de rechercher et de résoudre les erreurs potentielles.  
  
## Hôte de service WCF  
 L'hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] énumère les services contenus dans un projet de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], charge la configuration du projet et effectue l'instanciation d'un hôte pour chaque service trouvé.Cet outil est intégré à [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] via le modèle Service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et est appelé lorsque vous commencez le débogage de votre projet.  
  
 Grâce à l'utilisation de l'hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], vous pouvez héberger un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \(dans un projet de bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]\) sans écrire de code supplémentaire ou se limiter à un hôte spécifique pendant le développement.  
  
> [!NOTE]
>  L'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ne prend pas en charge la confiance partielle.Si vous souhaitez utiliser un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] en confiance partielle, n'utilisez pas le modèle de projet de la bibliothèque de services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] pour générer votre service.À la place, créez un nouveau site Web dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] en choisissant le modèle de site Web de service de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] qui peut héberger le service dans un serveur Web sur lequel la confiance partielle [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est prise en charge.  
  
## Types de projet hébergés par l'hôte de service WCF  
 L'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] peut héberger les types de projets Bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] suivants : Bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], Bibliothèque du service de workflow séquentiel, Bibliothèque du service de workflow de l'ordinateur d'état et Bibliothèque du service de syndication.L'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] peut également héberger les services qui peuvent être ajoutés à un projet Bibliothèque du service à l'aide de la fonction **Ajouter un élément**.Parmi ces services, on compte le service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], le service de l'ordinateur d'état WF, le service séquentiel WF, le service de l'ordinateur d'état WF XAML et le service séquentiel WF XAML.  
  
 Toutefois, il est à noter que l'outil ne vous aidera pas à configurer un hôte.Pour cette tâche, vous devez modifier le fichier App.config manuellement.L'outil ne permet pas non plus de valider les fichiers de configuration définis par l'utilisateur.  
  
> [!CAUTION]
>  Vous ne devez pas utiliser l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pour héberger des services au sein d'un environnement de production, car il n'a pas été conçu dans ce but.L'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ne prend pas en charge la fiabilité, la sécurité et les exigences de facilité de gestion propres à ce type d'environnement.Utilisez plutôt IIS car cette solution présente une fiabilité et des fonctionnalités de surveillance plus élevées ; elle constitue en outre la solution recommandée pour les services d'hébergement.Une fois que vous avez terminé le développement de vos services, vous devez effectuer une migration de ceux\-ci depuis l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] vers IIS.  
  
## Scénarios d'utilisation de l'hôte de service WCF dans Visual Studio  
 Le tableau suivant répertorie tous les paramètres de la boîte de dialogue **Arguments de la ligne de commande** qui s'ouvre lorsque vous cliquez avec le bouton droit sur votre projet dans l'**Explorateur de solutions** dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] en sélectionnant **Propriétés**, puis en cliquant sur l'onglet **Débogage** et sur **Démarrer le projet**.Ces paramètres sont utiles pour configurer l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
|Paramètre|Signification|  
|---------------|-------------------|  
|`/client`|Paramètre facultatif qui spécifie le chemin d'accès à un fichier exécutable à utiliser une fois les services hébergés.Il permet de lancer le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] une fois l'hébergement effectué.|  
|`/clientArg`|Spécifie une chaîne en tant qu'argument passé à l'application cliente personnalisée.|  
|`/?`|Affiche le texte de l'aide.|  
  
#### Utilisation du client test WCF  
 Après avoir créé un projet de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et appuyé sur la touche F5 pour démarrer le débogueur, l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] commence à héberger tous les services trouvés dans votre projet.Ensuite, le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ouvre et affiche automatiquement une liste de points de terminaison de service définis dans le fichier de configuration.Dans la fenêtre principale, vous pouvez tester les paramètres et appeler votre service.  
  
 Pour vérifier que le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est en cours d'utilisation, cliquez avec le bouton droit sur votre projet dans l'**Explorateur de solutions** \(dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]\), puis sélectionnez**Propriétés** et cliquez sur l'onglet **Débogage**.Cliquez sur **Démarrer le projet** et assurez\-vous que les éléments suivants apparaissent dans la boîte de dialogue **Arguments de la ligne de commande**.  
  
 `/client:WcfTestClient.exe`  
  
#### Utilisation d'un client personnalisé  
 Pour utiliser un client personnalisé, cliquez avec le bouton droit sur votre projet dans l'**Explorateur de solutions** \(dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]\), puis sélectionnez **Propriétés** et cliquez sur l'onglet **Débogage**.Cliquez sur **Démarrer le projet** et modifiez le paramètre `/client` dans la boîte de dialogue **Arguments de la ligne de commande** afin de désigner votre client personnalisé, comme indiqué dans l'exemple suivant.  
  
 `/client:"path/CustomClient.exe"`  
  
 Lorsque vous appuyez sur la touche F5 pour redémarrer le service, l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] démarre automatiquement votre client personnalisé quand vous lancez le débogueur.  
  
 Vous pouvez également utiliser le paramètre `/clientArg:` pour spécifier une chaîne en tant qu'argument qui est passé à l'application cliente personnalisée, comme indiqué dans l'exemple suivant.  
  
 `/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`  
  
 Par exemple, si vous utilisez le modèle de bibliothèque du service de syndication, vous pouvez utiliser les arguments de la ligne de commandes suivante :  
  
 `/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`  
  
#### Spécification d'aucun client  
 Pour spécifier qu'aucun client ne sera utilisé après l'hébergement du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], cliquez avec le bouton droit sur votre projet dans l'**Explorateur de solutions** \(dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]\), puis sélectionnez **Propriétés** et cliquez sur l'onglet **Débogage**.Cliquez sur **Démarrer le projet** et ne renseignez aucun champ de la boîte de dialogue **Arguments de la ligne de commande**.  
  
#### Utilisation d'un hôte personnalisé  
 Pour utiliser un hôte personnalisé, cliquez avec le bouton droit sur votre projet dans l'**Explorateur de solutions** \(dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]\), puis sélectionnez **Propriétés** et cliquez sur l'onglet **Débogage**.Cliquez sur **Démarrer le programme externe** et entrez le chemin d'accès complet à l'hôte personnalisé.Vous pouvez également utiliser la boîte de dialogue **Arguments de la ligne de commande** pour spécifier les arguments à passer à l'hôte.  
  
## Interface utilisateur de l'Hôte de service WCF  
 Lors de l'appel initial de l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \(en appuyant sur la touche F5 dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]\), la fenêtre **Hôte de service WCF** s'ouvre automatiquement.Lorsque l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est en cours d'exécution, l'icône du programme apparaît dans la zone de notification.Double\-cliquez sur l'icône pour ouvrir la fenêtre **Hôte de service WCF**  
  
 Lorsque des erreurs surviennent pendant l'hébergement de service, la boîte de dialogue de l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] s'ouvre et affiche les informations correspondantes.  
  
 La fenêtre principale **Hôte de service WCF** contient deux menus :  
  
-   Le menu **Fichier** : contient les commandes **Fermer** et **Quitter**.Lorsque vous cliquez sur **Fermer**, la boîte de dialogue **Hôte de service WCF** se referme, mais les services continuent à être hébergés.Lorsque vous cliquez sur **Quitter**, l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est également arrêté.Cela arrête également tous les services hébergés.  
  
-   Le menu **Aide** : contient la commande **À propos de** qui affiche des informations sur la version.Il contient également la commande **Aide** qui permet d'ouvrir un fichier d'aide.  
  
 La fenêtre principale **Hôte de service WCF** contient deux zones :  
  
-   La première zone est **Service**.Elle contient une liste qui affiche des informations de base sur tous les services.Ces informations incluent :  
  
    -   **Service** : répertorie tous les services.  
  
    -   **État** : répertorie l'état du service.Les valeurs valides sont "Démarré", "Arrêté" et "Erreur".  
  
    -   **Adresse de métadonnées** : affiche l'adresse des métadonnées des services.  
  
-   La deuxième zone est **Informations supplémentaires**.Elle affiche une explication détaillée de l'état d'un service lorsque la ligne de service spécifique est sélectionnée dans la zone **Service**.Si l'état est Erreur, vous pouvez consulter le message d'erreur complet qui s'affiche à l'écran.  
  
## Arrêt de l'Hôte de service WCF  
 Vous pouvez arrêter l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] en utilisant l'une des quatre méthodes suivantes :  
  
-   Arrêtez la session de débogage dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
-   Sélectionnez **Quitter** dans le menu **Fichier**, dans la fenêtre **Hôte de service WCF**.  
  
-   Sélectionnez **Quitter** dans le menu contextuel de l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], dans la zone de notification du système.  
  
-   Quittez le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] s'il est en cours d'utilisation.  
  
## Utilisation de l'hôte de service sans privilège d'administrateur  
 Pour permettre aux utilisateurs qui ne disposent pas de privilèges d'administrateur de développer des services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], une liste de contrôle d'accès \(ACL, Access Control List\) est créée pour l'espace de noms http:\/\/\+:8731\/Design\_Time\_Addresses pendant l'installation de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].La liste ACL a la valeur \(UI\), qui inclut tous les utilisateurs interactifs ayant ouvert une session sur l'ordinateur.Les administrateurs peuvent ajouter ou supprimer des utilisateurs de cette liste ou ouvrir des ports supplémentaires. Cette liste ACL permet aux utilisateurs d'exécuter l'hôte de service auto [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \(wcfSvcHost.exe\) sans devoir obtenir au préalable des privilèges d'administrateur.  
  
 Vous pouvez modifier l'accès grâce à l'outil netsh.exe dans [!INCLUDE[wv](../../../includes/wv-md.md)], via le compte d'administrateur avec élévation de privilèges.Ceci est un exemple d'utilisation de netsh.exe .  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Pour plus d'informations sur netsh.exe, consultez [Utilisation de l'outil Netsh.exe et des commutateurs de ligne de commandes](http://go.microsoft.com/fwlink/?LinkId=97877) \(page pouvant être en anglais\).  
  
## Voir aussi  
 [Client test WCF \(WcfTestClient.exe\)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)