---
title: "Service Trace Viewer Tool (SvcTraceViewer.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 9027efd3-df8d-47ed-8bcd-f53d55ed803c
caps.latest.revision: 55
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 55
---
# Service Trace Viewer Tool (SvcTraceViewer.exe)
L'outil Service Trace Viewer [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] vous aide à analyser des suivis de diagnostic générés par [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].Service Trace Viewer permet de fusionner, d'afficher et de filtrer facilement des messages de suivi dans le journal afin de les diagnostiquer, de les réparer et de vérifier les problèmes des services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
## Configuration du suivi  
 Les suivis de diagnostic vous fournissent des informations qui affichent ce qui arrive pendant le fonctionnement de votre application.Comme son nom l'indique, il permet de suivre le fonctionnement de la source à la destination, ainsi qu'au niveau de points intermédiaires.  
  
 Vous pouvez configurer le suivi à l'aide du fichier de configuration de l'application : Web.config pour les applications hébergées sur le Web ou *Appname*.config pour les applications auto\-hébergées.Par exemple :  
  
```  
<system.diagnostics>  
    <trace autoflush="true" />  
    <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="sdt"   
                   type="System.Diagnostics.XmlWriterTraceListener"   
                   initializeData= "SdrConfigExample.e2e" />  
            </listeners>  
         </source>  
    </sources>  
</system.diagnostics>  
  
```  
  
 Dans cet exemple, le nom et le type de l'écouteur de suivi sont spécifiés.L'écouteur est nommé `sdt` et l'écouteur de suivi standard de .NET Framework \(System.Diagnostics.XmlWriterTraceListener\) est ajouté comme type.L'attribut `initializeData` est utilisé pour définir le nom du fichier journal de cet écouteur sur `SdrConfigExample.e2e`.Pour le fichier journal, vous pouvez substituer un chemin d'accès complet par un nom de fichier simple.  
  
 Cet exemple crée un fichier dans le répertoire racine appelé SdrConfigExample.e2e.Lorsque vous utilisez Trace Viewer pour ouvrir le fichier comme décrit dans la section «  Ouverture et consultation de fichiers de trace WCF », vous pouvez voir tous les messages qui ont été envoyés.  
  
 Le niveau de suivi est contrôlé par le paramètre `switchValue`.Les niveaux de suivi disponibles sont décrits dans le tableau suivant.  
  
|Niveau de suivi|Description|  
|---------------------|-----------------|  
|Critique|-   Enregistre les entrées d'échec et du journal des événements, ainsi que les informations de corrélation de suivi.Les éléments suivants sont quelques exemples de l'utilisation du  niveau critique :<br />-   Votre AppDomain s'est arrêté à cause d'une exception non prise en charge.<br />-   Votre application ne peut pas démarrer.<br />-   Le message qui a provoqué la panne provient du processus MyApp.exe.|  
|Erreur|-   Enregistre toutes les exceptions.Vous pouvez utiliser le niveau Erreur dans les situations suivantes :<br />-   Votre code a échoué à cause d'une exception de cast non valide.<br />-   Une exception d'échec de création de point de terminaison entraîne l'échec de démarrage de votre application..|  
|Avertissement|-   Une condition existe pouvant provoquer par la suite une erreur ou une défaillance critique.Vous pouvez utiliser ce niveau dans les situations suivantes :<br />-   L'application reçoit davantage de demandes que ses paramètres de limitation ne l'autorisent.<br />-   La file d'attente de réception est à 98 pour cent de sa capacité configurée.|  
|Informations|-   Des messages d'aide au contrôle et au diagnostic de l'état système, à la mesure des performances ou au profilage sont générés.Vous pouvez utiliser ces informations pour la planification de capacité et la gestion des performances.Vous pouvez utiliser ce niveau dans les situations suivantes :<br />-   Une défaillance s'est produite après que le message ait atteint AppDomain et ait été désérialisé.<br />-   Une défaillance s'est produite pendant que la liaison HTTP était créée.|  
|Commentaires|-   Suivi au niveau du débogage pour le code utilisateur et la maintenance.Définissez ce niveau lorsque :<br />-   Vous n'êtes pas certain de la méthode appelée lorsque la défaillance s'est produite.<br />-   Un point de terminaison incorrect a été configuré et le service n'a pas pu démarrer parce que l'entrée dans le magasin de réservations était verrouillée.|  
|ActivityTracing|Transfert d'événements entre des activités de traitement et des composants.<br /><br /> Ce niveau permet aux administrateurs et aux développeurs de corréler des applications dans le même domaine d'application.<br /><br /> -   Suivis pour les limites d'activité : démarrage\/arrêt.<br />-   Suivis pour les transferts.|  
  
 Vous pouvez utiliser `add` pour indiquer les nom et type de l'écouteur de suivi à utiliser.Dans l'exemple de configuration, l'écouteur est nommé `sdt` et l'écouteur de suivi standard de .NET Framework \(`System.Diagnostics.XmlWriterTraceListener`\) est ajouté comme type.Utilisez `initializeData` pour définir le nom du fichier journal de cet écouteur.Vous pouvez également remplacer un chemin d'accès complet par un nom de fichier simple.  
  
## Utilisation de l'outil Service Trace Viewer  
  
### Ouverture et consultation de fichiers de suivi WCF  
 Service Trace Viewer prend en charge trois types de fichier :  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Fichier de suivi \(.svcLog\)  
  
-   Les fichiers de suivi d'événement \(.etl\)  
  
-   Les fichiers de suivi Crimson  
  
 Service Trace Viewer permet d'ouvrir tout fichier de suivi pris en charge, d'ajouter et d'intégrer des fichiers de suivi supplémentaires ou d'ouvrir et de fusionner simultanément un groupe de fichiers de suivi.  
  
##### Pour ouvrir un fichier de suivi  
  
1.  Démarrez Service Trace Viewer à l'aide d'une fenêtre de commande afin de naviguer jusqu'à votre emplacement d'installation de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \(C:\\Program Files\\Microsoft SDKs\\Windows\\v6 0\\Bin\), puis tapez `SvcTraceViewer.exe`.  
  
