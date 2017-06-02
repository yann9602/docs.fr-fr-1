---
title: "Activation d&#39;instance | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Activation d&#39;instance
Le magasin d'instances de workflow SQL exécute une tâche interne qui se réveille régulièrement et détecte les instances de workflow exécutables ou activables dans la base de données de persistance.En cas de détection d'une instance de workflow exécutable, il avertit l'hôte de workflow capable d'activer l'instance.En cas de détection d'une instance de workflow activable, il avertit un hôte générique qui active un hôte de workflow qui, à son tour, exécute l'instance de workflow.Les sections suivantes de cette rubrique décrivent en détail le processus d'activation d'instance.  
  
##  <a name="RunnableSection"></a> Détection et activation d'instances de workflow exécutables  
 Le magasin d'instances de workflow considère une instance de workflow comme *exécutable* si celle\-ci n'est pas à l'état suspendu ni terminé et satisfait les conditions suivantes :  
  
-   L'instance est déverrouillée et a un minuteur en attente qui a expiré.  
  
-   L'instance a un verrou périmé.  
  
-   L'instance est déverrouillée et son état est **Exécution**.  
  
 Lorsqu'il détecte une instance exécutable, le magasin d'instances de workflow SQL déclenche l'objet <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent>.Ensuite, le SqlWorkflowInstanceStore cesse de surveiller jusqu'à ce que l'objet <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> soit appelé une fois sur le magasin.  
  
 Un hôte de workflow qui s'est abonné à l'objet <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> et capable de charger l'instance exécute l'objet <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> par rapport au magasin d'instances pour charger l'instance en mémoire.Un hôte de workflow est considéré comme capable de charger une instance de workflow si l'hôte et l'instance ont une propriété de métadonnées **WorkflowServiceType** définie sur la même valeur.  
  
## Détection et activation d'instances de workflow activables  
 Une instance de workflow est considérée comme *activable* si elle est exécutable et si aucun hôte de workflow capable de charger l'instance est en cours d'exécution sur l'ordinateur.Consultez « Détection et activation d'instances de workflow exécutables », ci\-dessus, pour obtenir la définition d'une instance de workflow exécutable.  
  
 Lorsque le magasin d'instances de workflow SQL détecte une instance de workflow activable dans la base de données, il déclenche l'objet <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent>.Ensuite, le SqlWorkflowInstanceStore cesse de surveiller jusqu'à ce que l'objet <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> soit appelé une fois sur le magasin.  
  
 Lorsqu'un hôte générique qui s'est abonné à l'objet <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> reçoit l'événement, il exécute l'objet <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> par rapport au magasin d'instances pour obtenir des paramètres d'activation nécessaires à la création d'un hôte de workflow.L'hôte générique utilise ces paramètres d'activation pour créer un hôte de workflow qui, à son tour, charge et exécute l'instance de service exécutable.  
  
## Hôtes génériques  
 Un hôte générique est un hôte pour lequel la valeur de la propriété de métadonnées **WorkflowServiceType** pour les hôtes génériques est définie sur **WorkflowServiceType.Any**, cela afin d'indiquer qu'il peut gérer tout type de workflow.Un hôte générique a un paramètre XName nommé **ActivationType**.  
  
 Actuellement, le magasin d'instances de workflow SQL prend en charge des hôtes génériques ayant la valeur du paramètre ActivationType définie sur **WAS**.Si le paramètre ActivationType n'est pas défini sur WAS, le magasin d'instances de workflow SQL lève un objet <xref:System.Runtime.DurableInstancing.InstancePersistenceException>.Le service de gestion du flux de travail fourni avec le [!INCLUDE[dublin](../../../includes/dublin-md.md)] est un hôte générique dont le type d'activation est défini sur **WAS**.  
  
 Pour l'activation WAS, un hôte générique requiert un jeu de paramètres d'activation pour dériver l'adresse de point de terminaison à laquelle les nouveaux hôtes peuvent être activés.Les paramètres d'activation pour l'activation WAS sont : nom du site, chemin d'accès vers l'application relatif au site et chemin d'accès vers le service relatif à l'application.Lors de l'exécution de l'objet <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>, le magasin d'instances de workflow SQL stocke ces paramètres d'activation.  
  
## Période de détection des instances activables  
 La propriété **Période de détection des instances activables** du magasin d'instances de workflow SQL spécifie la période après laquelle ce dernier exécute une tâche de détection pour détecter toutes les instances de workflow exécutables ou activables dans la base de données de persistance, à l'issue du cycle de détection précédent.Pour plus d'informations sur cette propriété, consultez [Période de détection des instances activables](../../../docs/framework/windows-workflow-foundation//runnable-instances-detection-period.md).