---
title: "Nouveaut&#233;s de Windows Workflow Foundation dans .NET 4.5 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
caps.latest.revision: 32
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 32
---
# Nouveaut&#233;s de Windows Workflow Foundation dans .NET 4.5
[!INCLUDE[wf](../../../includes/wf-md.md)] dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] possède de nombreuses nouvelles fonctionnalités, telles que de nouvelles activités, fonctions du concepteur et modèles de développement de workflow.Nombre des nouvelles fonctionnalités de workflow introduites dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] sont prises en charge dans le concepteur de workflow réhébergé.[!INCLUDE[crabout](../../../includes/crabout-md.md)] les nouvelles fonctionnalités prises en charge, consultez [Prise en charge de nouvelles fonctionnalités Workflow Foundation 4.5 dans le concepteur de workflow réhébergé](../../../docs/framework/windows-workflow-foundation//wf-features-in-the-rehosted-workflow-designer.md).[!INCLUDE[crabout](../../../includes/crabout-md.md)] la migration des applications de workflow .NET 3.0 et .NET 3.5 de façon à utiliser la version la plus récente, consultez [Conseils de migration](../../../docs/framework/windows-workflow-foundation//migration-guidance.md).Cette rubrique fournit une vue d'ensemble des nouvelles fonctionnalités de workflow introduites dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
> [!WARNING]
>  Les nouvelles fonctionnalités [!INCLUDE[wf2](../../../includes/wf2-md.md)] introduites dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ne sont pas disponibles pour les projets qui ciblent les versions antérieures du .NET Framework.Si un projet qui cible [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] est reciblé vers une version antérieure du .NET Framework, plusieurs problèmes peuvent se produire.  
>   
>  -   Les expressions C\# seront remplacées dans le concepteur par le message **Valeur définie en XAML**.  
> -   De nombreuses erreurs de build se produisent, y compris l'erreur suivante.  
>   
>  **Le format de fichier n'est pas compatible avec l'infrastructure objet du ciblage.Pour convertir le format de fichier, enregistrez\-le de manière explicite.Ce message d'erreur disparaîtra une fois que vous aurez enregistré le fichier et rouvert le concepteur.**  
  
##  <a name="BKMK_Versioning"></a> Contrôle de version pour le workflow  
 Le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] présente plusieurs nouvelles fonctionnalités de contrôle de version basées sur la nouvelle classe <xref:System.Activities.WorkflowIdentity>.<xref:System.Activities.WorkflowIdentity> fournit aux auteurs d'applications de workflow un mécanisme pour mapper une instance de workflow persistante avec sa définition.  
  
