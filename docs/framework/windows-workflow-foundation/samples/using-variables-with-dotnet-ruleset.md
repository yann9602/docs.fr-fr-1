---
title: "Utilisation de variables avec un Ruleset&#160;.NET Framework&#160;3.5 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Utilisation de variables avec un Ruleset&#160;.NET Framework&#160;3.5
Cet exemple montre comment créer un workflow qui utilise l'activité <xref:System.Activities.Statements.Interop> pour une intégrer une activité personnalisée écrite dans [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] et qui utilise une stratégie et des règles.Le workflow passe des données à l'activité personnalisée en liant des variables aux propriétés de dépendance exposées par l'activité personnalisée.  
  
## Exemple de procédure pas à pas  
  
#### Pour examiner TravelRuleLibrary  
  
1.  À l'aide de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], ouvrez le fichier solution InteropWith35RuleSet.sln.  
  
2.  Ouvrez TravelRuleSet.cs dans le concepteur de workflow.  
  
     Une activité séquentielle personnalisée qui contient un <xref:System.Workflow.Activities.PolicyActivity> s'affiche.  
  
3.  Double\-cliquez sur l'activité de stratégie DiscountPolicy pour examiner les règles.  
  
     L'éditeur de règles s'affiche pour présenter les règles.  
  
4.  Cliquez avec le bouton droit sur `DiscountPolicy` et sélectionnez l'option **Afficher le code** pour examiner le code C\# code\-beside pour l'activité.  
  
     Observez le paramètre de propriété de dépendance pour `DiscountLevel`.Cela est équivalent à des arguments dans le [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les arguments, consultez [Variables et arguments](../../../../docs/framework/windows-workflow-foundation//variables-and-arguments.md).  
  
## InteropWith35RuleSet  
 C'est un projet de workflow séquentiel qui utilise l'activité <xref:System.Activities.Statements.Interop> pour une intégration à l'ensemble de règles personnalisé créé dans le projet `TravelRuleLibrary`.Les variables sont créées sur l'activité <xref:System.Activities.Statements.Sequence> de niveau supérieur.L'activité <xref:System.Activities.Statements.Interop> est utilisée pour une intégration à l'activité `TravelRuleSet`.Les variables déclarées sur <xref:System.Activities.Statements.Sequence> sont utilisées pour créer une liaison aux propriétés de dépendance.  
  
## Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution InteropWith35RuleSet.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl\+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`  
  
## Voir aussi