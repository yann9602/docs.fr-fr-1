---
title: "Propri&#233;t&#233;s d&#39;ex&#233;cution | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Propri&#233;t&#233;s d&#39;ex&#233;cution
Cet exemple montre comment définir et utiliser une propriété d'exécution dans une activité personnalisée.Dans cet exemple, la propriété d'exécution détermine la couleur de premier plan de la console.Un exemple de workflow montre comment différents chemins logiques d'exécution \(branches d'une activité <xref:System.Activities.Statements.Parallel>\) peuvent maintenir des couleurs de console différentes malgré l'exécution entrelacée d'activités \(à travers les branches de l'activité <xref:System.Activities.Statements.Parallel>\).  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez l'exemple de solution ExecutionProperties.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    > [!NOTE]
    >  La consultation de ThreeColors.xaml avant la génération de la solution affiche une erreur, car les activités personnalisées utilisées doivent être générées en même temps que la solution.  
  
2.  Générez et exécutez la solution.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`  
  
## Voir aussi