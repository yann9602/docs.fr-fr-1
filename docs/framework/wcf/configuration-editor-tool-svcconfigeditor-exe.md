---
title: "Outil Éditeur de configuration (SvcConfigEditor.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
caps.latest.revision: "45"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a301e23ead8e52273ed4fe7a503f1fe11e2f1348
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a>Outil Éditeur de configuration (SvcConfigEditor.exe)
L'Éditeur de configuration de service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] (SvcConfiEditor.exe) permet aux administrateurs et aux développeurs de créer et de modifier des paramètres de configuration pour les services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] à l'aide d'une interface graphique utilisateur. Grâce à cet outil, vous pouvez gérer les paramètres des liaisons, des comportements, des services et des diagnostics [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sans modifier directement les fichiers de configuration XML.  
  
 L'Éditeur de configuration de service se trouve dans le dossier C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.  
  
## <a name="the-wcf-configuration-editor"></a>Éditeur de configuration WCF  
 L'Éditeur de configuration de service est fourni avec un Assistant qui vous guide à travers toutes les étapes de configuration d'un service ou d'un client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Il est vivement recommandé d'utiliser l'Assistant au lieu d'utiliser directement l'éditeur.  
  
 Si vous avez déjà quelques fichiers de configuration conformes au schéma System.Configuration standard, vous pouvez gérer des paramètres spécifiques pour les liaisons, comportements, services et diagnostics avec l'interface utilisateur. L'Éditeur de configuration de service vous permet de gérer les paramètres des fichiers de configuration [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] existants, ainsi que les fichiers exécutables, les services COM+ et les services hébergés sur le Web. Lorsque vous ouvrez un service hébergé sur le Web au moyen de l'Éditeur de configuration de service, vous accédez à la propre configuration du service et aux sections de configurations héritées des nœuds de niveau supérieur.  
  
 Les paramètres de configuration [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sont situés dans la section `<system.serviceModel>` du fichier de configuration ; par conséquent, l'éditeur fonctionne exclusivement sur le contenu de cet élément et n'accède pas à d'autres éléments du même fichier. Vous pouvez naviguer directement jusqu'aux fichiers de configuration existants ou vous pouvez sélectionner un assembly qui contient un service, un répertoire virtuel ou un service COM+. L'éditeur charge le fichier de configuration pour ce service particulier et autorise l'utilisateur à ajouter des nouveaux éléments ou à modifier des éléments existants imbriqués dans la section `<system.serviceModel>` du fichier de configuration.  
  
 L'éditeur prend en charge IntelliSense et applique la conformité de schéma. Le résultat est conformer au schéma du fichier de configuration et possède des valeurs de données correctes syntaxiquement. Toutefois, l'éditeur ne garantit pas que le fichier de configuration soit correct sur un plan sémantique. En d'autres termes, l'éditeur ne garantit pas que le fichier de configuration puisse fonctionner avec le service qu'il configure.  
  
> [!CAUTION]
>  L'éditeur ne peut pas supprimer un élément de configuration du fichier de configuration une fois que vous avez modifié l'élément. Par exemple, si vous utilisez l'éditeur pour affecter au nom de point de terminaison une chaîne non vide et l'enregistrer, le contenu du fichier de configuration est le suivant, comme illustré dans l'exemple suivant.  
>   
>  `<endpoint binding="basicHttpBinding" name="somename" />`  
>   
>  Si vous tentez de supprimer le nom en lui affectant une chaîne vide et que vous enregistrez le fichier, le fichier de configuration contient toujours l'attribut `name`, comme illustré dans l'exemple suivant.  
>   
>  `<endpoint binding="basicHttpBinding" name="" />`  
>   
>  Pour supprimer l'attribut, vous devez modifier manuellement l'élément à l'aide d'un autre éditeur de texte.  
>   
>  Vous devez être particulièrement prudent avec ce problème lorsque vous utilisez l'élément `issueToken` du comportement de point de terminaison `clientCredential`. De façon spécifique, l'attribut `address` de son sous-élément `localIssuer` ne doit pas être une chaîne vide. Si vous avez modifié l'attribut `address` à l'aide de l'Éditeur de configuration et que vous souhaitez le supprimer complètement, vous devez pour cela utiliser un autre outil que l'Éditeur. Sinon, l'attribut contient une chaîne vide et votre application lève une exception.  
  
## <a name="using-the-configuration-editor"></a>Utilisation de l'Éditeur de configuration  
 L'Éditeur de configuration de service se trouve à l'emplacement d'installation du Kit de développement logiciel (SDK) Windows suivant :  
  
 C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe  
  
 Une fois que vous lancez l’éditeur de Configuration de Service, vous pouvez utiliser la **fichier/ouvrir** menu pour accéder au service ou d’un assembly que vous souhaitez gérer. Vous pouvez ouvrir des fichiers de configuration directement, rechercher des services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] /COM + et ouvrir des fichiers de configuration pour des services hébergés par le Web.  
  
 L'interface utilisateur de l'Éditeur de configuration de service est divisée dans les zones suivantes :  
  