> [!NOTE]
>  L'outil Service Trace Viewer peut être associé à deux types de fichier : .svclog et .stvproj.Vous pouvez utiliser deux paramètres dans la ligne de commande pour inscrire et supprimer l'inscription des extensions de fichier.  
>   
>  \/register : inscrire l'association des extensions de fichier .svclog et .stvproj avec SvcTraceViewer.exe  
>   
>  \/unregister : supprimer l'inscription de l'association des extensions de fichier .svclog et .stvproj avec SvcTraceViewer.exe  
  
1.  Lors du démarrage de Service Trace Viewer, cliquez sur **Fichier** puis pointez sur **Ouvrir**.Naviguez jusqu'à l'emplacement où vos fichiers de suivi sont stockés.  
  
2.  Double\-cliquez sur le fichier de suivi que vous souhaitez ouvrir.  
  
    > [!NOTE]
    >  Appuyez sur MAJ en cliquant sur plusieurs fichiers de suivi pour sélectionner et ouvrir simultanément plusieurs fichiers.Service Trace Viewer fusionne le contenu de tous les fichiers et les affiche.Par exemple, vous pouvez ouvrir des fichiers à la fois de clients et de services.Cela est utile lorsque vous avez activé l'enregistrement de message et la propagation d'activité dans la configuration.Ainsi, vous pouvez consulter l'échange de messages entre le client et le service.Vous pouvez également faire glisser plusieurs fichiers dans Viewer ou utilisez l'onglet **Projet**.Pour plus d'informations, voir la section Gestion de projet.  
  
3.  Pour ajouter des fichiers de suivi supplémentaires à la collection ouverte, cliquez sur **Fichier** puis pointez sur **Ajouter**.Dans la fenêtre qui s'affiche, naviguez jusqu'à l'emplacement des fichiers de suivi et double\-cliquez sur le fichier que vous souhaitez ajouter.  
  
> [!CAUTION]
>  Il n'est pas recommandé de charger un fichier journal de suivi dont la taille est supérieure à 200 Mo.Si vous essayez de charger un fichier plus volumineux, le processus de chargement peut durer longtemps, selon vos ressources informatiques.L'outil Service Trace Viewer peut ne peut pas être réactif pendant une longue période, ou épuiser la mémoire de l'ordinateur.Pour éviter cela, il est recommandé de configurer un chargement partiel.Pour plus d'informations sur la méthode à utiliser, consultez la section consacrée au chargement des fichiers de suivi volumineux.  
  
#### Suivi de fichier d'événement et de fichier Crimson  
 Le format natif de Viewer correspond au format de suivi d'activité que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] émet.Les suivis émis dans un format différent doivent être convertis avant que Viewer les affiche.Actuellement, Viewer prend en charge le format de suivi d'activité mais également de fichiers d'événement et de fichiers Crimson.  
  
 Lorsque vous ouvrez un fichier qui ne contient pas de suivis d'activité, Viewer essaie de convertir le fichier.Vous devez préciser le nom et emplacement du fichier qui contiendra les données de suivi converties.Une fois que les données ont été converties, Viewer affiche le contenu du nouveau fichier.  
  
> [!NOTE]
>  La conversion nécessite de l'espace disque pour stocker les données de suivi converties.Assurez\-vous que vous disposez de suffisamment d'espace disque pour stocker les données avant de démarrer une conversion.Sinon, la conversion échoue.  
  
### Gestion de projets  
 Viewer prend en charge les projets pour faciliter l'affichage de plusieurs fichiers de suivi.Par exemple, si vous avez un fichier de suivi client et un fichier de suivi de service, vous pouvez les ajouter à un projet.Puis, à chaque fois que vous ouvrez le projet, tous les fichiers de suivi du projet sont chargés simultanément.  
  
 Il existe deux façons de gérer des projets :  
  
-   Dans le menu **Fichier**, vous pouvez ouvrir, enregistrer et fermer les projets.  
  
-   Sous l'onglet **Projet**, vous pouvez ajouter des fichiers à un projet.  
  
### Consultation de fichiers de suivi WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] émet des fichiers de suivi à l'aide du format de suivi d'activité.Dans le modèle de suivi d'activité, les suivis individuels sont regroupés par activité en fonction de leur but.Le flux de contrôle logique est transféré entre les activités.Par exemple, pendant la durée de vie d'une application, de nombreuses activités d'envoi de messages apparaissent et disparaissent.Pour plus d'informations sur la consultation des suivis et des activités, ainsi que sur l'interface utilisateur de l'outil Service Trace Viewer, consultez [Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
#### Basculer vers des vues différentes  
 Service Trace Viewer propose les différentes vues suivantes.Elles sont affichées sous forme d'onglets sur le volet gauche de la visionneuse et il est également possible d'y accéder dans le menu **Affichage**.  
  
-   Vue d'activité  
  
-   Vue du projet  
  
-   Vue du message  
  
-   Vue du graphique  
  
##### Vue d'activité  
 Une fois que les fichiers de suivi sont ouverts, vous pouvez consulter les suivis regroupés en activités et affichés dans la fenêtre **Activité**, dans le volet gauche.  
  
 La vue **Activité** affiche le nom des activités, le nombre de suivis dans l'activité, la durée, l'heure de début et de fin.  
  
 Lorsque vous cliquez sur chacune des activités répertoriées, les suivis de cette activité sont affichés à droite dans le volet de suivi.Vous pouvez ensuite sélectionner un suivi pour afficher ses détails.  
  
 Vous pouvez sélectionner plusieurs activités en appuyant sur la touche **CTRL** ou **MAJ** et en cliquant sur les activités souhaitées.Le volet de suivi affiche tous les suivis des activités sélectionnées.  
  
 Vous pouvez double\-cliquer sur une activité pour l'afficher dans la vue **Graphique**.Il est également possible de sélectionner une activité et de basculer vers la vue **Graphique**.  
  
