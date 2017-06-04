---
title: "Concepts Windows Workflow fondamentaux | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e930e80-5060-45d2-8a7a-95c0690105d4
caps.latest.revision: 27
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 27
---
# Concepts Windows Workflow fondamentaux
Le développement de flux de travail dans [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] fait appel à des concepts que certains développeurs peuvent ne pas connaître.Cette rubrique en décrit quelques\-uns, ainsi que la façon dont ils sont implémentés.  
  
## Flux de travail et activités  
 Un flux de travail est une collection structurée d'actions qui modélise un processus.Chaque action du flux de travail est modélisée en tant qu'activité.Un hôte interagit avec un flux de travail à l'aide des objets suivants : <xref:System.Activities.WorkflowInvoker> pour l'appel d'un flux de travail comme s'il s'agissait d'une méthode, <xref:System.Activities.WorkflowApplication> pour le contrôle explicite sur l'exécution d'une instance de workflow unique et <xref:System.ServiceModel.WorkflowServiceHost> pour des interactions basées sur des messages dans les scénarios à plusieurs instances.Comme les étapes du flux de travail sont définies comme une hiérarchie d'activités, l'activité supérieure de la hiérarchie peut être désignée pour définir le flux de travail lui\-même.Ce modèle de hiérarchie remplace les classes `SequentialWorkflow` et `StateMachineWorkflow` explicites des versions précédentes.Les activités elles\-mêmes peuvent être développées comme des collections d'autres activités \(à l'aide de la classe <xref:System.Activities.Activity> comme base, généralement définie en XAML\). Sinon, elles peuvent être créées de façon personnalisée à l'aide de la classe <xref:System.Activities.CodeActivity> qui peut utiliser le runtime d'accès aux données ou à l'aide de la classe <xref:System.Activities.NativeActivity> qui montre la portée de l'exécution du workflow à l'auteur de l'activité.Les activités développées à l'aide des classes <xref:System.Activities.CodeActivity> et <xref:System.Activities.NativeActivity> sont créées à l'aide de langages compatibles avec le CLR comme C\#.  
  
## Modèle de données des activités  
 Les activités stockent et partagent des données à l'aide des types indiqués dans le tableau suivant :  
  
|||  
|-|-|  
|Variable|Stocke des données dans une activité.|  
|Argument|Déplace les données vers l'intérieur et l'extérieur d'une activité.|  
|Expression|Activité ayant une valeur de retour élevée utilisée dans les liaisons d'arguments.|  
  
## Exécution du workflow  
 L'exécution du workflow est l'environnement dans lequel les flux de travail s'exécutent.<xref:System.Activities.WorkflowInvoker> est la façon la plus simple d'exécuter un flux de travail.L'hôte utilise l'objet <xref:System.Activities.WorkflowInvoker> pour les actions suivantes :  
  
-   appeler un flux de travail de façon synchrone ;  
  
-   fournir l'entrée à un flux de travail ou en extraire des sorties ;  
  
-   ajouter des extensions à utiliser par les activités.  
  
 <xref:System.Activities.ActivityInstance> est le proxy thread\-safe que les hôtes peuvent utiliser pour interagir avec le runtime.L'hôte utilise l'objet <xref:System.Activities.ActivityInstance> pour les actions suivantes :  
  
-   acquérir une instance en la créant ou en la chargeant à partir d'un magasin d'instances ;  
  
-   être informé des événements du cycle de vie de l'instance ;  
  
-   contrôler l'exécution du workflow ;  
  
-   fournir l'entrée à un flux de travail ou en extraire des sorties ;  
  
-   signaler une continuation de flux de travail et passer des valeurs dans le flux de travail ;  
  
-   rendre persistantes les données du workflow ;  
  
-   ajouter des extensions à utiliser par les activités.  
  
 Les activités accèdent à l'environnement d'exécution du flux de travail à l'aide de la classe dérivée <xref:System.Activities.ActivityContext> appropriée, telle que <xref:System.Activities.NativeActivityContext> ou <xref:System.Activities.CodeActivityContext>.Ils utilisent celle\-ci pour la résolution d'arguments et de variables, la planification d'activités enfants et de nombreuses autres fins.  
  
## Services  
 Les flux de travail offrent une façon naturelle d'implémenter les services faiblement couplés et d'y accéder, à l'aide d'activités de messagerie.Les activités de messagerie reposent sur [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et sont le mécanisme principal utilisé pour obtenir des données dans ou hors d'un flux de travail.Vous pouvez composer des activités de messagerie ensemble pour modéliser tout type de modèle d'échange de messages que vous souhaitez.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)] voir [Activités de messagerie](../../../docs/framework/wcf/feature-details/messaging-activities.md).Les services de flux de travail sont hébergés à l'aide de la classe <xref:System.ServiceModel.Activities.WorkflowServiceHost>.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Vue d'ensemble de l'hébergement de services de workflow](../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md).[!INCLUDE[crabout](../../../includes/crabout-md.md)] les services de workflow, consultez [Services de workflow](../../../docs/framework/wcf/feature-details/workflow-services.md)  
  
## Persistance, déchargement et workflows de longue durée  
 Windows Workflow simplifie la création de programmes réactifs de longue durée en fournissant les éléments suivants :  
  
-   activités qui accèdent à l'entrée externe ;  
  
-   capacité à créer des objets <xref:System.Activities.Bookmark> qui peuvent être repris par un écouteur hôte ;  
  
-   Capacité à rendre persistantes les données d'un workflow et décharger le flux de travail, puis le recharger et le réactiver en réponse à la reprise d'objets <xref:System.Activities.Bookmark> dans un flux de travail particulier.  
  
 Un flux de travail exécute en continu des activités jusqu'à ce qu'il n'y en ait plus à exécuter ou jusqu'à ce que toutes les activités en cours d'exécution soient en attente de réponse.Dans ce dernier cas, le flux de travail est inactif.Il est fréquent qu'un hôte décharge les flux de travail qui sont devenus inactifs et les recharger pour reprendre l'exécution lorsqu'un message arrive.<xref:System.ServiceModel.Activities.WorkflowServiceHost> fournit les fonctionnalités pour cette fonction, ainsi qu'une stratégie de déchargement extensible.Pour les blocs d'exécution utilisant des données d'état volatiles ou des données qui ne peuvent pas être rendues persistantes autrement, une activité peut indiquer à un hôte qu'il ne doit pas être rendu persistant à l'aide de l'objet <xref:System.Activities.NoPersistHandle>.Un flux de travail peut également rendre explicitement ses données persistantes sur un support de stockage durable à l'aide de l'activité <xref:System.Activities.Statements.Persist>.