-   Volet (arborescence) qui affiche les éléments de configuration sous forme d'arborescence à gauche. Vous pouvez exécuter des opérations dans l'arbre en cliquant avec le bouton droit sur les nœuds.  
  
-   Volet de tâches qui présente les tâches courantes applicables aux éléments actuels dans la partie inférieure gauche de la fenêtre.  
  
-   Volet Détail qui affiche les paramètres détaillés du nœud de configuration sélectionné dans l'arborescence à droite.  
  
### <a name="opening-a-configuration-file"></a>Ouverture d'un fichier de configuration  
  
1.  Démarrez l’éditeur de Configuration de Service à l’aide d’une fenêtre de commande pour accéder à votre [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] emplacement d’installation, puis tapez `SvcConfigEditor.exe`.  
  
2.  À partir de la **fichier** menu, sélectionnez **ouvrir** et cliquez sur le type de fichier que vous souhaitez gérer.  
  
3.  Dans le **ouvrir** boîte de dialogue, accédez au fichier spécifique que vous souhaitez gérer et double-cliquez dessus.  
  
 La visionneuse suit automatiquement le chemin d’accès de fusion de la configuration et crée une vue de la configuration fusionnée. Par exemple, la configuration réelle d'un service non hébergé est une combinaison de Machine.config et App.config. Toutes les modifications sont appliquées au fichier actif dans SvcConfigEditor. Si vous souhaitez modifier un fichier spécifique dans le chemin d'accès de fusion de la configuration, vous devez l'ouvrir directement.  
  
> [!NOTE]
>  L'Éditeur de configuration recharge le fichier de configuration actuellement ouvert lorsque ce dernier a été modifié à l'extérieur de l'Éditeur. Lorsque cela se produit, toutes les modifications non enregistrées dans l'Éditeur sont perdues. Si les rechargements sont fréquents, la cause la plus probable est l'accès constant d'un service au fichier de configuration (par exemple, un logiciel antivirus exécuté en arrière-plan). Pour y remédier, vérifiez que l'éditeur de configuration est l'unique processus autorisé à accéder au fichier lorsque celui-ci est ouvert.  
  
### <a name="services"></a>Services  
 Le **Services** nœud affiche tous les services assignés actuellement dans le fichier de configuration. Chaque nœud secondaire dans l’arborescence correspond à un sous-élément de la <`services`> élément dans le fichier de configuration.  
  
 Lorsque vous cliquez sur le **Services** nœud, vous pouvez afficher ou exécuter des tâches dans la Page de résumé dans le **détail** volet.  
  
#### <a name="creating-a-new-service-configuration"></a>Création d'une configuration de service  
 Vous pouvez créer une configuration de service de l'une des manières suivantes :  
  
-   À l’aide d’un Assistant : cliquez sur le lien **créer un nouveau Service...** dans le volet de tâches ou la Page de résumé pour lancer l’Assistant. Vous pouvez également l’effectuer dans le **fichier** menu -> **ajouter un nouvel élément**.  
  
-   Créer manuellement : vous pouvez cliquer sur le **Services** nœud et choisissez **nouveau Service**.  
  
