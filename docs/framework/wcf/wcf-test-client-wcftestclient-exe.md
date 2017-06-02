---
title: "Client test WCF (WcfTestClient.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
caps.latest.revision: 45
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 45
---
# Client test WCF (WcfTestClient.exe)
Le client test [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] \(WcfTestClient.exe\) est un outil GUI qui permet aux utilisateurs d'entrer des paramètres de test, d'envoyer ces entrées au service et d'afficher la réponse renvoyée par ce dernier.  Il offre des conditions de test de service transparentes lorsqu'il est associé à l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
 Vous pouvez trouver le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \(WcfTestClient.exe\) à l'emplacement suivant : C:\\Program Files\\Microsoft Visual Studio 9.0\\Common7\\IDE\\  
  
## Scénarios d'utilisation du client test  
 Les sections suivantes décrivent les scénarios les plus classiques dans lesquels vous pouvez utiliser le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pour rendre votre processus de développement transparent.  
  
### Dans Visual Studio  
  
#### L'Hôte de service WCF démarre le client test WCF avec un service unique.  
 Après avoir créé un projet de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et appuyé sur la touche F5 pour démarrer le débogueur, l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] commence à héberger le service dans votre projet.  Ensuite, le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ouvre et affiche une liste de points de terminaison de service définis dans le fichier de configuration.  Vous pouvez tester les paramètres et appeler le service, et répéter ce processus pour tester et valider régulièrement votre service.  
  
#### L'Hôte de service WCF démarre le client test WCF avec plusieurs services  
 Vous pouvez également utiliser le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pour vous aider à déboguer un projet de service contenant plusieurs services.  Lorsque le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] s'ouvre, il itère automatiquement au sein de la liste des services contenus dans votre projet et les ouvre à des fins de test.  
  
### En dehors de Visual Studio  
 Vous pouvez également appeler le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \(WcfTestClient.exe\) à l'extérieur de Visual Studio pour tester un service arbitraire sur Internet.  Pour localiser l'outil, allez à l'emplacement suivant :  
  
 C:\\Program Files\\Microsoft Visual Studio 9.0\\Common7\\IDE\\  
  
 Pour utiliser l'outil, double\-cliquez sur le nom de fichier afin de l'ouvrir à partir de cet emplacement ou lancez\-le à partir d'une ligne de commandes.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Le client test prend un nombre arbitraire d'URI comme arguments de ligne de commandes.  Il s'agit des URI des services qui peuvent être testés.  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 Une fois la fenêtre du client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ouverte, cliquez sur **Fichier**\-\>**Ajouter un service** et tapez l'adresse du point de terminaison du service à ouvrir.  
  
## Interface utilisateur du client test WCF  
 Vous pouvez utiliser le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] avec un service unique ou avec plusieurs services.  
  
### Opérations de service  
 Le volet gauche de la fenêtre principale du client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] répertorie tous les services disponibles, ainsi que leurs opérations et points de terminaison respectifs.  
  
 Lorsque vous double\-cliquez sur une opération, vous pouvez afficher son contenu dans le volet droit d'un nouvel onglet portant le nom de l'opération.  
  
 Le volet gauche répertorie également les fichiers de configuration du client.  Double\-cliquez sur l'un des éléments pour afficher le contenu du fichier correspondant dans une nouvelle page à onglets, dans le volet droit.  
  
### Saisie de paramètres de test  
 Pour afficher les paramètres de test, double\-cliquez sur une opération afin de l'ouvrir dans le volet droit.  Les paramètres sont affichés dans la vue **Mis en forme** par défaut et vous pouvez entrer des valeurs arbitraires pour les paramètres afin de tester le service.  
  
 Pour afficher le fichier XML du message, cliquez sur **XML**.  Pour les envoyer au service, cliquez sur **Appeler**.  
  
 Pour un paramètre DataSet, cliquez sur le bouton **…** en regard de **Modifier** pour le modifier dans une nouvelle fenêtre affichant le DataGrid.  Notez l'aspect des boutons **Copier le DataSet** et **Coller le DataSet**.  Si le schéma de l'objet DataSet est inconnu lors de la première modification, DataGrid est vide.  Vous devez coller un objet DataSet avec le même schéma dans l'objet actuel de DataGrid.  \(Notez que vous devez copier le schéma à partir d'un autre endroit avant l'opération de collage.\) Vous pouvez également copier un objet Dataset en vue d'une utilisation ultérieure en cliquant sur le bouton **Copier le DataSet**.  
  
 La réponse du service apparaît au\-dessous des paramètres de test.  
  
> [!NOTE]
>  Si la valeur de retour attendue est une chaîne, le résultat est affiché sous la forme d'une chaîne entre guillemet même si l'entrée fournie n'est pas incluse entre guillemet.  
  
 Si vous avez spécifié une opération particulière comme étant unidirectionnelle lorsque vous avez créé le contrat pour le service, aucune réponse de service n'est affichée.  Dès que le message est placé en file d'attente en vue de sa transmission, une boîte de dialogue apparaît pour vous notifier que le message a été envoyé avec succès.  
  