> [!NOTE]
>  L'activité « 000000000000 » est une activité spéciale qui ne peut pas être affichée dans la vue du graphique.Étant donné que toutes les autres activités sont liées à cette activité, l'affichage de celle\-ci a une incidence importante en termes de performances.  
  
 Vous pouvez cliquer sur le titre de colonne pour trier la liste d'activités.Les activités qui contiennent des suivis d'avertissement ont un arrière\-plan jaune et celles qui contiennent des suivis d'erreur ont un arrière\-plan rouge.  
  
 Il existe différents types d'activité et chaque type correspond à une icône sur le côté gauche de chaque activité.Vous pouvez vous reporter à la section Présentation des icônes de suivi pour connaître leur signification.  
  
##### Vue du projet  
 Cette vue vous permet de gérer des fichiers de suivi dans le projet actif.Pour plus d'informations, voir la section Gestion de projet.  
  
##### Vue du graphique  
 L'une des fonctionnalités les plus puissantes de Service Trace Viewer est la vue **Graphique** qui affiche les données de suivi pour une activité donnée sous forme de graphique.Le graphique vous permet de voir l'exécution des événements pas à pas et les relations entre plusieurs activités alors que des données circulent entre elles.  
  
 Pour basculer vers la vue **Graphique**, sélectionnez une activité dans la vue **Activité** et cliquez sur l'onglet **Activité** ou sur un suivi du journal des messages dans la vue **Message**.Si plusieurs fichiers de suivi sont chargés et que l'activité regroupe des suivis de plusieurs fichiers, tous les suivis concernés apparaissent dans la vue Graphique.Vous pouvez également accéder à la vue **Graphique** en double\-cliquant sur les activités et suivis du journal des messages.  
  
 Dans la vue **Graphique**, chaque colonne verticale représente une activité et chaque bloc dans la colonne représente un suivi.Les activités sont regroupées par processus \(ou thread\).Les petites flèches entre les activités représentent des transferts.Les grandes flèches entre les processus représentent l'échange de messages.L'activité sélectionnée est toujours en jaune.  
  
###### Sélection de suivis dans le graphique  
  
1.  Cliquez sur un bloc dans le graphique.  
  
2.  Utilisez les touches haut et bas pour sélectionner les suivis précédents et suivants.  
  
3.  Observez les informations de suivi dans le volet Suivi et le volet Détail.  
  
###### Développement ou réduction de transferts d'activité  
 Vous pouvez développer les transferts d'activité lors du transfert de l'activité sélectionnée vers une autre activité.Cela vous permet de suivre les transferts.  
  
 Pour développer ou réduire des transferts d'activité  
  
1.  Localisez le suivi de transfert avec un symbole « \+ » sur la gauche de l'icône de transfert.  
  
2.  Cliquez sur \+ ou appuyez sur **CTRL** et \+ à l'aide du clavier.  
  
3.  L'activité suivante apparaît dans le graphique.  
  
4.  Un symbole « \- » apparaît à gauche de l'icône de transfert.Cliquez sur le symbole \- ou appuyez sur CTRL et \-. Le transfert d'activité est réduit.  
  
> [!NOTE]
>  Lorsqu'une activité se compose de plusieurs transferts et que vous développez l'un des transferts, les activités entre l'activité racine et la nouvelle activité s'affichent.Ces nouvelles activités apparaissent sous forme réduite.Si vous souhaitez consulter les détails de ces activités, développez\-les verticalement en cliquant sur l'icône de développement dans l'en\-tête du graphique.  
  
###### Développement ou réduction verticaux des activités  
 La visionneuse masque les détails inutiles dans le graphique d'activité en réduisant les activités.Dans une activité réduite, les suivis individuels ne sont pas affichés.Seuls les transferts de suivi apparaissent.Si vous souhaitez consulter tous les suivis d'une activité, développez l'activité verticalement en cliquant sur l'icône de développement de l'activité dans l'en\-tête du graphique.  
  
 Pour développer ou réduire verticalement des activités :  
  
1.  Cliquez sur l'icône \+ dans l'en\-tête d'activité pour développer verticalement l'activité.  
  
2.  Remarquez que tous les suivis sont affichés dans le graphique.  
  
3.  Cliquez sur l'icône \- dans l'en\-tête d'activité pour réduire verticalement l'activité.  
  
4.  Remarquez que seuls les transferts, journaux de messages, suivis d'avertissement et d'exception importants sont affichés dans l'activité.  
  
###### Options  
 Vous pouvez sélectionner deux options dans le menu **Option** à partir de la vue du graphique.  
  
-   Si Afficher les suivis de limite d'activité est désactivé, les suivis de limite d'activité sont ignorés dans le graphique.  
  
-   Si Afficher les suivis de détail d'informations hors message est désactivé, les suivis au niveau de détail d'informations sont ignorés, à l'exception des suivis de messages.Dans la plupart des cas, les suivis au niveau de détail d'informations sont moins importants pour l'analyse.Cette option est utile lorsque vous ne souhaitez pas analyser des suivis au niveau de détail d'informations et que vous souhaitez uniquement vous concentrer sur des suivis plus importants.  
  
###### Mode disposition  
 Viewer se compose de deux modes de disposition : **Processus** et **Thread**.Ce paramètre définit la plus grande unité d'organisation.Le mode de disposition par défaut est **Processus**, ce qui signifie que les activités sont regroupées par processus dans le graphique.  
  
###### Liste d'exécution  
 Dans cette liste déroulante, vous pouvez sélectionner quel processus ou thread vous souhaitez afficher dans le graphique.Par exemple, si les fichiers de suivi de deux clients \(A et B\) et un service sont ouverts, et que vous souhaitiez seulement afficher le service et le client A dans le graphique, vous pouvez désélectionner le client B dans la liste.  
  
#### Affichage des détails de suivi  
 Pour consulter un détail de suivi, sélectionnez un suivi dans le volet Suivi.Les détails sont affichés dans le volet Détails.  
  
##### Volet Suivi  
 Le volet supérieur droit de Service Trace Viewer est le Volet Trace.Il répertorie tous les suivis dans l'activité sélectionnée et inclut des informations supplémentaires telles que le niveau de suivi, l'ID de thread, le nom du processus.  
  
 Vous pouvez copier les éléments XML bruts du suivi vers le Presse\-papiers en cliquant avec le bouton droit sur un suivi et en sélectionnant **Copier le suivi dans le Presse\-papiers**..  
  