#### <a name="creating-a-new-service-endpoint-configuration"></a>Création d'une configuration de point de terminaison de service  
 Vous pouvez créer une nouvelle configuration de point de terminaison de service de l'une des manières suivantes :  
  
-   Créer à l’aide d’un Assistant : cliquez sur le lien **créer un nouveau point de terminaison de Service...** dans le volet de tâches ou la Page de résumé pour lancer l’Assistant. Vous pouvez également l’effectuer dans le **fichier** menu -> **ajouter un nouvel élément**.  
  
-   Créer manuellement : une fois que vous avez créé un Service, vous pouvez cliquer sur le **points de terminaison** nœud et choisissez «**nouveau point de terminaison de Service**».  
  
#### <a name="editing-a-service-configuration"></a>Modification d'une configuration de service  
  
1.  Cliquez sur un **Service** nœud.  
  
2.  Modifiez les paramètres dans les grilles de propriété.  
  
#### <a name="editing-a-service-endpoint-configuration"></a>Modification d'une configuration de points de terminaison de service  
  
1.  Cliquez sur un **point de terminaison de Service** nœud.  
  
2.  Modifiez les paramètres dans les grilles de propriété.  
  
#### <a name="adding-a-base-address"></a>Ajout d'une adresse de base  
  
1.  Cliquez sur le **hôte** nœud.  
  
2.  Cliquez sur le **nouveau...** bouton dans le **les adresses de Base** section.  
  
3.  Tapez l'URI de l'adresse de base dans la boîte de dialogue.  
  
4.  Cliquez sur **OK**.  
  
