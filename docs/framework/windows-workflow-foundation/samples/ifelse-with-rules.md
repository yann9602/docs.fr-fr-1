---
title: "IfElse With Rules | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# IfElse With Rules
Cet exemple illustre l'utilisation d'une condition de règle avec une activité <xref:System.Workflow.Activities.IfElseActivity>.  
  
 L'exemple transmet un paramètre `OrderValue` depuis l'hôte.La valeur du paramètre est utilisée dans une condition de règle sur la première branche de l'activité <xref:System.Workflow.Activities.IfElseActivity>.Si la valeur est inférieure à 10 000, la première branche s'exécute et l'activité <xref:System.Workflow.Activities.CodeActivity> de la première branche imprime **Get Manager Approval** \(obtenir l'approbation du responsable\) sur la console.Si la valeur est supérieure à 10 000, l'activité <xref:System.Workflow.Activities.CodeActivity> de la deuxième branche s'exécute et imprime **Get VP Approval** \(obtenir l'approbation du vice\-président\).  
  
### Pour générer l'exemple  
  
1.  Ouvrez la solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez la solution en appuyant sur Ctrl\+Maj\+B.  
  
3.  Exécutez la solution sans débogage en appuyant sur Ctrl\+F5.  
  
### Pour exécuter l'exemple  
  
-   Dans la fenêtre Invite de commandes du Kit de développement logiciel \(SDK\), exécutez le fichier .exe dans le dossier IfElseWithRules\\bin\\debug \(ou le dossier IfElseWithRules\\bin pour la version Visual Basic de l'exemple\), situé sous le dossier principal de l'exemple.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer :  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant :  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## Voir aussi  
 <xref:System.Workflow.Activities.Rules>   
 <xref:System.Workflow.Activities.IfElseActivity>   
 <xref:System.Workflow.Activities.CodeActivity>   
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>