##### Volet Détails  
 Le volet gauche inférieur du Service Trace Viewer est le volet Détails.Il se compose de trois onglets pour afficher les détails de suivi.  
  
 La vue **Formaté** affiche les informations de façon plus organisée.Elle répertorie tous les éléments XML connus dans les tables et les arbres et simplifie ainsi la lecture et la compréhension des informations.  
  
 La vue **XML** affiche les éléments XML qui correspondent au suivi sélectionné.Elle prend en charge la mise en surbrillance et la couleur de syntaxe.Lorsque vous utilisez **Rechercher** pour rechercher des chaînes, les résultats de la recherche sont mis en surbrillance.  
  
 La vue **Message** affiche la partie message des éléments XML dans les suivis du journal des messages.Elle est invisible lorsque vous sélectionnez un suivi qui ne contient pas de message.  
  
### Filtrage de suivis WCF  
 Pour simplifier l'analyse de fichiers de suivi, vous pouvez les filtrer selon les méthodes suivantes :  
  
-   La barre d'outils de filtre permet d'accéder aux filtres prédéfinis et personnalisés.Il peut être activé à travers le menu **Affichage**.  
  
-   Le filtre prédéfini de Viewer peut être utilisé pour filtrer des parties des suivis d'infrastructure [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].Par défaut, il est configuré pour permettre à tous les suivis d'infrastructure de passer.Les paramètres de ce filtre sont définis dans le sous\-menu **Options du filtre** du menu **Affichage**.  
  
-   Les filtres XPath personnalisés permettent aux utilisateurs de contrôler entièrement les filtres.Ils peuvent être définis dans le sous\-menu **Filtre personnalisé** du menu **Affichage**.  
  
 Seuls les suivis qui traversent tous les filtres actifs sont affichés.  
  
#### Utilisation de la barre d'outils de filtre  
 La barre d'outils de filtre apparaît dans la partie supérieure de l'outil.Si ce n'est pas le cas, vous pouvez l'activer dans le menu **Affichage**.La barre inclut trois composants :  
  
-   **Rechercher** : ce champ permet de définir le sujet à chercher lors de l'opération de filtrage.Par exemple, si vous souhaitez rechercher tous les suivis émis dans le contexte du processus X, affectez la valeur X à ce champ et la valeur 'Nom Processus' au champ **Rechercher dans**.Ce champ se transforme en contrôle de sélecteur DateTime lorsqu'un filtre temporel est sélectionné.  
  
-   Rechercher dans : ce champ définit le type de filtre à appliquer.  
  
-   Niveau : le paramètre de niveau permet de définir le niveau de suivi minimal autorisé par le filtre.Par exemple, si le niveau est défini sur « Erreur et Haut », seuls les suivis de niveau Erreur et Critique s'affichent.Ce filtre s'associe aux critères spécifiés par Rechercher et Rechercher dans.  
  
 Le bouton **Filtrer maintenant** permet de démarrer l'opération de filtrage.Certains filtres, surtout lorsqu'ils s'appliquent à un ensemble important de données, prennent du temps à se terminer.Vous pouvez annuler l'opération de filtre en appuyant sur le bouton **Arrêter** qui apparaît dans la barre d'état sous le menu **Opérations**.  
  
 Le bouton **Effacer** réinitialise les filtres prédéfinis et personnalisés pour permettre à tous les suivis de passer.  
  
#### Options du filtre  
 Viewer peut supprimer automatiquement les suivis [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] de la vue.Il peut sélectionner les suivis émis en fonction des zones spécifiques de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], par exemple, en supprimant de la vue les suivis liés aux transactions.  
  
 Les paramètres de ce filtre sont définis dans le sous\-menu **Options du filtre** du menu **Affichage**.  
  
#### Filtres personnalisés  
 Si vous connaissez le langage XML XPath, vous pouvez l'utiliser pour créer des filtres personnalisés et rechercher des éléments XML intéressants dans les données de suivi.Vous pouvez accéder aux filtres par la barre d'outils de filtre.  
  
 Les filtres personnalisés peuvent inclure des paramètres.Vous pouvez également importer des filtres préexistants personnalisés.  
  
##### Création d'un filtre personnalisé  
 Il existe deux façons de créer des filtres :  
  
###### Création d'un filtre personnalisé à l'aide de l'Assistant Modèle  
 Vous pouvez cliquer sur un suivi existant et créer un filtre en fonction de la structure du suivi.Cet exemple permet de créer un filtre personnalisé en fonction de l'ID de thread.  
  
1.  Dans le volet de suivi, dans la zone supérieure droite de Trace Viewer, sélectionnez un suivi qui inclut l'élément que vous souhaitez filtrer.  
  
2.  Cliquez sur le bouton **Créer un filtre personnalisé** situé dans la partie supérieure du volet de suivi.  
  
3.  Dans la boîte de dialogue qui s'affiche, entrez un nom pour votre filtre.Dans cet exemple, entrez `Thread ID`.Vous pouvez également fournir une description de votre filtre.  
  
4.  L'arborescence sur la gauche affiche la structure de l'enregistrement de suivi que vous avez sélectionné lors de la première étape.Naviguez jusqu'à l'élément pour lequel vous souhaitez créer une condition.Dans cet exemple, naviguez jusqu'au ThreadID qui doit probablement se trouver dans le nœud XPath  \/E2ETraceEvent\/System\/Execution\/@ThreadID.Double\-cliquez sur l'attribut ThreadID dans l'arborescence.Cela crée à droite de la boîte de dialogue une expression pour l'attribut.  
  
5.  Modifiez le champ de paramètre pour la condition ThreadID de Aucun à '{0}'.Cette étape permet de configurer la valeur de ThreadID lorsque le filtre est appliqué\(voir la section Comment appliquer un filtre\). Vous pouvez définir jusqu'à quatre paramètres.Les conditions sont associées à l'aide de l'opérateur OR.  
  
