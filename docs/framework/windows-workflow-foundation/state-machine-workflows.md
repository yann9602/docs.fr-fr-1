---
title: "Workflows d&#39;ordinateur d&#39;&#233;tat | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# Workflows d&#39;ordinateur d&#39;&#233;tat
Une machine à états représente un paradigme connu pour développer des programmes.L'activité <xref:System.Activities.Statements.StateMachine>, avec <xref:System.Activities.Statements.State>, <xref:System.Activities.Statements.Transition>, et d'autres activités peut être utilisée pour générer des programmes de workflow de machine à états.Cette rubrique fournit une vue d'ensemble de la création des workflows de machine à états.  
  
## Présentation du workflow de machine à états  
 Les workflows de machine à états fournissent un style de modélisation avec lequel vous pouvez modéliser votre workflow de façon pilotée par événements.Une activité <xref:System.Activities.Statements.StateMachine> contient les états et les transitions qui composent la logique de la machine à états, et peut être utilisée partout où une activité peut être utilisée.Il existe plusieurs classes dans le runtime de machine à états :  
  
-   <xref:System.Activities.Statements.StateMachine>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
 Pour créer un workflow de machine à états, les états sont ajoutés à une activité <xref:System.Activities.Statements.StateMachine>, et les transitions sont utilisées pour contrôler le flux entre les états.La capture d'écran suivant, de l'étape [Procédure : créer un workflow d'ordinateur d'état](../../../docs/framework/windows-workflow-foundation//how-to-create-a-state-machine-workflow.md) du [Didacticiel de mise en route](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md), affiche un workflow de machine à états avec trois états et trois transitions.**Initialize Target** est l'état initial et représente le premier état dans le workflow.Cela est indiqué par la ligne qui le provoque à partir du nœud **Début**.L'état final dans le workflow est nommé **FinalState**, et représente le point auquel le workflow se termine.  
  
 ![Flux de travail de l'ordinateur d'état terminé](../../../docs/framework/windows-workflow-foundation//media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Un workflow de machine à états ne doit avoir qu'un seul état initial, et au moins un état final.Chaque état qui n'est pas un état final doit avoir au moins une transition.Les sections suivantes décrivent la création et la configuration des états et des transitions.  
  
## Création et configuration d'états  
 Un <xref:System.Activities.Statements.State> représente un état dans lequel une machine à états peut être.Pour ajouter un état <xref:System.Activities.Statements.State> à un workflow, faites glisser le concepteur d'activités **State** de la section **Machine à états** de la **Boîte à outils** et déposez\-le sur une activité <xref:System.Activities.Statements.StateMachine> sur l'aire [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].  
  
 ![Activités de la machine à états WF4](../../../docs/framework/windows-workflow-foundation//media/netframework4platformupdate1statemachineactivities.jpg "NETFramework4PlatformUpdate1StateMachineActivities")  
  
 Pour configurer un état comme **État initial**, cliquez avec le bouton droit sur l'état et sélectionnez **Définir en tant qu'état initial**.En outre, s'il n'y a pas d'état initial actuel, l'état initial peut être désigné en faisant glisser une ligne du nœud **Début** en haut du workflow vers l'état souhaité.Lorsqu'une activité <xref:System.Activities.Statements.StateMachine> est déposée dans le concepteur de workflow, elle est préconfigurée avec un premier état nommé **State1**.Un workflow de machine à états ne doit avoir qu'un seul état initial.  
  
 Un état qui représente un état d'arrêt dans une machine à états est appelé un état final.Un état final est un état dont la propriété <xref:System.Activities.Statements.State.IsFinal%2A> a la valeur `true`, n'a aucune activité <xref:System.Activities.Statements.State.Exit%2A>, et aucune transition provenant de cette dernière.Pour ajouter un état final dans un workflow, faites glisser un concepteur d'activités **FinalState** de la section **Machine à états** de la **Boîte à outils** et déposez\-le sur une activité <xref:System.Activities.Statements.StateMachine> sur l'aire [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].Un workflow de machine à états doit avoir au moins un état final.  
  
### Configurer les actions d'entrée et de sortie  
 Un état peut avoir une propriété <xref:System.Activities.Statements.State.Entry%2A> et une action <xref:System.Activities.Statements.State.Exit%2A> .\(Un état configuré comme état final ne peut avoir qu'une action d'entrée.\)Lorsqu'une instance du workflow entre dans un état, toutes les activités de l'action d'entrée s'exécutent.Lorsque l'action d'entrée est terminée, les déclencheurs pour les transitions de l'état sont planifiés.Lorsqu'une transition vers un autre état est validée, les activités de l'action de sortie sont exécutées, même si l'état revient au même état.Une fois que l'action de sortie est terminée, les activités dans l'action de transition s'exécutent, et le nouvel état est passé, puis ses actions d'entrée sont planifiées.  
  
> [!NOTE]
>  Lors du débogage d'un workflow de machine à états, les points d'arrêt peuvent être placés sur l'activité de machine à états racine et les états dans le workflow de machine à états.Les points d'arrêt ne peuvent être placés directement sur les transitions, mais ils peuvent être placés sur toutes les activités contenues dans les états et les transitions.  
  
## Création et configuration de transitions  
 Tous les états doivent avoir au moins une transition, à l'exception d'un état final qui peut n'avoir aucune transitions.Des transitions peuvent être ajoutées après ajout d'un état à un workflow de machine à états, ou elles peuvent être créées à mesure que l'état est déposé.  
  
 Pour ajouter un <xref:System.Activities.Statements.State> et créer une transition en une seule étape, faites glisser une activité **State** de la section **Machine à états** de la **Boîte à outils** et placez\-la sur un autre état dans le concepteur de workflow.Lorsque le <xref:System.Activities.Statements.State> est déplacé vers un autre <xref:System.Activities.Statements.State>, quatre triangles apparaissent autour de l'autre <xref:System.Activities.Statements.State>.Si <xref:System.Activities.Statements.State> est déposé sur un des quatre triangles, il est ajouté à la machine à états et une transition est créée à partir du <xref:System.Activities.Statements.State> source vers le <xref:System.Activities.Statements.State> de destination de dépôt.Pour plus d'informations, consultez [Concepteur d'activités de transition](../Topic/Transition%20Activity%20Designer.md).  
  
 Pour créer une transition après ajout d'un état, il existe deux options.La première option consiste à faire glisser l'état depuis l'aire du concepteur de workflow et à le placer sur un état existant, puis à le déposer sur l'un des points de dépôt.Elle est très similaire à la méthode décrite dans la section précédente.Vous pouvez également pointer la souris sur l'état source souhaité, et faire glisser une ligne vers l'état de destination souhaité.  
  
> [!NOTE]
>  Un seul état dans une machine à états peut contenir jusqu'à 76 transitions créées à l'aide du concepteur de workflow.Le nombre maximal de transitions d'un état pour les workflows créés en dehors du concepteur est limité uniquement par les ressources système.  
  
 Une transition peut avoir un <xref:System.Activities.Statements.Transition.Trigger%2A>, un <xref:System.Activities.Statements.Transition.Condition%2A> et un <xref:System.Activities.Statements.Transition.Action%2A>.Le <xref:System.Activities.Statements.Transition.Trigger%2A> d'une transition est planifié lorsque l'action <xref:System.Activities.Statements.State.Entry%2A> de l'état source de la transition est terminée.En général, <xref:System.Activities.Statements.Transition.Trigger%2A> est une activité qui attend qu'un type d'événement se produise, mais il peut s'agir de n'importe quelle activité, ou d'aucune activité.Une fois que l'activité <xref:System.Activities.Statements.Transition.Trigger%2A> est terminée, <xref:System.Activities.Statements.Transition.Condition%2A>, le cas échéant, est évalué.S'il n'existe aucune activité <xref:System.Activities.Statements.Transition.Trigger%2A>, <xref:System.Activities.Statements.Transition.Condition%2A> est évalué immédiatement.Si la condition a la valeur `false`, la transition est annulée, et l'activité <xref:System.Activities.Statements.Transition.Trigger%2A> de toutes les transitions de l'état est replanifiée.S'il existe d'autres transitions qui partagent le même état source que la transition actuelle, ces actions <xref:System.Activities.Statements.Transition.Trigger%2A> sont également annulées et replanifiées.Si <xref:System.Activities.Statements.Transition.Condition%2A> a la valeur `true`, ou s'il n'existe aucune condition, l'action <xref:System.Activities.Statements.State.Exit%2A> de l'état source est exécutée, puis le <xref:System.Activities.Statements.Transition.Action%2A> de la transition est exécuté.Lorsque <xref:System.Activities.Statements.Transition.Action%2A> se termine, le contrôle passe à l'état **Target**  
  
 Les transitions qui partagent un déclencheur commun sont appelées transitions de déclencheur partagées.Chaque transition d'un groupe de transitions de déclencheur partagé a le même déclencheur, mais un <xref:System.Activities.Statements.Transition.Condition%2A> et une action uniques.Pour ajouter des actions supplémentaires à une transition et créer une transition partagée, cliquez sur le cercle qui indique le début de la transition souhaitée et faites\-le glisser vers l'état souhaité.La nouvelle transition partagera un même déclencheur que la transition d'origine, mais elle aura une condition et une action uniques.Des transitions partagées peuvent également être créées à partir du concepteur de transition en cliquant sur **Ajouter une transition de déclencheur partagée** en bas du concepteur de transition, puis en sélectionnant l'état cible souhaité dans la liste déroulante **États disponibles pour la connexion**.  
  
> [!NOTE]
>  Notez que si la condition <xref:System.Activities.Statements.Transition.Condition%2A> d'une transition a pour valeur `False` \(ou si toutes les conditions d'une transition de déclencheur partagée ont la valeur `False`\), la transition n'a pas lieu et tous les déclencheurs de toutes les transitions de l'état sont replanifiés.  
  
 Pour plus d'informations sur la création de workflows de machine à états, consultez [Procédure : créer un workflow d'ordinateur d'état](../../../docs/framework/windows-workflow-foundation//how-to-create-a-state-machine-workflow.md), [Concepteur d'activités StateMachine](../Topic/StateMachine%20Activity%20Designer.md), [Concepteur d'activités d'état](../Topic/State%20Activity%20Designer.md), [Concepteur d'activités FinalState](../Topic/FinalState%20Activity%20Designer.md) et [Concepteur d'activités de transition](../Topic/Transition%20Activity%20Designer.md).  
  
## Terminologie de machine à états  
 Cette section explique la terminologie de machine à états utilisée dans cette rubrique.  
  
 État  
 Unité de base qui constitue une machine à états.Une machine à états peut être dans un état à un moment donné.  
  
 Action d'entrée  
 Activité exécutée lors de la transition à l'état  
  
 Action de sortie  
 Activité exécutée lors de la sortie de l'état  
  
 Transition  
 Relation directe entre deux états qui représente la réponse complète d'une machine à états à une occurrence d'un événement d'un type particulier.  
  
 Transition partagée  
 Transition qui partage un état source et un déclencheur avec une ou plusieurs transitions, mais qui possède une condition et une action uniques.  
  
 Déclencheur  
 Activité de déclenchement qui provoque une transition.  
  
 Condition  
 Contrainte qui doit avoir la valeur `true` après l'exécution du déclencheur de sorte que la transition se termine.  
  
 Action de transition  
 Activité qui est exécutée lors de l'exécution d'une certaine transition.  
  
 Transition conditionnelle  
 Transition avec une condition explicite.  
  
 Transition  
 Transition qui passe d'un état à elle\-même.  
  
 État initial  
 État qui représente le point de départ de la machine à états.  
  
 État final  
 État qui représente l'achèvement de la machine à états.  
  
## Voir aussi  
 [Procédure : créer un workflow d'ordinateur d'état](../../../docs/framework/windows-workflow-foundation//how-to-create-a-state-machine-workflow.md)   
 [Concepteur d'activités StateMachine](../Topic/StateMachine%20Activity%20Designer.md)   
 [Concepteur d'activités d'état](../Topic/State%20Activity%20Designer.md)   
 [Concepteur d'activités FinalState](../Topic/FinalState%20Activity%20Designer.md)   
 [Concepteur d'activités de transition](../Topic/Transition%20Activity%20Designer.md)