> [!NOTE]
>  Vous ne pouvez pas modifier la valeur de [ \<baseAddressPrefixFilters >](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) à l’intérieur de cet outil. Pour ajouter ou modifier cet élément, vous devez utiliser un éditeur de texte ou [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
### <a name="client"></a>Client  
 Le **Client** nœud affiche tous les points de terminaison client dans le fichier de configuration. Chaque nœud secondaire dans l’arborescence correspond à un sous-élément de la <`client`> élément dans le fichier de configuration.  
  
 Lorsque vous cliquez sur le **Client** nœud, vous pouvez afficher ou exécuter des tâches sur le client **Page Résumé** dans les **volet Détail**.  
  
#### <a name="creating-a-new-client-endpoint-configuration"></a>Création d'une configuration de point de terminaison client  
 Vous pouvez créer une configuration de point de terminaison client de l'une des manières suivantes :  
  
-   Créer par l’Assistant : cliquez sur le lien **créer un nouveau Client en cours...** sur le **volet** sur inférieur gauche de la fenêtre, ou **Page Résumé** pour lancer l’Assistant. Vous pouvez également l’effectuer dans le **fichier** menu -> **ajouter un nouvel élément**. L'Assistant vous invite à désigner l'emplacement de la configuration du service, à partir duquel la configuration cliente est générée. Vous pouvez alors choisir le point de terminaison de service avec lequel établir une connexion.  
  
-   Créer manuellement : avec le bouton droit le **points de terminaison** nœud sous **Client**, puis choisissez **nouveau point de terminaison Client**.  
  
#### <a name="editing-a-client-endpoint-configuration"></a>Modification d'une configuration de point de terminaison client  
  
1.  Cliquez sur un **point de terminaison Client** nœud.  
  
2.  Modifiez les paramètres dans les grilles de propriété.  
  
### <a name="standard-endpoint"></a>Point de terminaison standard  
 Les points de terminaison standard sont des points de terminaison spécialisés possédant une ou plusieurs parties de l’adresse, contrat et liaison définies sur les valeurs par défaut.  
  
 Ces paramètres de configuration sont stockés dans le **point de terminaison Standard** nœud. Le **point de terminaison Standard** nœud affiche tous les paramètres de point de terminaison standard dans le fichier de configuration. Chaque nœud secondaire dans l’arborescence correspond à un sous-élément dans le `<standardEndpoints>` élément dans le fichier de configuration.  
  
 Lorsque vous cliquez sur le **point de terminaison Standard** nœud, vous pouvez afficher ou exécuter des tâches sur le point de terminaison standard **Page Résumé** dans les **volet Détail**.  
  
#### <a name="creating-a-new-standard-endpoint-configuration"></a>Création d'une configuration de point de terminaison standard  
 Vous pouvez créer une configuration de point de terminaison standard de l'une des manières suivantes :  
  
-   Cliquez sur le **point de terminaison Standard** nœud et sélectionnez **nouvelle Configuration de point de terminaison Standard...** Sélectionnez le type de liaison dans la boîte de dialogue, cliquez sur **OK**.  
  
-   Sélectionnez le **point de terminaison Standard** nœud et cliquez sur **nouvelle Configuration de point de terminaison Standard...** dans le **volet** sur bas à gauche de la fenêtre.  
  
 Le **création d’un nouveau point de terminaison Standard** boîte de dialogue affiche et répertorie les types de point de terminaison standard Enregistrer.  
  
#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a>Affichage et modification d'une configuration de point de terminaison standard  
 Vous pouvez ouvrir une configuration de point de terminaison standard en vue de l'afficher et de la modifier des façons suivantes :  
  
-   Cliquez pour développer le **point de terminaison Standard** nœud et cliquez sur le sous-nœud de point de terminaison respectif.  
  
-   Cliquez sur le **point de terminaison Standard** nœud et cliquez sur le point de terminaison respectif dans le volet de détails.  
  
 Les attributs correspondant au point de terminaison s'affichent dans le volet droit pour modification.  
  
#### <a name="deleting-a-standard-endpoint-configuration"></a>Suppression d'une configuration de point de terminaison standard  
 Vous pouvez supprimer une configuration de point de terminaison standard de l'une des manières suivantes :  
  
-   Cliquez pour développer le **point de terminaison Standard** nœud et avec le bouton droit le sous-nœud de point de terminaison respectif. Utilisez la commande de contexte **supprimer la Configuration de point de terminaison Standard** pour supprimer le point de terminaison.  
  
-   Cliquez sur le **point de terminaison Standard** nœud. Dans le **tâche** volet, cliquez sur **supprimer la Configuration de point de terminaison Standard**.  
  
 Si le point de terminaison standard est en cours d'utilisation, le message d'avertissement suivant apparaît lorsque vous essayez de le supprimer :**Le point de terminaison standard est en cours d'utilisation. Si vous le supprimez maintenant, veillez à supprimer toutes ses références dans d'autres parties de la configuration (par exemple, dans le point de terminaison de service ou le point de terminaison de client). Sinon, la configuration ne sera pas valide et ne pourra pas être ouverte la prochaine fois. Êtes-vous sûr de que vouloir supprimer le point de terminaison standard ? »**  
  
### <a name="binding"></a>Liaison  
 Les configurations de liaison sont utilisées pour configurer des liaisons sur les points de terminaison. Ces paramètres de configuration sont stockés dans le **liaison** nœud. Les points de terminaison référencent les configurations de liaison par nom et plusieurs points de terminaison peuvent référencer une configuration de liaison unique.  
  
 Le **liaisons** nœud affiche tous les paramètres de liaison dans le fichier de configuration. Chaque nœud secondaire dans l’arborescence correspond à un sous-élément dans le <`bindings`> élément dans le fichier de configuration.  
  
 Lorsque vous cliquez sur le **liaisons** nœud, vous pouvez afficher ou exécuter des tâches sur la liaison **Page Résumé** dans les **volet Détail**.  
  
#### <a name="creating-a-new-binding-configuration"></a>Création d’une configuration de liaison  
 Vous pouvez créer une configuration de liaison de l’une des manières suivantes :  
  
-   Cliquez sur le **liaisons** nœud et sélectionnez **nouvelle Configuration de liaison**... Sélectionnez le type de liaison dans la boîte de dialogue, cliquez sur **OK**.  
  
-   Sélectionnez le **liaisons** nœud et cliquez sur **nouvelle Configuration de liaison**... dans le **volet** sur bas à gauche de la fenêtre.  
  
-   Dans la page de résumé cliente ou de service, cliquez sur **cliquez ici pour créer** dans les **Configuration de liaison** champ pour créer une configuration de liaison pour le point de terminaison correspondant.  
  
#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a>Ajout d’extensions d’élément de liaison à une liaison personnalisée  
  
1.  Sélectionnez la liaison à laquelle vous souhaitez ajouter une extension d’élément.  
  
2.  Cliquez sur **Ajouter**.  
  
3.  Dans la liste d’extensions disponibles, sélectionnez l’extension d’élément de liaison que vous souhaitez ajouter. Pour sélectionner plusieurs éléments, appuyez simultanément sur la touche CTRL.  
  
4.  Cliquez sur **Ajouter**.  
  
#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a>Ajustement de la position d’extensions dans une liaison personnalisée  
 Une liaison personnalisée est une collection d'éléments de liaison qui forment une pile. Chaque élément de liaison sur la pile possède ses propres paramètres de configuration. L'ordre des extensions d'élément de liaison dans une liaison personnalisée indique leur position dans la pile. Les éléments en haut de la pile sont appliqués en premier. Pour modifier l'ordre :  
  
1.  Sélectionnez le nœud de liaison personnalisé.  
  
2.  Sélectionnez un élément d’extension de liaison dans le **Position Extension d’élément de liaison** section.  
  
3.  Utilisez le **des** ou **vers le bas** bouton sur le côté gauche de la liste pour modifier la position de l’élément sélectionné.  
  
#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a>Modification de la configuration d’extensions d’élément de liaison dans une liaison personnalisée  
  
1.  Sélectionnez le nœud de liaison dans l'arbre.  
  
2.  Sélectionnez la liaison personnalisée qui contient l'élément que vous souhaitez modifier.  
  
3.  Sélectionnez l'extension d'élément de liaison que vous souhaitez modifier. Les paramètres de l'élément apparaissent dans le volet droit où ils peuvent être modifiés.  
  
### <a name="diagnostics"></a>Diagnostics  
 Le **Diagnostics** nœud affiche tous les paramètres de diagnostic dans le fichier de configuration. Permet d'activer ou de désactiver des compteurs de performances et Windows Management Instrumentation (WMI), de configurer le traçage [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et de configurer l'enregistrement de messages [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Les paramètres dans le **Diagnostics** nœud correspond à la <`system.diagnostics`> section, et `<diagnostics>` section `<system.serviceModel>` dans le fichier de configuration.  
  
 Lorsque vous cliquez sur le **Diagnostics** nœud, vous pouvez afficher ou effectuer des tâches sur les tests de diagnostic **Page Résumé** dans les **volet Détail**.  
  
#### <a name="configuring-performance-counters-and-wmi"></a>Configuration des compteurs de performance et de WMI  
  
1.  Cliquez sur le **Diagnostics** nœud.  
  
2.  Cliquez sur **activer/désactiver les compteurs de Performance**. Le compteur de performance peut avoir trois états : Off (valeur par défaut), ServiceOnly et All. Il est possible de basculer entre les trois états en cliquant sur le lien.  
  
#### <a name="configuring-wmi-provider"></a>Configuration d'un fournisseur WMI  
  
1.  Cliquez sur le **Diagnostics** nœud.  
  
2.  Pour activer le fournisseur WMI, cliquez sur le **activer le fournisseur WMI** lien.  
  
#### <a name="enabling-wcf-tracing"></a>Activation du suivi WCF  
 Vous pouvez créer un fichier de suivi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] avec des propriétés standard ou configurer un fichier de suivi personnalisé.  
  
1.  Cliquez sur le **Diagnostics** nœud.  
  
2.  Cliquez sur **activer le traçage**.  
  
3.  Cliquez sur le **au niveau de Trace** lien pour ajuster le niveau de trace. Six niveaux de suivi sont disponibles : Fermé, Critique, Erreur, Avertissement, Information et Commentaires. Le **le suivi des activités** et **propager l’activité** option Activer vous permet d’utiliser le [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] fonctionnalité de suivi d’activité.  
  
4.  Cliquez sur le nom de l'écouteur de suivi pour spécifier le fichier et les options de suivi.  
  
#### <a name="enabling-wcf-logging"></a>Activation de la journalisation WCF  
 Vous pouvez créer un fichier de suivi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] avec des propriétés standard ou configurer un fichier de suivi personnalisé.  
  
