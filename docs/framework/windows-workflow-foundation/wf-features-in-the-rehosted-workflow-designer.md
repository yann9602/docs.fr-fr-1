---
title: "Prise en charge de nouvelles fonctionnalités Workflow Foundation 4.5 dans le concepteur de workflow réhébergé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 346dc5f06fd5f655426d8f41164a9a2f24acdb5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a>Prise en charge de nouvelles fonctionnalités Workflow Foundation 4.5 dans le concepteur de workflow réhébergé
[!INCLUDE[wf](../../../includes/wf-md.md)] dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a introduit plusieurs nouvelles fonctionnalités, notamment plusieurs améliorations à l'utilisation de Workflow Designer. Cette rubrique détaille lesquelles de ces fonctionnalités sont prises en charge dans le concepteur réhébergé, et celles qui ne sont pas actuellement prises en charge.  
  
> [!NOTE]
>  Pour obtenir la liste de tous les nouveaux [!INCLUDE[wf](../../../includes/wf-md.md)] fonctionnalités introduites dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], y compris celles qui ne sont pas liées au réhébergement du concepteur, consultez [quelles sont les nouveautés de Windows Workflow Foundation dans .NET 4.5](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).  
  
## <a name="activities"></a>Activités  
 La bibliothèque d'activités intégrée contient de nouvelles activités et de nouvelles fonctionnalités pour les activités existantes. Toutes ces nouvelles activités sont prises en charge dans le concepteur réhébergé. Pour plus d’informations sur ces nouvelles activités, consultez le [activités](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_NewActivities) section de [quelles sont les nouveautés de Windows Workflow Foundation dans .NET 4.5](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).  
  
## <a name="c-expressions"></a>Expressions C#  
 Avant le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], toutes les expressions de workflow ne pouvaient être écrites que dans Visual Basic. Dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les expressions Visual Basic sont uniquement utilisées pour les projets créés à l'aide de Visual Basic. Les projets Visual C# utilisent C# pour les expressions. Lors de la création de workflow dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], un éditeur d'expressions C# fonctionnel est fourni, qui a des fonctions telles que la mise en surbrillance de la grammaire et IntelliSense. Les projets de workflow C# créés dans les versions antérieures qui utilisent des expressions Visual Basic continueront à fonctionner.  
  
> [!WARNING]
>  Les expressions C# ne sont pas prises en charge dans le concepteur réhébergé.  
  
## <a name="new-designer-capabilities"></a>Nouvelles fonctions du concepteur  
  
### <a name="designer-search"></a>Recherche du concepteur  
 Le [recherche rapide](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) et [rechercher dans les fichiers](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) fonctionnalités introduites avec [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ne sont pas pris en charge dans le concepteur réhébergé. La recherche `Toolbox` est prise en charge dans le concepteur réhébergé. Pour plus d’informations sur ces fonctionnalités, consultez [recherche du concepteur](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch).  
  
> [!WARNING]
>  [Recherche rapide](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) et [rechercher dans les fichiers](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) ne sont pas pris en charge dans le concepteur réhébergé.  
  
### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a>Supprimer l’élément de menu contextuel dans le concepteur de variable et d’argument  
 Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], les variables et les arguments ne pouvaient être supprimés dans le concepteur qu'en utilisant le clavier. À partir du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les variables et les arguments peuvent être supprimés à l'aide du menu contextuel. Cette fonctionnalité est prise en charge dans le concepteur réhébergé.  
  
 La capture d’écran suivante indique le menu contextuel du concepteur de variable et d’argument.  
  
 ![Variable et le Menu contextuel du Concepteur de Argument](../../../docs/framework/windows-workflow-foundation/media/designercontextmenu.png "DesignerContextMenu")  
  
