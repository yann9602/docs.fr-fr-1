---
title: "Simple Policy | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Simple Policy
Cet exemple indique comment utiliser une activité <xref:System.Workflow.Activities.PolicyActivity> dans un workflow.  
  
 Le workflow séquentiel de cet exemple est créé à l'aide d'une activité <xref:System.Workflow.Activities.PolicyActivity>.Le workflow définit les champs `orderValue`, `customerType` et `discount` utilisés pour configurer un workflow de remise de produit.Les règles configurées dans le fichier de règles définissent une valeur de remise basée sur `orderValue` et sur `customerType`.Les champs `orderValue` et `customerType` sont définis dans la définition de classe `SimplePolicyWorkflow` et peuvent être changés pour modifier le comportement.La remise obtenue est écrite dans la console dans le gestionnaire d'événements <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> défini dans la classe `SimplePolicyWorkflow`.  
  
### Pour générer l'exemple  
  
1.  Ouvrez la solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez la solution en appuyant sur Ctrl\+Maj\+B.  
  
3.  Exécutez la solution sans débogage en appuyant sur Ctrl\+F5.  
  
### Pour exécuter l'exemple  
  
-   Dans la fenêtre d'invite de commandes du Kit de développement logiciel \(SDK\), exécutez le fichier .exe dans le dossier SimplePolicy\\bin\\debug \(ou le dossier SimplePolicy\\bin pour la version Visual Basic de l'exemple\), situé sous le dossier principal de l'exemple.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer :  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant :  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## Voir aussi  
 <xref:System.Workflow.Activities.Rules.RuleSet>   
 <xref:System.Workflow.Activities.PolicyActivity>   
 [Advanced Policy](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)