1.  Cliquez sur le **Diagnostics** nœud.  
  
2.  Cliquez sur **activer la journalisation des messages**.  
  
3.  Cliquez sur le **au niveau du journal** lien pour ajuster le niveau de journal. Il existe trois niveaux de journal : Messages malformés, Service et Transport.  
  
4.  Cliquez sur le nom de l'écouteur pour spécifier le fichier journal et les options de suivi.  
  
> [!NOTE]
>  Si vous souhaitez que les journaux de suivi et de message pour être vidé automatiquement lors de la fermeture de votre application, activez la **Effacement automatique** option.  
  
 Le **Diagnostics** **Page Résumé** vous permet d’accomplir les tâches les plus courantes de la configuration de diagnostics. Toutefois, si vous souhaitez modifier les paramètres des écouteurs et des Sources manuellement, vous devez développer la **Diagnostics** nœud et modifier les paramètres dans **Message Logging**, **écouteurs** et **Sources** nœud.  
  
#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a>Activation de la journalisation des messages ou le suivi personnalisé de WCF  
  
1.  Cliquez sur le **Diagnostics** nœud, puis développez-le.  
  
2.  Cliquez sur le **écouteurs** nœud et sélectionnez **nouvel écouteur**.  
  
3.  Tapez le nom de fichier de trace dans le **InitData** champ. Vous pouvez cliquer sur le bouton «... » pour accéder à un chemin d’accès.  
  