-   Les développeurs qui utilisent l'hébergement <xref:System.Activities.WorkflowApplication> peuvent utiliser <xref:System.Activities.WorkflowIdentity> pour permettre l'hébergement de plusieurs versions d'un workflow côte à côte.Les instances de workflow persistantes peuvent être chargées à l'aide de la nouvelle classe <xref:System.Activities.WorkflowApplicationInstance>, puis <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> peut être utilisé par l'hôte pour fournir la version appropriée de la définition de workflow en instanciant <xref:System.Activities.WorkflowApplication>.Pour plus d'informations, consultez [Utilisation de WorkflowIdentity et du versioning](../../../docs/framework/windows-workflow-foundation//using-workflowidentity-and-versioning.md) et [Procédure : héberger plusieurs versions d'un workflow côte à côte](../../../docs/framework/windows-workflow-foundation//how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
-   <xref:System.ServiceModel.WorkflowServiceHost> est maintenant un hôte multi\-version.Lorsqu'une nouvelle version d'un service de workflow est déployée, les nouvelles instances sont créées à l'aide du nouveau service, mais les instances existantes s'exécutent à l'aide de la version antérieure.Pour plus d'informations, consultez [Versioning côte à côte dans WorkflowServiceHost](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).  
  
-   Cette rubrique présente la mise à jour dynamique qui fournit un mécanisme pour mettre à jour la définition d'une instance persistante de workflow.Pour plus d'informations, consultez [Mise à jour dynamique](../../../docs/framework/windows-workflow-foundation//dynamic-update.md) et [Procédure : mettre à jour la définition d'une instance de workflow en cours d'exécution](../../../docs/framework/windows-workflow-foundation//how-to-update-the-definition-of-a-running-workflow-instance.md).  
  
-   Le script de base de données SqlWorkflowInstanceStoreSchemaUpgrade.sql est fourni pour mettre à niveau les bases de données de persistance créées à l'aide de scripts de base de données [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].Ce script met à jour les bases de données de persistance [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] pour prendre en charge les nouvelles fonctions de versioning introduites dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].Des valeurs de versioning par défaut sont attribuées à toutes les instances persistantes de workflow dans la base de données et ces instances peuvent ensuite participer côte à côte à l'exécution et à la mise à jour dynamique.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Mise à niveau des bases de données de persistance .NET Framework 4 pour prendre en charge le versioning de workflow](../../../docs/framework/windows-workflow-foundation//using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).  
  
##  <a name="BKMK_NewActivities"></a> Activités  
 La bibliothèque d'activités intégrée contient de nouvelles activités et de nouvelles fonctionnalités pour les activités existantes.  
  
###  <a name="BKMK_NoPersistScope"></a> NoPersistScope  
 <xref:System.Activities.Statements.NoPersistScope> est une nouvelle activité de conteneur qui empêche la persistance d'un workflow lorsque des activités enfants de NoPersistScope sont en cours d'exécution.Cela s'avère utile dans les scénarios où il n'est pas nécessaire que le workflow soit rendu persistant, par exemple lorsque le workflow utilise des ressources propres à l'ordinateur telles que les handles de fichiers, ou pendant les transactions de bases de données.Auparavant, pour empêcher la persistance de se produire pendant l'exécution d'une activité, un <xref:System.Activities.NativeActivity> personnalisé utilisant un utilisait<xref:System.Activities.NoPersistHandle> était nécessaire.  
  
###  <a name="BKMK_NewFlowchartCapabilities"></a> Nouvelles fonctions d'organigramme  
 Les organigrammes sont mis à jour pour le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] et disposent des nouvelles fonctionnalités suivantes :  
  
-   La propriété `DisplayName` d'une activité <xref:System.Activities.Statements.FlowSwitch%601> ou <xref:System.Activities.Statements.FlowDecision> est modifiable.Cela laisse le concepteur d'activités afficher davantage d'informations sur l'objectif de l'activité.  
  
-   Les organigrammes ont une nouvelle propriété appelée <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A> ; la valeur par défaut de cette propriété est `False`.Si cette propriété a la valeur `True`, les nœuds déconnectés d'organigramme génèreront des erreurs de validation.  
  
## Prise en charge de la confiance partielle  
 Les workflows dans [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] nécessitaient un domaine d'application bénéficiant d'un niveau de confiance total.Dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les workflows peuvent s'exécuter dans un environnement de confiance partielle.Dans un environnement de confiance partielle, des composants tiers peuvent être utilisés sans leur octroyer un accès total aux ressources de l'hôte.Les problèmes liés à l'exécution des workflows dans un environnement de confiance partielle sont les suivants :  
  
1.  L'utilisation de composants hérités \(comprenant des règles\) contenus dans l'activité <xref:System.Activities.Statements.Interop> n'est pas prise en charge dans un environnement de confiance partielle.  
  
2.  L'exécution de workflows dans un environnement de confiance partielle dans <xref:System.ServiceModel.WorkflowServiceHost> n'est pas prise en charge.  
  
3.  Les exceptions de persistance dans un scénario de confiance partielle sont une menace potentielle à la sécurité.Pour désactiver la persistance des exceptions, une extension de type <xref:System.Activities.ExceptionPersistenceExtension> doit être ajoutée au projet pour supprimer les exceptions persistantes.L'exemple de code suivant illustre l'implémentation de ce type.  
  
    ```  
    public class ExceptionPersistenceExtension   
    {  
        public ExceptionPersistenceExtension()   
        {   
            this.PersistExceptions = false;   
        }   
        public bool PersistExceptions { get; set; }   
    }  
  
    ```  
  
     Si les exceptions ne doivent pas être sérialisées, assurez\-vous qu'elles sont utilisées dans un <xref:System.Activities.Statements.NoPersistScope>.  
  
4.  Les auteurs d'activités doivent substituer <xref:System.Activities.Activity.CacheMetadata%2A> pour éviter que le runtime du workflow exécute automatiquement la réflexion sur le type.Les arguments et les activités enfants doivent être non\-null, et <xref:System.Activities.ActivityMetadata.Bind%2A> doit être appelé explicitement.Pour plus d'informations sur la substitution de <xref:System.Activities.Activity.CacheMetadata%2A>, consultez [Exposition de données avec CacheMetadata](../../../docs/framework/windows-workflow-foundation//exposing-data-with-cachemetadata.md).De plus, les instances des arguments qui sont de type `internal` ou **privé** doivent être créées explicitement dans <xref:System.Activities.Activity.CacheMetadata%2A> pour éviter d'être créées par réflexion.  
  
5.  Les types n'utilisent pas <xref:System.Runtime.Serialization.ISerializable> ou <xref:System.SerializableAttribute> pour la sérialisation ; les types qui doivent être sérialisés doivent prendre en charge <xref:System.Runtime.DataContractSerializer>.  
  
6.  Les expressions qui utilisent <xref:System.Activities.Expressions.LambdaValue%601> nécessitent <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A> et, par conséquent, ne fonctionnent pas dans un scénario de confiance partielle.Les workflows qui utilisent <xref:System.Activities.Expressions.LambdaValue%601> doivent remplacer les expressions qui ont des activités qui dérivent de <xref:System.Activities.CodeActivity%601>..  
  
7.  Les expressions ne peuvent pas être compilées à l'aide de <xref:System.Activities.XamlIntegration.WorkflowExpressionCompiler> ou du compilateur hébergé Visual Basic, mais les expressions précédemment compilées peuvent être exécutées.  
  
8.  Un seul assembly qui utilise la [transparence de niveau 2](http://aka.ms/Level2Transparency) ne peut pas être utilisé dans [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] dans un environnement de confiance totale, et dans [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] dans un environnement de confiance partielle.  
  
##  <a name="BKMK_NewDesignerCapabilites"></a> Nouvelles fonctions du concepteur  
  
###  <a name="BKMK_DesignerSearch"></a> Recherche du concepteur  
 Pour rendre les plus grands workflows plus pratiques, les workflows peuvent maintenant être trouvés par mot clé.Cette fonctionnalité est disponible uniquement dans [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] ; elle n'est pas disponible dans un concepteur réhébergé.Il existe deux types de recherche disponibles :  
  
-   Recherche rapide, initialisée avec **Ctrl\+F** ou **Édition**, **Rechercher et remplacer**, **Recherche rapide**.  
  
-   Rechercher dans les fichiers, initialisé avec **Ctrl\+Maj\+F** ou **Edition**, **Rechercher et remplacer**, **Rechercher dans les fichiers**.  
  
 Notez que Remplacer n'est pas pris en charge.  
  
####  <a name="BKMK_QuickFind"></a> Recherche rapide  
 Les mots clés trouvés dans les workflows correspondent aux éléments de concepteur suivants :  
  
-   Propriétés des objets <xref:System.Activities.Activity>, des objets <xref:System.Activities.Statements.FlowNode>, des objets <xref:System.Activities.Statements.State>, des objets <xref:System.Activities.Statements.Transition>, et d'autres éléments de contrôle de flux personnalisés.  
  
-   Variables  
  
-   Arguments  
  
-   Expressions  
  
 La recherche rapide est exécutée sur l'arborescence <xref:System.Activities.Presentation.Model.Modelitem> du concepteur.La recherche rapide n'ajoutera pas d'espaces de noms importés dans la définition de workflow.  
  
####  <a name="BKMK_FindInFiles"></a> Rechercher dans les fichiers  
 Les mots clés trouvés dans les workflows correspondent au contenu réel des fichiers de workflow.Les résultats de la recherche sont affichés dans le volet d'affichage des résultats de recherche de Visual Studio.Double\-cliquez sur l'élément de résultat pour accéder à l'activité qui contient la correspondance dans le concepteur de workflow.  
  
###  <a name="BKMK_VariableDeleteContextMenu"></a> Supprimer l'élément de menu contextuel dans le concepteur de variable et d'argument  
 Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], les variables et les arguments ne pouvaient être supprimés dans le concepteur qu'en utilisant le clavier.À partir du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les variables et les arguments peuvent être supprimés à l'aide du menu contextuel.  
  
 La capture d'écran suivante indique le menu contextuel du concepteur de variable et d'argument.  
  
 ![Menu contextuel du concepteur de variable et d'argument](../../../docs/framework/windows-workflow-foundation//media/designercontextmenu.png "DesignerContextMenu")  
  
###  <a name="BKMK_AutoSurround"></a> Encadrement automatique avec séquence  
 Étant donné qu'un workflow ou certaines activités de conteneur \(telles que <xref:System.Activities.Statements.NoPersistScope>\) peuvent uniquement contenir une seule activité de corps, l'ajout d'une deuxième activité exigeait que le développeur supprime la première activité, ajoute une activité <xref:System.Activities.Statements.Sequence>, puis ajoute les deux activités à l'activité de séquence.À partir du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], lors de l'ajout d'une deuxième activité sur l'aire du concepteur, un activité `Sequence` est créée automatiquement pour encapsuler les deux activités.  
  
 La capture d'écran suivante affiche une activité `WriteLine` avec le `Body` d'un `NoPersistScope`.  
  
 ![Emplacement cible de l'encadrement automatique](../../../docs/framework/windows-workflow-foundation//media/autosurround1.png "AutoSurround1")  
  
 La capture d'écran suivante montre l'activité `Sequence` créée automatiquement dans le `Body` lorsqu'un second `WriteLine` est supprimé sous le premier.  
  
 ![Activité Sequence créée automatiquement](../../../docs/framework/windows-workflow-foundation//media/autosurround2.png "AutoSurround2")  
  
###  <a name="BKMK_PanMode"></a> Mode Panoramique  
 Pour naviguer plus facilement dans un grand workflow dans le concepteur, le mode panoramiques peut être activé, ce qui permet au développeur de cliquer sur la partie visible du workflow et de la faire glisser, plutôt que d'utiliser les barres de défilement.Le bouton pour activer le mode panoramiques se trouve dans le coin inférieur droit du concepteur.  
  
 La capture d'écran suivante indique le bouton de panoramique qui se trouve dans le coin inférieur droit du concepteur de workflow.  
  
 ![Bouton panoramique dans le Concepteur de flux de travail](../../../docs/framework/windows-workflow-foundation//media/panbutton.png "PanButton")  
  
 Le bouton central de la souris ou la barre d'espace peut également être utilisé pour appliquer un panoramique au concepteur de workflow.  
  
###  <a name="BKMK_MultiSelect"></a> Multisélection  
 Plusieurs activités peuvent être sélectionnées en même temps, en faisant glisser un rectangle autour d'elles \(lorsque le mode panoramique n'est pas activé\), ou en maintenant la touche Ctrl enfoncée et en cliquant sur les activités souhaitées une à une.  
  
 Il est également possible de glisser\-déplacer plusieurs activités sélectionnées et de les utiliser dans une interaction à l'aide du menu contextuel.  
  
###  <a name="BKMK_DocumentOutline"></a> Mode Plan des éléments de workflow  
 Afin de simplifier la navigation dans les workflows hiérarchiques, les composants d'un workflow s'affichent dans un mode Plan de style arborescent.Le mode Plan est affiché dans la vue **Structure du document**.Pour ouvrir cette vue dans le menu principal, sélectionnez **Affichage**, **Autres fenêtres**, **Structure du document**, ou appuyez sur Ctrl W,U.Cliquer sur un nœud en mode Plan permet d'accéder à l'activité correspondante dans le Concepteur de workflow, et le mode Plan est mis à jour pour afficher les activités qui sont sélectionnées dans le concepteur.  
  
 La capture d'écran suivante du workflow terminé du [Didacticiel de mise en route](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md) montre le mode Plan avec un workflow séquentiel.  
  
 ![Mode Plan dans le concepteur de flux de travail](../../../docs/framework/windows-workflow-foundation//media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")  
  
###  <a name="BKMK_CSharpExpressions"></a> Expressions C\#  
 Avant le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], toutes les expressions de workflow ne pouvaient être écrites que dans Visual Basic.Dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les expressions Visual Basic sont uniquement utilisées pour les projets créés à l'aide de Visual Basic.Les projets Visual C\# utilisent C\# pour les expressions.Un éditeur d'expressions C\# fonctionnel est fourni, qui a des fonctions telles que la mise en surbrillance de la grammaire et IntelliSense.Les projets de workflow C\# créés dans les versions antérieures qui utilisent des expressions Visual Basic continueront à fonctionner.  
  
 Les expressions C\# sont validées au moment de la conception.Les erreurs dans les expressions C\# sont marquées avec un soulignement ondulé rouge.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] les expressions C\#, consultez [Expressions C\#](../../../docs/framework/windows-workflow-foundation//csharp-expressions.md).  
  
###  <a name="BKMK_Visibility"></a> Meilleur contrôle de la visibilité des éléments d'en\-tête et de la barre de shell  
 Dans un concepteur réhébergé, certains des contrôles d'interface utilisateur standard peuvent ne pas avoir de signification pour un workflow donné, et peuvent être désactivés.Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], cette personnalisation est prise en charge uniquement par la barre de shell en bas du concepteur.Dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], la visibilité des éléments d'en\-tête de shell en haut du concepteur peut être ajustée en affectant à <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> la valeur <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> appropriée.  
  
###  <a name="BKMK_AutoConnect"></a> Connexion automatique et insertion automatique dans les workflows Organigramme et Machine à états  
 Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], les connexions entre les nœuds d'un workflow Organigramme devaient être ajoutées manuellement.Dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les nœuds Organigramme et Machine à états ont des points de connexion automatique qui sont visibles lorsqu'une activité est déplacée de la boîte à outils vers l'aire du concepteur.Le dépôt d'une activité sur un de ces points ajoute automatiquement l'activité avec la connexion nécessaire.  
  
 La capture d'écran suivante montre les points d'attachement qui sont visibles lorsqu'une activité est déplacée depuis la boîte à outils.  
  
 ![Nœud de départ de l'organigramme montrant des points de connexion automatique](../../../docs/framework/windows-workflow-foundation//media/autoconnect1.png "Autoconnect1")  
  
 Les activités peuvent également être déplacées sur les connexions entre des nœuds d'organigramme et des états de façon à insérer automatiquement le nœud entre deux autres nœuds.La capture d'écran suivante montre la ligne de connexion en surbrillance où les activités peuvent être glissées\-déplacées depuis la boîte à outils.  
  
 ![Poignée d'insertion automatique pour déposer les activités](../../../docs/framework/windows-workflow-foundation//media/autoinsert.png "Autoinsert")  
  
###  <a name="BKMK_Annotations"></a> Annotations du concepteur  
 Pour faciliter le développement de plus grands workflows, le concepteur prend désormais en charge l'ajout d'annotations pour faciliter le suivi du processus de création.Une annotation peut être ajoutée aux activités, états, nœuds d'organigramme, variables et arguments.La capture d'écran suivante montre le menu contextuel utilisé pour ajouter des annotations au concepteur.  
  
 ![Menu contextuel des annotations](../../../docs/framework/windows-workflow-foundation//media/annotationdialog.png "annotationdialog")  
  
### États de débogage  
 Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], les éléments autres que des activités ne prennent pas en charge les points d'arrêt du débogage étant donné qu'ils n'étaient pas des unités d'exécution.Cette version fournit un mécanisme pour ajouter des points d'arrêt aux objets <xref:System.Activities.Statements.State>.Lorsqu'un point d'arrêt est défini sur un <xref:System.Activities.Statements.State>, l'exécution s'arrête lorsque l'état subit une transition, avant que ses activités d'entrée ou déclencheurs ne soient planifiés.  
  
###  <a name="BKMK_ActivityDelegates"></a> Définir et consommer des objets ActivityDelegate dans le concepteur  
 Les activités dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] utilisaient des objets <xref:System.Activities.ActivityDelegate> pour exposer des points d'exécution où d'autres parties du workflow peuvent interagir avec l'exécution d'un workflow, mais l'utilisation de ces points d'exécution nécessite généralement du code.Dans cette version finale, les développeurs peuvent définir et utiliser des délégués d'activité à l'aide du concepteur de workflow.Pour plus d'informations, consultez [Procédure : définir et utiliser des délégués d'activité dans le Concepteur de flux de travail](../Topic/How%20to:%20Define%20and%20consume%20activity%20delegates%20in%20the%20Workflow%20Designer.md).  
  
###  <a name="BKMK_BuildTimeValidation"></a> Validation au moment de la génération  
 Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], les erreurs de validation de workflow n'étaient pas été comptées comme des erreurs de build pendant la génération d'un projet de workflow.Cela signifiait que la génération d'un projet de workflow pouvait réussir même lorsqu'il existait des erreurs de validation de workflow.Dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], des erreurs de validation de workflow provoquent l'échec de la génération.  
  
###  <a name="BKMK_DesignTimeValidation"></a> Validation d'arrière\-plan au moment du design  
 Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], les workflows étaient validés en tant que processus de premier plan, ce qui pouvait éventuellement bloquer l'interface utilisateur pendant les processus de validation complexes ou longs.La validation de workflow a lieu à présent sur un thread d'arrière\-plan, afin que l'interface utilisateur ne soit pas bloquée.  
  