### <a name="auto-surround-with-sequence"></a>Encadrement automatique avec séquence  
 Étant donné qu'un workflow ou certaines activités de conteneur (telles que <xref:System.Activities.Statements.NoPersistScope>) peuvent uniquement contenir une seule activité de corps, l'ajout d'une deuxième activité exigeait que le développeur supprime la première activité, ajoute une activité <xref:System.Activities.Statements.Sequence>, puis ajoute les deux activités à l'activité de séquence. À partir du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], lors de l'ajout d'une deuxième activité sur l'aire du concepteur, un activité `Sequence` est créée automatiquement pour encapsuler les deux activités. Cette fonctionnalité est prise en charge dans le concepteur réhébergé.  
  
 La capture d'écran suivante affiche une activité `WriteLine` avec le `Body` d'un `NoPersistScope`.  
  
 ![Auto &#45; emplacement de dépôt de surround](../../../docs/framework/windows-workflow-foundation/media/autosurround1.png "AutoSurround1")  
  
 La capture d'écran suivante montre l'activité `Sequence` créée automatiquement dans le `Body` lorsqu'un second `WriteLine` est supprimé sous le premier.  
  
 ![Activité sequence créée automatiquement](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
### <a name="pan-mode"></a>Mode Panoramique  
 Pour naviguer plus facilement dans un grand workflow dans le concepteur, le mode panoramiques peut être activé, ce qui permet au développeur de cliquer sur la partie visible du workflow et de la faire glisser, plutôt que d'utiliser les barres de défilement. Le bouton pour activer le mode panoramiques se trouve dans le coin inférieur droit du concepteur. Cette fonctionnalité est prise en charge dans le concepteur réhébergé.  
  
 La capture d'écran suivante indique le bouton de panoramique qui se trouve dans le coin inférieur droit du concepteur de workflow.  
  
 ![Bouton panoramique dans le Concepteur de workflow](../../../docs/framework/windows-workflow-foundation/media/panbutton.png "PanButton")  
  
 Le bouton central de la souris ou la barre d'espace peut également être utilisé pour appliquer un panoramique au concepteur de workflow.  
  
### <a name="multi-select"></a>Multisélection  
 Plusieurs activités peuvent être sélectionnées en même temps, en faisant glisser un rectangle autour d'elles (lorsque le mode panoramique n'est pas activé), ou en maintenant la touche Ctrl enfoncée et en cliquant sur les activités souhaitées une à une. Cette fonctionnalité est prise en charge dans le concepteur réhébergé.  
  
 Il est également possible de glisser-déplacer plusieurs activités sélectionnées et de les utiliser dans une interaction à l'aide du menu contextuel.  
  
### <a name="outline-view-of-workflow-items"></a>Mode Plan des éléments de workflow  
 Afin de simplifier la navigation dans les workflows hiérarchiques, les composants d’un workflow s’affichent dans un mode Plan de style arborescent. Le mode plan est affiché dans le **structure du Document** vue. Pour ouvrir cette vue dans [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], dans le menu principal, sélectionnez **vue**, **autres fenêtres**, **structure du Document**, ou appuyez sur Ctrl W, U. Cliquer sur un nœud en mode Plan permet d'accéder à l'activité correspondante dans le Concepteur de workflow, et le mode Plan est mis à jour pour afficher les activités qui sont sélectionnées dans le concepteur. Cette fonctionnalité est prise en charge dans le concepteur réhébergé.  
  
 La capture d’écran suivante du flux de travail terminé à partir de la [Getting Started Tutorial](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) montre le mode plan avec un flux de travail séquentiel.  
  
 ![Mode d’affichage dans le Concepteur de flux de travail plan](../../../docs/framework/windows-workflow-foundation/media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")  
  
### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a>Meilleur contrôle de la visibilité des éléments d'en-tête et de la barre de shell  
 Dans un concepteur réhébergé, certains des contrôles d'interface utilisateur standard peuvent ne pas avoir de signification pour un workflow donné, et peuvent être désactivés. Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], cette personnalisation est prise en charge uniquement par la barre de shell en bas du concepteur. Dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], la visibilité des éléments d'en-tête de shell en haut du concepteur peut être ajustée en affectant à <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> la valeur <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> appropriée.  
  
### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a>Connexion automatique et insertion automatique dans les workflows Organigramme et Machine à états  
 Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], les connexions entre les nœuds d'un workflow Organigramme devaient être ajoutées manuellement. Dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les nœuds Organigramme et Machine à états ont des points de connexion automatique qui sont visibles lorsqu'une activité est déplacée de la boîte à outils vers l'aire du concepteur. Le dépôt d'une activité sur un de ces points ajoute automatiquement l'activité avec la connexion nécessaire.  
  
 La capture d'écran suivante montre les points d'attachement qui sont visibles lorsqu'une activité est déplacée depuis la boîte à outils.  
  
 ![Nœud de démarrage d’organigramme montrant des points](../../../docs/framework/windows-workflow-foundation/media/autoconnect1.png "Autoconnect1")  
  
 Les activités peuvent également être déplacées sur les connexions entre des nœuds d'organigramme et des états de façon à insérer automatiquement le nœud entre deux autres nœuds. La capture d’écran suivante montre la ligne de connexion en surbrillance où les activités peuvent être glissées-déposées depuis la boîte à outils.  
  
 ![Auto &#45; l’instruction insert gérer pour déposer les activités](../../../docs/framework/windows-workflow-foundation/media/autoinsert.png "Autoinsert")  
  
 Connexion automatique et insertion automatique sont prises en charge dans le concepteur réhébergé.  
  
### <a name="designer-annotations"></a>Annotations du concepteur  
 Pour faciliter le développement de plus grands workflows, le concepteur prend désormais en charge l'ajout d'annotations pour faciliter le suivi du processus de création. Une annotation peut être ajoutée aux activités, états, nœuds d'organigramme, variables et arguments. La capture d'écran suivante montre le menu contextuel utilisé pour ajouter des annotations au concepteur.  
  
 ![Menu contextuel des annotations](../../../docs/framework/windows-workflow-foundation/media/annotationdialog.png "annotationdialog")  
  
 Les annotations du concepteur sont prises en charge dans le concepteur réhébergé.  
  
### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a>Définir et consommer des objets ActivityDelegate dans le concepteur  
 Les activités dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] utilisaient des objets <xref:System.Activities.ActivityDelegate> pour exposer des points d'exécution où d'autres parties du workflow peuvent interagir avec l'exécution d'un workflow, mais l'utilisation de ces points d'exécution nécessite généralement du code. Dans cette mise en production, les développeurs peuvent définir et utiliser des délégués d’activité à l’aide du concepteur de workflow. Pour plus d’informations, consultez [Comment : définir et utiliser des délégués d’activité dans le Concepteur de flux de travail](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).  
  
 Les délégués d'activité sont pris en charge dans le concepteur réhébergé.  
  
### <a name="build-time-validation"></a>Validation au moment de la génération  
 Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], les erreurs de validation de workflow n'étaient pas été comptées comme des erreurs de build pendant la génération d'un projet de workflow. Cela signifiait que la génération d'un projet de workflow pouvait réussir même lorsqu'il existait des erreurs de validation de workflow. Dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], des erreurs de validation de workflow provoquent l'échec de la génération.  
  