4.  En cliquant sur le **TypeName** ligne affiche un bouton «... ». Cliquez sur ce bouton pour ouvrir la **Explorateur de types d’écouteur de Trace**, que vous pouvez utiliser pour rechercher des écouteurs de suivi préconfigurés qui sont déjà installés.  
  
5.  Remarque la **Source** section. Cliquez sur **ajouter** dans cette section pour ouvrir une boîte de dialogue avec un menu déroulant, qui répertorie les sources de suivi disponibles. Sélectionnez une source de suivi, cliquez sur **OK**.  
  
6.  Pour modifier les paramètres de journalisation des messages, cliquez sur le **Message Logging** nœud. Vous pouvez modifier les paramètres dans la grille des propriétés.  
  
### <a name="advanced"></a>Avancé  
  
#### <a name="behaviors"></a>comportements  
 Le **comportements** nœud affiche les comportements qui sont actuellement définies dans le fichier de configuration.  
  
 Les configurations de comportement sont utilisées pour configurer des comportements de points de terminaison et de services. Ces paramètres de configuration sont stockés dans le **avancé** nœud sous **comportements de Service** et **les comportements de point de terminaison**. Les comportements de service sont utilisés par les services, alors que les comportements de point de terminaison par les points de terminaison.  
  
 Les comportements représentent un ensemble d'éléments d'extension qui forment une pile. L'élément en haut de la pile est appliqué en premier. Chaque élément d'extension peut avoir sa propre configuration.  
  
##### <a name="creating-a-new-behavior-configuration"></a>Création d'une configuration de comportement  
 Vous pouvez créer une nouvelle configuration de comportement de l'une des manières suivantes :  
  
-   Cliquez sur un des nœuds de comportement et sélectionnez «**nouvelle Configuration de comportement**  
  
-   Sélectionnez un des nœuds de comportement et cliquez sur le **nouvelle Configuration de comportement**... dans le **volet** sur bas à gauche de la fenêtre.  
  
##### <a name="adding-behavior-element-extensions-to-a-behavior"></a>Ajout d’extensions d’éléments de comportement à un comportement  
  
1.  Sélectionnez l'un des nœuds de comportement.  
  
2.  Sélectionnez le comportement que vous souhaitez modifier.  
  
3.  Cliquez sur **Ajouter**.  
  
4.  Dans la liste d’extensions disponibles, sélectionnez l’extension d’élément de comportement que vous souhaitez ajouter.  
  
5.  Cliquez sur **Ajouter**.  
  