6.  Cliquez sur **Ok** pour créer le filtre.  
  
> [!NOTE]
>  Une fois qu'un filtre a été créé à l'aide de l'Assistant Modèle, il peut être modifié uniquement manuellement.Il n'est pas possible d'activer l'Assistant pour un filtre qui a été créé précédemment.De plus, les conditions d'un filtre XPath créé dans l'Assistant Modèle sont associées à l'aide de l'opérateur OR.Si vous avez besoin d'une opération AND, vous pouvez modifier l'expression de filtre une fois qu'elle a été créée.  
  
###### Création manuelle d'un filtre personnalisé  
 Le menu Filtres personnalisés vous permet d'entrer des filtres XPath manuellement.  
  
1.  Dans le menu Affichage, cliquez sur l'élément de menu **Filtres personnalisés**.  
  
2.  Dans la boîte de dialogue qui s'affiche, cliquez sur **Nouveau**.  
  
3.  Au minimum, précisez un nom de filtre et une expression XPath.  
  
4.  Cliquez sur **OK**.  
  
###### Application d'un filtre personnalisé  
 Une fois qu'un filtre personnalisé a été créé, il est accessible via la barre d'outils de filtre.Sélectionnez le filtre que vous souhaitez appliquer dans le champ **Rechercher dans** de la barre d'outils de filtre.Pour l'exemple précédent, sélectionnez 'ID Thread'.  
  
1.  Spécifiez la valeur que vous cherchez dans le champ **Rechercher**.Dans notre exemple, entrez l'ID du thread pour lequel vous souhaitez effectuer une recherche.  
  
2.  Cliquez sur **Filtrer maintenant** et examinez le résultat de l'opération.  
  
 Si votre filtre utilise plusieurs paramètres, entrez\-les en utilisant « ; » comme séparateur dans le champ **Rechercher**.Par exemple, la chaîne suivante définit trois paramètres : '1;findValue;text'.La visionneuse applique la valeur '1' au paramètre {0} du filtre.'findValue' et 'text' sont appliqués à {1} et {2} respectivement.  
  
###### Partage de filtres personnalisés  
 Les filtres personnalisés peuvent être partagés entre différentes sessions et différents utilisateurs.Vous pouvez exporter les filtres vers un fichier de définition et importer ce fichier vers un autre emplacement.  
  
 Pour importer un filtre personnalisé :  
  
1.  Dans le menu **Affichage**, cliquez sur **Filtres personnalisés**.  
  
2.  Dans la boîte de dialogue qui s'affiche, cliquez sur le bouton **Importer**.  
  
3.  Naviguez jusqu'au fichier de filtre personnalisé \(.stvcf\), cliquez sur le fichier et cliquez sur le bouton **Ouvrir**.  
  
 Pour exporter un filtre personnalisé :  
  
1.  Dans le menu Affichage, cliquez sur **Filtres personnalisés**.  
  
2.  Dans la boîte de dialogue qui s'affiche, sélectionnez le filtre que vous souhaitez exporter.  
  
3.  Cliquez sur le bouton **Exporter**.  
  
4.  Précisez le nom et l'emplacement du fichier de définition du filtre personnalisé \(.stvcf\) et cliquez sur le bouton **Enregistrer**.  
  
> [!NOTE]
>  Ces filtres personnalisés peuvent uniquement être importés et exportés à partir de Service Trace Viewer.Ils ne peuvent pas être lus par d'autres outils.  
  
### Recherche de données  
 L'outil Viewer permet de rechercher des données selon les méthodes suivantes :  
  
-   La barre d'outils Rechercher fournit un accès rapide aux options de recherche les plus courantes.  
  
-   La boîte de dialogue Rechercher fournit des options de recherche supplémentaires.Vous pouvez y accéder par le menu **Edition** ou à l'aide des touches de raccourci CTRL \+ F.  
  
 La barre d'outils Rechercher apparaît en haut de l'outil Viewer.Si ce n'est pas le cas, vous pouvez l'activer dans le menu **Affichage**.La barre se compose de deux composants :  
  
-   Rechercher : vous pouvez y entrer un mot clé de recherche.  
  
-   Regardez dans : vous pouvez y entrer la zone de recherche.Vous pouvez choisir d'effectuer une recherche dans toutes les activités ou dans l'activité en cours uniquement.  
  
 La boîte de dialogue de recherche fournit deux options supplémentaires :  
  
-   Rechercher la cible :  
  
    -   L'option Données brutes du journal permet de chercher le mot clé dans toutes les données brutes.  
  
    -   Les options Texte XML et Attribut XML permettent d'effectuer une recherche uniquement dans les éléments XML.  
  
    -   L'option Message consigné permet de rechercher uniquement le mot clé dans les messages.  
  
-   Ignorer l’activité racine : la recherche ignore les suivis dans l'activité 000000000000.Cela permet d'améliorer les performance dans les fichiers de suivi volumineux lorsque l'activité racine se compose de milliers de suivis dont la plupart sont des transferts.  
  
### Navigation parmi les suivis  
 Parce que les suivis sont enregistrés pas à pas pendant l'exécution des applications, la navigation parmi les suivis peut vous aider à déboguer votre application.Service Trace Viewer fournit différentes façons de naviguer dans les suivis.  
  
#### Étape suivante ou Étape précédente  
 Si vous considérez chaque suivi comme une ligne de code du programme, « Étape suivante » est une opération similaire à l'opération « Pas à pas principal » dans l'environnement de développement intégré Visual Studio \(IDE\).La différence est que vous pouvez également revenir en arrière dans les suivis.« Étape suivante » vous permet de passer au suivi suivant dans l'activité.  
  
-   Étape suivante : utilisez le menu **Activité** ou appuyez sur F10Vous pouvez également utiliser la touche BAS dans le volet de suivi.  
  
-   Étape précédente : utilisez le menu **Activité** ou appuyez sur F9Vous pouvez également utiliser la touche HAUT dans le volet de suivi.  
  
> [!NOTE]
>  Une activité peut ainsi se produire dans un processus différent ou même sur un autre ordinateur, parce que les messages [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] peuvent contenir des ID d'activité applicables à différents ordinateurs.  
  