###  <a name="BKMK_ViewState"></a> État d'affichage dans un emplacement distinct des fichiers XAML  
 Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], les informations d'état d'affichage pour un workflow sont stockées dans le fichier XAML en différents emplacements.Cela n'est pas pratique pour les développeurs qui souhaitent lire le XAML directement, ou écrire du code pour supprimer les informations d'état d'affichage.Dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les informations d'état d'affichage dans le fichier XAML sont sérialisées en tant qu'élément distinct dans le fichier XAML. Les développeurs peuvent facilement rechercher et modifier des informations d'état d'affichage d'une activité, ou supprimer complètement l'état d'affichage.  
  
###  <a name="BKMK_ExpressionExtensibility"></a> Extensibilité des expressions  
 Dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], nous fournissons une méthode permettant aux développeurs de créer leur propre expression et expérience de création d'expression qui peut être intégrée au concepteur de workflow.  
  
###  <a name="BKMK_BackwardCompatRehostedDesigner"></a> Opter pour les fonctionnalités de workflow 4.5 dans le concepteur réhébergé  
 Pour conserver la compatibilité descendante, certaines nouvelles fonctionnalités incluses dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ne sont pas activées par défaut dans le concepteur réhébergé.Il s'agit de garantir que les applications existantes qui utilisent le concepteur réhébergé ne sont pas interrompues par la mise à jour vers la version la plus récente.Pour activer les nouvelles fonctionnalités du concepteur réhébergé, affectez à <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> la valeur « .NET Framework 4.5 », ou définissez des membres de <xref:System.Activities.Presentation.DesignerConfigurationService> pour activer des fonctionnalités.  
  
