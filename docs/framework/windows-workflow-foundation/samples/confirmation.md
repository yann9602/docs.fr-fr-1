---
title: "Confirmation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8637aeaf-ac9e-49b8-93f4-da15dee45277
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Confirmation
Cet exemple présente quatre scénarios courants se rapportant à l'utilisation de <xref:System.Activities.Statements.CompensableActivity> et à la confirmation.L'exemple exécute quatre workflows pour illustrer la confirmation.Cet exemple est disponible dans les versions déclarative et impérative.  
  
## Confirmer une activité compensable  
 Le premier workflow, qui est composé d'une séquence de deux instances <xref:System.Activities.Statements.CompensableActivity>, montre comment confirmer une activité compensable.Après l'achèvement du deuxième <xref:System.Activities.Statements.CompensableActivity>, une activité de confirmation confirme la première activité.Lorsque le workflow se termine correctement, toutes les instances <xref:System.Activities.Statements.CompensableActivity> qui n'ont pas été confirmées ou compensées sont automatiquement confirmées dans l'ordre par défaut.Sans la confirmation, le deuxième <xref:System.Activities.Statements.CompensableActivity> aurait été confirmé en premier.  
  
## Compensation explicite  
 Le deuxième scénario présente l'effet sur la confirmation par défaut lorsqu'un <xref:System.Activities.Statements.CompensableActivity> est compensé de manière explicite.Le workflow est composé d'une séquence de deux activités <xref:System.Activities.Statements.CompensableActivity>. Une fois la deuxième terminée, la première est compensée de manière explicite.Par conséquent, lorsque le workflow se termine, seul le deuxième <xref:System.Activities.Statements.CompensableActivity> est confirmé.  
  
## Contrôle de l'ordre de confirmation pour les activités CompensableActivity imbriquées  
 Le troisième scénario montre comment contrôler l'ordre de confirmation pour des <xref:System.Activities.Statements.CompensableActivity> imbriqués.Le scénario est composé d'un <xref:System.Activities.Statements.CompensableActivity> comme racine du workflow.Le corps du <xref:System.Activities.Statements.CompensableActivity> racine est une séquence de trois <xref:System.Activities.Statements.CompensableActivity>.Le <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> pour le <xref:System.Activities.Statements.CompensableActivity> racine est une séquence qui spécifie le premier <xref:System.Activities.Statements.CompensableActivity> imbriqué doit être confirmé, puis le deuxième.Lorsque le workflow se termine, il confirme le <xref:System.Activities.Statements.CompensableActivity> racine, qui confirme ensuite le premier, le deuxième et le troisième <xref:System.Activities.Statements.CompensableActivity> imbriqués, dans cet ordre.Par conséquent, l'ordre de confirmation par défaut est fondamentalement inversé.Étant donné que le troisième <xref:System.Activities.Statements.CompensableActivity> n'a pas été explicitement confirmé dans le cadre du <xref:System.Activities.Statements.CompensableActivity> racine par <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>, il est confirmé d'après l'ordre par défaut.Toutefois, étant donné qu'il est le seul <xref:System.Activities.Statements.CompensableActivity> non confirmé, cela signifies simplement qu'il est confirmé.  
  
## Étendue des variables  
 Le quatrième scénario montre comment la durée de vie des variables définies pour un <xref:System.Activities.Statements.CompensableActivity> ou l'un de ses parents se trouve toujours dans l'étendue lorsque le gestionnaire <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> ou <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> est exécuté, même si l'activité ou le workflow est terminé.Le workflow est composé d'une séquence de deux <xref:System.Activities.Statements.CompensableActivity>.Dans le corps du premier, la valeur de la variable `mySum` est la somme de 5 et de 10, et le résultat est imprimé.Dans le corps du deuxième <xref:System.Activities.Statements.CompensableActivity>, la valeur de la somme est la somme existante à laquelle est ajoutée la valeur 7, et le résultat est imprimé.Un gestionnaire de confirmation personnalisé est défini pour le premier <xref:System.Activities.Statements.CompensableActivity>, qui imprime la somme, soustrait 7, et imprime à nouveau la somme.En inspectant les sommes imprimées, il est clair que la variable se trouve dans l'étendue non seulement pour les corps des deux <xref:System.Activities.Statements.CompensableActivity>, mais également pour <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.  
  
#### Pour exécuter l'exemple  
  
1.  Chargez la solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Exécutez l'application ConfirmationSample.exe.  
  
3.  Observez la sortie suivante :  
  
 **Explicit confirmation:Start of workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: Confirmation HandlerEnd of workflowCompensableActivity2: Confirmation HandlerExplicit compensation:Start of workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: Compensation HandlerEnd of workflowCompensableActivity2: Confirmation HandlerCustom confirmation handler:Start of workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity3: BodyEnd of workflowCompensableActivity1: Confirmation HandlerCompensableActivity2: Confirmation HandlerCompensableActivity3: Confirmation HandlerVariable access in a confirmation handler:Start of workflowCompensableActivity1: BodyCompensableActivity1: The sum is: 15CompensableActivity2: BodyCompensableActivity2: Adding 7 to the sumCompensableActivity2: The sum is now: 22End of workflowCompensableActivity2: Confirmation HandlerCompensableActivity1: Confirmation HandlerCompensableActivity2: The sum is: 22CompensableActivity2: After subtracting 12 the sum is now: 10Press ENTER to exit.**  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Compensation\Confirmation`  
  
## Voir aussi