#### Suivre le transfert  
 Les suivi de transfert sont des suivis spéciaux dans le fichier de suivi.Il est possible d'effectuer un transfert d'une activité vers une autre activité par le biais d'un suivi de transfert.Par exemple, il est possible de transférer « Activité A » vers « Activité B ».Dans ce cas, un suivi de transfert est créé dans Activité A avec le nom À : Activité et l'icône de transfert.Ce suivi de transfert est un lien entre les deux suivis.Dans « Activité B », il peut y avoir également un suivi de transfert à la fin de l'activité pour rétablir le transfert vers « Activité A ».Ce processus est identique aux appels de fonctions dans les programmes: A appelle B, puis B retourne l'appel.  
  
 « Suivre le transfert » est semblable à « Pas à pas détaillé » dans un débogueur.Il suit le transfert de l'activité A vers l'activité B.Il n'a aucun effet sur les autres suivis.  
  
 Il existe deux façons de suivre un transfert : à l'aide de la souris ou du clavier :  
  
-   À l'aide de la souris : double\-cliquez sur le suivi de transfert dans le volet de suivi.  
  
-   À l'aide du clavier : sélectionnez un suivi de transfert et utilisez « Suivre le transfert » dans le menu **Activité** ou appuyez sur F11.  
  
> [!NOTE]
>  Dans de nombreux cas, lors d'un transfert de l'activité A vers l'activité B, l'activité A attend le transfert de retour de l'activité B vers l'activité A.Cela signifie qu'aucun suivi n'est enregistré par l'activité A lors du suivi actif de l'activité B.Toutefois, il est également possible que l'activité A n'attende pas et continue à enregistrer des suivis.Il est également possible que l'activité B n'effectue pas de transfert en retour vers l'activité A.Par conséquent, les transferts d'activité sont encore différents des appels de fonction.La vue Graphique vous permet de mieux comprendre les transferts d'activité.  
  
#### Passer au transfert suivant ou précédent  
 Lorsque vous analysez l'activité en cours ou certaines activités sélectionnées en cas de sélection de plusieurs activités, vous pouvez rechercher rapidement les activités vers lesquelles des transferts sont effectués.« Passer au transfert suivant » vous permet d'identifier le suivi de transfert suivant dans l'activité.Une fois que vous avez trouvé le suivi de transfert, vous pouvez utiliser « Suivre le transfert » pour effectuer un pas à pas détaillé vers l'activité suivante.  
  
-   Passer au transfert suivant : utilisez le menu **Activité** ou appuyez sur CTRL \+ F10.  
  
-   Passer au transfert précédent : utilisez le menu **Activité** ou appuyez sur CTRL \+ F9.  
  
#### Naviguer dans la vue Graphique  
 La navigation dans le volet d'activité et le volet de suivi est similaire au débogage mais la vue **Graphique** améliore la navigation.Pour plus d'informations, consultez la section consacrée à la vue Graphique.  
  
### Chargement de fichiers de suivi volumineux  
 Les fichiers de suivi peuvent être volumineux.Par exemple, si vous activez le suivi au niveau « Commentaires », la taille du fichier de suivi obtenu après une exécution de quelques minutes peut facilement atteindre quelques centaines de mégaoctets ou même plus, selon la vitesse du réseau et du modèle de communication.  
  
 Lorsque vous ouvrez un fichier de suivi volumineux dans Service Trace Viewer, cela peut avoir une incidence néfaste sur les performances système.La vitesse de chargement et le temps de réponse après le chargement peut être lent.La vitesse réelle diffère et dépend de votre configuration matérielle.Dans la plupart des PC, le chargement d'un fichier de suivi de taille supérieure à 200 Mo peut avoir une incidence néfaste sur les performances.Pour les fichiers de suivi de taille supérieure à 1 Go, il est possible que l'outil utilise toute la mémoire disponible ou cesse de répondre pendant un très long moment.  
  
 Pour éviter ce ralentissement du chargement et du temps de réponse pour analyser les fichiers de suivi volumineux, Service Trace Viewer fournit une fonctionnalité appelée Chargement partiel qui charge uniquement le suivi par petites parties.Par exemple, un fichier de suivi de taille supérieure à 1 Go peut s'exécuter pendant plusieurs jours sur le serveur.Lorsque certaines erreurs se sont produites et que vous souhaitez analyser le suivi, vous n'avez pas besoin d'ouvrir entièrement le fichier de suivi.Vous pouvez charger les suivis au moment où l'erreur a pu se produire.Étant donné que l'étendue est plus petite, l'outil Service Trace Viewer peut charger le fichier plus rapidement et vous pouvez identifier les erreurs à l'aide d'un groupe de données plus petit.  
  
#### Activation du chargement partiel  
 Vous n'avez pas besoin d'activer manuellement le chargement partiel.Si la taille totale des fichiers de suivi que vous essayez de charger dépasse 40 Mo, Service Trace Viewer affiche automatiquement une boîte de dialogue Chargement partiel pour que vous puissiez sélectionner la partie que vous souhaitez charger.  
  
> [!NOTE]
>  Étant donné que les suivis ne sont pas toujours répartis de façon régulière dans l'intervalle de temps, la durée que vous spécifiez dans la barre d'outils Chargement partiel n'est peut être pas proportionnelle à la taille de chargement affichée.La taille de chargement réelle peut être plus petite que la taille estimée dans la boite de dialogue de chargement partiel.  
  
#### Ajuster le chargement partiel  
 Une fois que vous avez chargé partiellement le fichier de suivi, vous pouvez modifier le groupe de données en cours de chargement.Vous pouvez l'effectuer en ajustant la barre d'outils Chargement partiel dans la partie supérieure de Viewer.  
  
1.  Déplacez la barre d'outils à l'aide de la souris ou indiquez le début et la fin du chargement partiel.  
  
2.  Cliquez sur le bouton **Ajuster**.  
  