> [!WARNING]
>  La validation au moment de la génération n'est pas prise en charge dans le concepteur réhébergé.  
  
### <a name="design-time-background-validation"></a>Validation d'arrière-plan au moment du design  
 Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], les workflows étaient validés en tant que processus de premier plan, ce qui pouvait éventuellement bloquer l'interface utilisateur pendant les processus de validation complexes ou longs. La validation de workflow a lieu à présent sur un thread d'arrière-plan, afin que l'interface utilisateur ne soit pas bloquée.  
  
 La validation de l'arrière-plan au moment de la génération est prise en charge dans le concepteur réhébergé.  
  
### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a>État d'affichage dans un emplacement distinct des fichiers XAML  
 Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], les informations d'état d'affichage pour un workflow sont stockées dans le fichier XAML en différents emplacements. Cela n'est pas pratique pour les développeurs qui souhaitent lire le XAML directement, ou écrire du code pour supprimer les informations d'état d'affichage. Dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les informations d’état de vue dans le fichier XAML sont sérialisées comme un élément distinct dans le fichier XAML.  Les développeurs peuvent facilement localiser et modifier les informations de l’état d’affichage d’une activité ou supprimer complètement de l’état d’affichage.  
  
 Cette fonctionnalité est prise en charge dans le concepteur de workflow réhébergé.  
  
### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a>Opter pour les fonctionnalités de workflow 4.5 dans le concepteur réhébergé  
 Pour conserver la compatibilité descendante, certaines nouvelles fonctionnalités incluses dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ne sont pas activées par défaut dans le concepteur réhébergé. Il s'agit de garantir que les applications existantes qui utilisent le concepteur réhébergé ne sont pas interrompues par la mise à jour vers la version la plus récente. Pour activer les nouvelles fonctionnalités du concepteur réhébergé, affectez à <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> la valeur « .Net Framework 4.5 », ou définissez des membres de <xref:System.Activities.Presentation.DesignerConfigurationService> pour activer des fonctionnalités.  
  
## <a name="new-workflow-development-models"></a>Nouveaux modèles de développement de workflow  
 Outre les modèles de développement d'organigramme et workflow séquentiel, cette version inclut des workflows Machine à états, et les services de workflow Contrat en premier.  
  
### <a name="state-machine-workflows"></a>Workflows de machine à états  
 Flux de travail de machine à états ont été introduites dans le cadre du .NET Framework 4.0.1 dans le [Microsoft .NET Framework 4 Platform Update 1](http://go.microsoft.com/fwlink/?LinkID=215092). Cette mise à jour inclut plusieurs nouvelles classes et activités qui permettent aux développeurs de créer des workflow de machine à états. Ces classes et activités ont été mises à jour pour le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Les mises à jour comprennent :  
  
1.  Possibilité de définir des points d'arrêt sur des états  
  
2.  Possibilité de copier et coller des transitions dans le concepteur de workflow  
  
3.  Prise en charge du concepteur pour la création de transition de déclencheur partagée  
  
4.  Les activités utilisées pour créer des workflows Machine à états, notamment : <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State> et <xref:System.Activities.Statements.Transition>  
  
 La capture d’écran suivante montre le workflow de machine d’état terminé à partir du [Getting Started Tutorial](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) étape [Comment : créer un Workflow de Machine d’état](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md).  
  
 ![Flux de travail de Machine d’état terminé](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Pour plus d’informations sur la création de workflows d’ordinateur d’état, consultez [Workflows d’ordinateur d’état](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md). Les workflow de machine à états sont pris en charge dans le concepteur réhébergé.  
  
### <a name="contract-first-workflow-development"></a>Développement de workflow « contrat en premier »  
 L'outil de développement Contrat en premier permet au développeur de concevoir un contrat dans le code en premier, puis, en quelques clics dans [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], de générer automatiquement un modèle d'activité dans la boîte à outils représentant chaque opération. Ces activités sont ensuite utilisées pour créer un workflow qui implémente les opérations définies par le contrat. Le concepteur de workflow validera le service de workflow pour garantir que ces opérations sont implémentées et que la signature du workflow correspond à la signature du contrat. Le développeur peut également associer un service de workflow à une collection de contrats implémentés. Pour plus d’informations sur le développement de service de workflow contrat en premier, consultez [Comment : créer un service de flux de travail qui consomme un contrat de service existant](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
> [!WARNING]
>  Le développement de workflow « contrat en premier » n'est pas pris en charge dans Workflow Designer.