### Prise en charge des sessions  
 La case à cocher **Démarrer un nouveau proxy** sous l'onglet d'une opération de service vous permet d'activer ou de désactiver la prise en charge des sessions.  Elle est désactivée par défaut.  
  
 Lorsque vous entrez les paramètres de test d'une opération spécifique \(ou d'une autre opération dans le même point de terminaison de service\) et cliquez plusieurs fois sur **Appeler** alors que la case à cocher est désélectionnée, ces opérations partagent un proxy et l'état du service est rendu persistant entre plusieurs opérations.  
  
 Si la case à cocher **Démarrer un nouveau proxy** est activée, un nouveau proxy est démarré chaque fois que vous cliquez sur **Appeler**. Le scénario de la session précédente est arrêté et l'état du service est réinitialisé.  
  
### Modification de la configuration client  
 Le volet gauche de la fenêtre principale du client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] répertorie les fichiers configuration du client.  Double\-cliquez sur l'un des éléments pour afficher le contenu du fichier dans le volet droit.  
  
#### Modifier avec l'Éditeur de configuration de service  
 Cliquez avec le bouton droit sur **Fichier de configuration** dans le volet gauche et sélectionnez le menu contextuel **Modifier avec SvcConfigEditor**.  L'Éditeur de configuration de service est lancé avec le contenu de la configuration client.  Vous pouvez modifier la configuration et l'enregistrer dans l'outil.  
  
 Après avoir enregistré le fichier dans l'Éditeur de configuration de service, le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] affiche un message d'avertissement pour vous informer que le fichier a été modifié en dehors de l'application et vous demande si vous voulez le recharger.  
  
 Si vous sélectionnez **Oui**, le contenu de la configuration dans l'onglet Client.dll.config reflète les modifications que vous avez effectuées dans l'éditeur.  
  
 Si vous sélectionnez **Non**, le contenu de la configuration dans l'onglet Client.dll.config reste inchangé et le contenu modifié est enregistré automatiquement dans le fichier source.  
  
#### Restaurer la configuration par défaut  
 Si vous souhaitez annuler toutes les modifications et restaurer la configuration client par défaut, cliquez avec le bouton droit sur **Fichier de configuration** dans le volet gauche et sélectionnez le menu contextuel **Restaurer la configuration par défaut**.  La valeur de configuration par défaut est chargée et le contenu sous l'onglet Client.dll.config est restauré.  
  