##### <a name="adjusting-the-extension-position-in-a-behavior"></a>Ajustement de la position d’extension dans un comportement  
 Les comportements sont des collections d'élément qui forment une pile. Chaque élément sur la pile possède sa propre configuration. L'ordre des extensions d'éléments de comportement dans un comportement personnalisé indique leur position dans la pile. Les éléments en haut de la pile sont appliqués en premier. Pour modifier l'ordre :  
  
1.  Sélectionnez l'un des nœuds de comportement.  
  
2.  Sélectionnez le comportement que vous souhaitez modifier.  
  
3.  Sélectionnez un élément d’extension de comportement dans les **Position d’Extension de comportement élément** section.  
  
4.  Utilisez le **des** ou **vers le bas** bouton sur le côté gauche de la liste pour modifier la position de l’élément sélectionné.  
  
##### <a name="editing-the-configuration-of-behavior-element-extensions"></a>Modification la configuration des extensions d’élément de comportement  
  
1.  Sélectionnez l'un des nœuds de comportement dans l'arbre.  
  
2.  Sélectionnez le comportement qui contient l'élément que vous souhaitez modifier.  
  
3.  Sélectionnez l'extension d'élément de comportement que vous souhaitez modifier. Les paramètres de l'élément apparaissent dans le volet droit où ils peuvent être modifiés.  
  
#### <a name="protocolmapping"></a>ProtocolMapping  
 Cette section permet de configurer des types de liaison par défaut pour différents protocoles (tels que HTTP, TCP, MSMQ ou net.pipe) en appliquant un mappage défini entre les schémas d'adresse de protocole et les liaisons possibles. Vous pouvez également ajouter de nouveaux mappages à d'autres protocoles.  
  