## Fonctionnement des icônes de suivi  
 Les éléments suivants sont une liste des icônes que l'outil Service Trace Viewer utilise dans la vue **Activité**, dans la vue **Graphique** et dans le volet **Suivi** pour représenter différents éléments.  
  
> [!NOTE]
>  Certains suivis non catégorisés \(par exemple, « un message est fermé »\) n'ont aucune icône.  
  
### Suivi d'activité  
  
|Icône|Description|  
|-----------|-----------------|  
|![Trace d'avertissement](../../../docs/framework/wcf/media/7457c4ed-8383-4ac7-bada-bcb27409da58.gif "7457c4ed\-8383\-4ac7\-bada\-bcb27409da58")|Suivi d'avertissement : suivi émis au niveau avertissement|  
|![Trace d'erreur](../../../docs/framework/wcf/media/7d908807-4967-4f6d-9226-d52125db69ca.gif "7d908807\-4967\-4f6d\-9226\-d52125db69ca")|Suivi d'erreur: suivi émis au niveau erreur.|  
|![Trace du démarrage de l'activité :](../../../docs/framework/wcf/media/8a728f91-5f80-4a95-afe8-0b6acd6e0317.gif "8a728f91\-5f80\-4a95\-afe8\-0b6acd6e0317")|Suivi de démarrage d'activité : suivi qui marque le début d'une activité.Il contient le nom de l'activité.En tant que concepteur ou développeur d'applications, vous devez définir un suivi de démarrage d'activité par ID d'activité par processus ou thread.<br /><br /> Si l'ID d'activité est propagé à travers des sources de suivi pour la corrélation de suivis, vous pouvez consulter plusieurs démarrages pour le même ID d'activité \(un par source de suivi\).Le suivi de démarrage est émis si le suivi d'activités est activé pour la source de suivi.|  
|![Trace de l'arrêt de l'activité](../../../docs/framework/wcf/media/a0493e95-653e-4af8-84a4-4d09a400bc31.gif "a0493e95\-653e\-4af8\-84a4\-4d09a400bc31")|Suivi d'arrêt d'activité : suivi qui marque la fin d'une activité..Il contient le nom de l'activité.En tant que concepteur ou développeur d'applications, vous devez définir un suivi d'arrêt d'activité par ID d'activité par source de suivi.Aucun suivi de source de suivi n'apparaît après le suivi d'arrêt d'activité émis par la source de suivi, sauf si la granularité de l'heure du suivi n'est pas suffisamment réduite.Lorsque cela se produit, deux suivis portant la même heure, y compris un arrêt, peuvent être entrelacés lorsqu'ils sont affichés.Si l'ID d'activité est propagé à travers les sources de suivi pour la corrélation de suivis, vous pouvez consulter plusieurs arrêts pour le même ID d'activité \(un par source de suivi\).Le suivi d'arrêt est émis si le suivi d'activités est activé pour la source de suivi.|  
|![Trace d'interruption de l'activité](../../../docs/framework/wcf/media/6f7f4191-df2b-4592-8998-8379769e2d32.gif "6f7f4191\-df2b\-4592\-8998\-8379769e2d32")|Suivi d'interruption d'activité : suivi qui marque l'heure à laquelle une activité marque une pause.Aucun suivi n'est émis pendant l'interruption d'une activité, jusqu'à ce que l'activité reprenne.Une activité interrompue indique qu'aucun traitement ne parvient à cette activité au niveau de la source de suivi.Les suivis d'interruption\/reprise sont utiles pour effecteur des profilages.Le suivi d'interruption est émis si le suivi d'activités est activé pour la source de suivi.|  
|![Trace de la reprise de l'activité](../../../docs/framework/wcf/media/1060d9d2-c9c8-4e0a-9988-cdc2f7030f17.gif "1060d9d2\-c9c8\-4e0a\-9988\-cdc2f7030f17")|Suivi de reprise d'activité : suivi qui marque l'heure à laquelle une activité reprend après avoir été interrompue.Les suivis peuvent être émis de nouveau dans cette activité.Les suivis d'interruption\/reprise sont utiles pour effecteur des profilages.Le suivi de reprise est émis si le suivi d'activités est activé pour la source de suivi.|  
|![Transférer](../../../docs/framework/wcf/media/b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5.gif "b2d9850e\-f362\-4ae5\-bb8d\-9f6f3ca036a5")|Transfert : un suivi est émis lorsque le flux de contrôle logique est transféré d'une activité à une autre.L'activité dont provient le transfert peut continuer à fonctionner en parallèle de l'activité vers laquelle le transfert se dirige.Le suivi de transfert est émis si le suivi d'activités est activé pour la source de suivi.|  
|![Transférer depuis](../../../docs/framework/wcf/media/1df215cb-b344-4f36-a20d-195999bda741.gif "1df215cb\-b344\-4f36\-a20d\-195999bda741")|Transfert De : suivi qui définit un transfert d'une autre activité vers l'activité actuelle.|  
|![Transférer à](../../../docs/framework/wcf/media/74255b6e-7c47-46ef-8e53-870c76b04c3f.gif "74255b6e\-7c47\-46ef\-8e53\-870c76b04c3f")|Transfert A : suivi qui définit un transfert de flux de contrôle logique de l'activité actuelle vers une autre activité.|  
  
### Suivis WCF  
  
|Icône|Description|  
|-----------|-----------------|  
|![Trace du journal des messages](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994\-2476\-4260\-a0db\-98948b9af197")|Suivi du journal des messages : suivi émis lorsqu'un message [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est enregistré par la fonctionnalité de journalisation des messages lorsque la source du suivi `System.ServiceModel.MessageLogging` est activée.Un clic sur ce suivi permet d'afficher le message.Il existe quatre points d'enregistrement configurables pour un message : ServiceLevelSendRequest, TransportSend, TransportReceive et ServiceLevelReceiveRequest, qui peut également être spécifié par l'attribut `messageSource` dans le suivi du journal des messages.|  
|![Trace des messages reçus](../../../docs/framework/wcf/media/de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c.gif "de4f586c\-c5dd\-41ec\-b1c3\-ac56b4dfa35c")|Suivi de message reçu : suivi émis lorsqu'un message [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est reçu, si la source de suivi `System.ServiceModel` est activée au niveau Informations ou Commentaires.Ce suivi est essentiel pour consulter la flèche de corrélation de messages dans la vue **Graphique** de l'activité.|  
|![Trace du message envoyé](../../../docs/framework/wcf/media/558943c4-17cf-4c12-9405-677e995ac387.gif "558943c4\-17cf\-4c12\-9405\-677e995ac387")|Suivi de message envoyé : suivi émis lorsqu'un message [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est envoyé, si la source de suivi `System.ServiceModel` est activée au niveau Informations ou Commentaires.Ce suivi est essentiel pour consulter la flèche de corrélation de messages dans la vue **Graphique** de l'activité.|  
  
### Activités  
  
|Icône|Description|  
|-----------|-----------------|  
|![Activité](../../../docs/framework/wcf/media/wcfc-defaultactivityc.gif "wcfc\_defaultActivityc")|Activité : indique que l'activité actuelle est une activité générique.|  
|![Activité racine](../../../docs/framework/wcf/media/5dc8e0eb-1c32-4076-8c66-594935beaee9.gif "5dc8e0eb\-1c32\-4076\-8c66\-594935beaee9")|Activité racine : indique l'activité racine d'un processus.|  
  
### Activités WCF  
  
|Icône|Description|  
|-----------|-----------------|  
|![Activité d'environnement](../../../docs/framework/wcf/media/29fa00ac-cf78-46e5-822d-56222fff61d1.gif "29fa00ac\-cf78\-46e5\-822d\-56222fff61d1")|Activité d'environnement : activité qui crée, ouvre ou ferme un hôte ou un client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].Les erreurs qui se sont produites pendant ces phases apparaîtront dans cette activité.|  
|![Activité Listen](../../../docs/framework/wcf/media/d7b135f6-ec7d-45d7-9913-037ab30e4c26.gif "d7b135f6\-ec7d\-45d7\-9913\-037ab30e4c26")|Activité d'écoute : activité qui enregistre les suivis relatifs à un écouteur.À l'intérieur de cette activité, vous pouvez consulter des informations et des demandes de connexion relatives à l'écouteur.|  
|![Activité de réception d'octets](../../../docs/framework/wcf/media/2f628580-b80f-45a7-925b-616c96426c0e.gif "2f628580\-b80f\-45a7\-925b\-616c96426c0e")|Activité Recevoir des octets : activité qui regroupe toutes les traces en rapport avec les octets entrants et sortants sur une connexion entre deux points de terminaison.Cette activité est essentielle pour la corrélation avec les activités de transport qui propagent leur ID d'activité tel que http.sys.Les erreurs de connexion telles que les abandons apparaîtront dans cette activité.|  
|![Activité ProcessMessage](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc\_ExecutionActivityIconc")|Activité Traiter le message : activité qui regroupe les suivis en rapport avec la création d'un message [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].Les erreurs dues à une mauvaise enveloppe ou à un message erroné apparaîtront dans cette activité.À l'intérieur de cette activité, vous pouvez contrôler les en\-têtes de message à afficher si un ID d'activité a été propagé à partir de l'appelant.Si cela se vérifie, lors du transfert vers l'activité Traiter l'action \(l'icône suivante\), vous pouvez également assigner à cette activité l'ID d'activité propagé pour la corrélation entre l'appelant et les suivis d'appelé.|  
|![Trace du journal des messages](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994\-2476\-4260\-a0db\-98948b9af197")|Activité Traiter l'action : activité qui regroupe tous les suivis en rapport avec une demande [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] entre deux points de terminaison.Si `propagateActivity` a la valeur `true` sur les deux points de terminaison de la configuration, tous les suivis des deux points de terminaison sont fusionnés au sein d'une activité, à des fins de corrélation directe.Cette activité contiendra des erreurs en raison du traitement du transport ou de la sécurité, au niveau de la limite du code utilisateur \(si une réponse existe\).|  
|![Activité ProcessMessage](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc\_ExecutionActivityIconc")|Activité Exécuter le code utilisateur : activité qui regroupe les suivis de code utilisateur pour le traitement d'une demande.|  
  
## Résolution des problèmes  
 Si vous n'avez pas l'autorisation d'écrire dans le registre, vous obtenez le message d'erreur suivant : « Microsoft Service Trace Viewer n'était pas enregistré dans le système. » lorsque vous utilisez la commande "`svctraceviewer /register` pour enregistrer l'outil.Si cela se produit, vous devez vous connecter en utilisant un compte qui possède un accès en écriture au registre.  
  
 De plus, l'outil Service Trace Viewer écrit certains paramètres \(par exemple, filtres personnalisés et options du filtre\) dans le fichier SvcTraceViewer.exe., dans son dossier assembly.Si vous ne disposez pas d'une autorisation de lecture pour le fichier, vous pouvez malgré tout lancer l'outil, mais vous ne pouvez pas charger les paramètres.  
  
 Si le message d'erreur « Une erreur inconnue s'est produite lors du traitement d'un ou de plusieurs suivis. » lors de l'ouverture du fichier .etl, cela signifie que le format du fichier .etl n'est pas valide.  
  
 Si vous ouvrez un journal des suivis créé à l'aide d'un système d'exploitation arabe, vous pouvez remarquer que le filtre temporel ne fonctionne pas.Par exemple, l'année 2005 correspond à année 1427 dans le calendrier arabe.Toutefois, la plage temporelle prise en charge par le filtre de l'outil Service Trace Viewer ne prend pas en charge de date antérieure à 1752.Cela peut vous empêcher de sélectionner une date correcte dans le filtre.Pour résoudre ce problème, vous pouvez créer un filtre personnalisé \(**Affichage\/Filtres personnalisés**\) à l'aide d'une expression XPath, afin d'inclure une plage temporelle spécifique.  
  
## Voir aussi  
 [Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)   
 [Configuration du suivi](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)   
 [Activity Tracing and Propagation for End\-To\-End Trace Correlation](http://msdn.microsoft.com/fr-fr/2c11a905-64f8-47b5-bae5-a74fc666137e)