#### Valider des modifications  
 Lorsque les modifications enregistrées sont chargées dans le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], la validité de la configuration par rapport au schéma [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est vérifiée.  Si les erreurs sont rencontrées, une boîte de dialogue est affichée pour afficher des détails d'erreur.  
  
 Pendant la génération d'un proxy, une compilation binaire ou l'appel du service, les éléments de menu qui prennent en charge l'édition \(autrement dit, les fonctions de modification, de restauration, etc.\) sont désactivés.  L'appel de service est également désactivé lors du chargement de la configuration mise à jour sur le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
#### Rendre la configuration client persistante  
 L'onglet **Outils**\-\>**Options**\-\>**Configuration client** contient une option **Toujours régénérer la configuration au démarrage des services**, qui est activée par défaut.  Cette option indique que chaque fois que le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] charge un service, un fichier de configuration est régénéré selon les fichiers App.config et de contrat de service les plus récents du service.  
  
 Si vous avez modifié la configuration client de votre service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et vous souhaitez toujours utiliser ce fichier mis à jour pour déboguer votre service, vous pouvez désactiver l'option **Régénérer**.  Ainsi, même lorsque vous mettez à jour le service et rouvrez le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], le fichier Client.dll.config est le dernier que vous avez mis à jour et non pas celui qui est régénéré selon le service mis à jour.  
  
 Toutefois, il peut s'avérer nécessaire de modifier le fichier de configuration afin qu'il soit conforme au proxy régénéré.  Si le proxy régénéré et fichier de configuration ne correspondent pas en raison de la mise à jour d'un service, des erreurs se produiront à l'appel du service.  
  
> [!CAUTION]
>  Si vous avez modifié le fichier de configuration client et décidez de le réutiliser ultérieurement, vous le trouverez à l'emplacement suivant :  
>   
>  \\Documents and Settings\\\[Compte d'utilisateur\]\\Mes documents\\Test Client Projects.  
>   
>  Toutes les informations d'identification mises à jour stockées dans le fichier de configuration client sont protégées par la Liste de contrôle d'Accès \(ACL\) de ce dossier.  
  
### Ajout, suppression et actualisation des services  
  
#### Ajouter un service  
 Cliquez sur **Fichier**\-\>**Ajouter un service** pour ajouter un service au client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  Vous devez alors taper l'URI \(adresse de point de terminaison\) du service à ajouter.  L'adresse du service peut être une adresse mex ou WSDL.  
  
 Vous trouverez également une liste contenant 10 points de terminaison de services ajoutés récemment dans le sous\-menu **Services récents**.  Si vous en sélectionnez un, le service spécifié est ajouté au client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
 Vous pouvez également cliquer avec le bouton droit sur la racine de l'arborescence des services **Mes projets de service** et sélectionner **Ajouter un service** pour obtenir le même résultat.  
  
 Pendant la génération d'un proxy, une compilation binaire ou l'appel d'un service, les éléments de menu qui prennent en charge l'ajout d'un service sont désactivés.  L'appel de service est également désactivé.  
  
#### Supprimer un service  
 Cliquez avec le bouton droit sur la racine du service à supprimer, puis sélectionnez **Supprimer le service** afin de supprimer le service du client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
 Pendant la génération d'un proxy, une compilation binaire ou l'appel d'un service, les éléments de menu qui prennent en charge la suppression d'un service sont désactivés.  L'appel de service est également désactivé.  
  
#### Actualiser un service  
 Si une modification est apportée au service pendant que le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est en cours d'exécution et vous souhaitez garantir que l'implémentation du client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pour ce service est à jour, cliquez avec le bouton droit sur la racine du service en question, puis sélectionnez **Actualiser le service**.  Notez qu'après avoir actualisé un service, son état est réinitialisé.  
  
 Pendant la génération d'un proxy, une compilation binaire ou l'appel d'un service, les éléments de menu qui prennent en charge l'actualisation d'un service sont désactivés.  L'appel de service est également désactivé.  
  
## Emplacement des fichiers générés par le client test  
 Par défaut, le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] stocke les fichiers de configuration et de code client générés dans le dossier %appdata%\\Local\\temp\\Test Client Projects.  Ce dossier est supprimé lorsque l'utilisateur quitte le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  Si un fichier de configuration est modifié dans le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et l'option **Toujours régénérer la configuration au démarrage des services** est désactivée, le fichier modifié est copié dans le dossier Cached Config sous Mes documents\\Test Client Projects Documents\\Test Client Projects avec un fichier XML de mappage \(nom du fichier d'adresse des métadonnées\) comme index.  
  
 Vous pouvez également démarrer le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] à partir d'une ligne de commandes, utiliser le commutateur `/ProjectPath` pour spécifier le chemin d'accès du nouvel emplacement où vous voulez stocker les fichiers générés ou utiliser le commutateur `/RestoreProjectPath` pour rétablir l'emplacement par défaut.  La syntaxe est la suivante :  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 L'exécution de cette commande n'ouvre pas le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  Seul l'emplacement du dossier est changé.  Vous pouvez exécuter cette commande que le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] soit en cours d'exécution ou non.  Le nouvel emplacement est validé aussitôt le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] redémarré.  Les informations concernant l'emplacement peuvent être enregistrées dans le Registre ou dans le fichier WcfTestClient.exe.option, dans le dossier %appdata%\\Local\\temp\\Test Client Projects.  
  
## Fonctionnalités prises en charge par le client test WCF  
 La liste suivante répertorie les fonctionnalités prises en charge par le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] :  
  
-   Appel de service : message unidirectionnel et demande\/réponse.  
  
-   Liaisons : toutes les liaisons prises en charge par Svcutil.exe.  
  
-   Contrôle de session.  
  
-   Contrat de message.  
  
-   Sérialisation XML.  
  
 La liste suivante indique les fonctionnalités qui ne sont pas prises en charge par le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] :  
  
-   Types : <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, types qui implémentent l'interface <xref:System.Xml.Serialization.IXmlSerializable>, y compris l'attribut <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> associé et les types <xref:System.Xml.Linq.XDocument> et <xref:System.Xml.Linq.XElement>, ainsi que le type ADO.NET <xref:System.Data.DataTable>.  
  
-   Contrat duplex.  
  
-   Transaction.  
  
-   Sécurité : [!INCLUDE[infocard](../../../includes/infocard-md.md)], certificat et nom d'utilisateur\/mot de passe.  
  
-   Liaisons : WSFederationbinding, toute liaison de contexte et Https, WebHttpbinding \(prise en charge des messages de réponse Json\).  
  
## Fermeture du client test WCF  
 Vous pouvez fermer le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] de différentes façons :  
  
-   Dans le menu **Fichier**, cliquez sur **Quitter**.  Dans la fenêtre principale du client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], vous pouvez également cliquer sur **Fermer**.  Ces deux actions arrêtent également l'hôte de service auto [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et le processus de débogage [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] si le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] a été lancé par [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
-   Cliquez avec le bouton droit sur l'icône **Hôte de service WCF** dans la zone de notification, puis cliquez sur **Quitter**. Cela permet d'arrêter à la fois l'hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], et de mettre fin au processus de débogage [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## Voir aussi  
 [Hôte de service WCF \(WcfSvcHost.exe\)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)