#### <a name="extensions"></a>Extensions  
 Les nouvelles extensions de liaison, les extensions d'élément de liaison, les extensions de point de terminaison standard et les extensions de comportement peuvent être enregistrées en vue d'être utilisées dans la configuration [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Les extensions sont des paires de nom/type. Le nom définit le nom de l'extension dans la configuration, alors que le type implémente l'extension. Il existe quatre types d'extension :  
  
-   Les extensions de liaison définissent un type de liaison entier. Par exemple : `basicHttpBinding`  
  
-   Les extensions d'élément de liaison définissent un élément d'une liaison. Par exemple : `textMessageEncoding`  
  
-   Les extensions de point de terminaison standard définissent un point de terminaison standard entier. Par exemple : `discoveryEndpoint`  
  
-   Les extensions d'élément de comportement définissent un élément d'un comportement. Par exemple : `clientVia`  
  
 Les extensions inscrites dans la configuration peuvent être utilisées comme tout autre composant [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] du même type.  
  
##### <a name="adding-a-new-extension"></a>Ajout d'une nouvelle extension  
 Sélectionnez l’un des nœuds d’extension parmi les nœuds avancés.  
  
1.  Cliquez sur **Nouveau**.  
  
2.  Entrez un nom et un type.  
  
3.  Cliquez sur **OK**.  
  
4.  L’extension apparaît maintenant dans l’éditeur à l’endroit approprié. Par exemple, si vous ajoutez une extension d'élément de comportement, elle apparaît dans la liste des extensions disponibles.  
  
#### <a name="hosting-environment"></a>Environnement d'hébergement  
 Cette section permet de définir des paramètres d'instanciation pour l'environnement d'hébergement de service.  
  
### <a name="creating-a-configuration-file-using-the-wizard"></a>Création d'un fichier de configuration à l'aide de l'Assistant  
 Pour créer un fichier de configuration, vous pouvez notamment utiliser l'Assistant Nouvel élément de service. L'Assistant recherche les types de service installés et d'autres éléments compatibles avec [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sur l'ordinateur, y compris les répertoires virtuels hébergés sur le Web et les répertoires COM+, et il les charge pour simplifier la création du fichier de configuration.  
  
#### <a name="creating-a-configuration-file"></a>Création d'un fichier de configuration  
  
1.  Démarrez l’éditeur de Configuration de Service à l’aide d’une fenêtre de commande pour accéder à votre [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] emplacement d’installation, puis tapez `SvcConfigEditor.exe`.  
  
2.  À partir de la **fichier** menu, sélectionnez **ouvrir** et cliquez sur **exécutable**, **Service COM +**, ou **WebHosted Service**, selon le type de fichier de configuration que vous souhaitez créer.  
  
3.  Dans le **ouvrir** boîte de dialogue, accédez au fichier spécifique que vous souhaitez créer un fichier de configuration et double-cliquez dessus.  
  
4.  Dans le **fichier** menu, pointez sur **ajouter un nouvel élément** et cliquez sur **Service**. L'Assistant Nouvel élément de service s'ouvre.  
  
5.  Suivez les étapes de création de service dans l'Assistant.  
  
> [!NOTE]
>  Si vous souhaitez utiliser NetPeerTcpBinding inclus dans le fichier de configuration (généré par l'Assistant), vous devez ajouter manuellement un élément de configuration de liaison et modifier l'attribut `mode` de son élément `security` en spécifiant "Aucun."  
  
## <a name="configuring-com"></a>Configuration de COM+  
 L'Éditeur de configuration de service vous permet de créer un fichier de configuration pour une application COM+ existante ou de modifier une configuration COM+ existante. Le **contrat COM** nœud est visible uniquement lorsque le <`comContract`> section existe dans le fichier de configuration.  
  
### <a name="creating-a-new-com-configuration"></a>Création d'une nouvelle configuration COM+  
 Avant de créer une configuration COM+, assurez-vous que votre application COM+ est installée dans les services de composants et enregistrée dans le Global Assembly Cache (GAC).  
  
1.  Sélectionnez **fichier** menu -> **intégrer** -> **l’Application COM +.** Cette opération ferme le fichier actuellement ouvert. Si des données ne sont pas enregistrées dans le fichier actif, une boîte de dialogue d'enregistrement apparaît. Le **Assistant intégration COM +** est ensuite lancée.  
  
2.  Dans la première page, sélectionnez l’application COM+ de l’arbre. Si vous ne trouvez pas votre application COM+ dans l'arbre, vérifiez qu'il est installé dans les services de composants et enregistré dans le Global Assembly Cache (GAC).  
  
3.  Dans la page suivante, sélectionnez les méthodes que vous souhaitez exposer en tant que services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Toutes les méthodes prises en charge dans l'application COM+ sont affichées et sélectionnées par défaut.  
  
4.  Choisissez une méthode d'hébergement.  
  
5.  Configurez d'autres paramètres conformément aux indications de l'Assistant.  
  
6.  L'Éditeur de configuration de service utilise ComSvcConfig.exe en arrière-plan pour générer un fichier de configuration. Une fois terminé, vous pouvez consulter un résumé et quitter l'Assistant. Le fichier de configuration généré est ouvert afin que vous puissiez le modifier directement.  
  
### <a name="editing-an-existing-com-configuration"></a>Modification d'une configuration COM+ existante  
  
1.  Sélectionnez **fichier** menu -> **ouvrir** -> **Service COM +**...  
  
2.  Sélectionnez le service COM+ que vous souhaitez modifier dans la liste.  
  
3.  Modifier les paramètres de configuration dans le **contrats COM** nœud.  
  
    > [!NOTE]
    >  Vous pouvez également ouvrir et modifier directement un fichier de configuration qui contient des contrats COM+.  
  
## <a name="security"></a>Sécurité  
 Le caractère sécurisé des fichiers de configuration de service générés par l'Éditeur de configuration n'est pas garanti. Reportez-vous à la [sécurité](../../../docs/framework/wcf/feature-details/security.md) documentation pour savoir comment sécuriser votre [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services.  
  
 De plus, l'Éditeur de configuration peut être utilisé uniquement pour lire et écrire des éléments de configuration [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] valides. Cet outil ignore les éléments conformes à des schémas, définis par l'utilisateur. Il ne tente pas non plus de supprimez ces éléments du fichier de configuration ou de déterminer leurs effets sur les éléments [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] connus. Il incombe à l'utilisateur de déterminer si ces éléments font peser une menace à l'application ou au système.