##  <a name="BKMK_NewWFModels"></a> Nouveaux modèles de développement de workflow  
 Outre les modèles de développement d'organigramme et workflow séquentiel, cette version inclut des workflows Machine à états, et les services de workflow Contrat en premier.  
  
###  <a name="BKMK_StateMachine"></a> Workflows de machine à états  
 Les workflows de machine à états ont été introduits dans le cadre du .NET Framework 4, version 4.0.1 dans [Microsoft .NET Framework 4 Platform Update 1](http://go.microsoft.com/fwlink/?LinkID=215092).Cette mise à jour inclut plusieurs nouvelles classes et activités qui permettent aux développeurs de créer des workflow de machine à états.Ces classes et activités ont été mises à jour pour le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].Les mises à jour comprennent :  
  
1.  Possibilité de définir des points d'arrêt sur des états  
  
2.  Possibilité de copier et coller des transitions dans le concepteur de workflow  
  
3.  Prise en charge du concepteur pour la création de transition de déclencheur partagée  
  
4.  Les activités utilisées pour créer des workflows Machine à états, notamment : <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State> et <xref:System.Activities.Statements.Transition>  
  
 La capture d'écran suivante affiche le workflow de machine à états terminé de l'étape [Procédure : créer un workflow d'ordinateur d'état](../../../docs/framework/windows-workflow-foundation//how-to-create-a-state-machine-workflow.md) du [Didacticiel de mise en route](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md) .  
  
 ![Flux de travail de l'ordinateur d'état terminé](../../../docs/framework/windows-workflow-foundation//media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Pour plus d'informations sur la création de workflows Machine à états, consultez [Workflows d'ordinateur d'état](../../../docs/framework/windows-workflow-foundation//state-machine-workflows.md).  
  
###  <a name="BKMK_ContractFirst"></a> Développement de workflow « contrat en premier »  
 L'outil de développement Contrat en premier permet au développeur de concevoir un contrat dans le code en premier, puis, en quelques clics dans [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], de générer automatiquement un modèle d'activité dans la boîte à outils représentant chaque opération.Ces activités sont ensuite utilisées pour créer un workflow qui implémente les opérations définies par le contrat.Le concepteur de workflow validera le service de workflow pour garantir que ces opérations sont implémentées et que la signature du workflow correspond à la signature du contrat.Le développeur peut également associer un service de workflow à une collection de contrats implémentés.Pour plus d'informations sur le développement de service de workflow Contrat en premier, consultez [Procédure : créer un service de workflow qui utilise un contrat de service existant](../../../docs/framework/windows-workflow-foundation//how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).