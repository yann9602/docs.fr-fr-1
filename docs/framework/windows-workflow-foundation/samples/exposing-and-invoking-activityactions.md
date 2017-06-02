---
title: "Exposition et appel d&#39;ActivityActions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Exposition et appel d&#39;ActivityActions
Cet exemple montre comment développer une activité personnalisée qui a un <xref:System.Activities.ActivityAction>.Il montre également comment utiliser cette activité en fournissant une implémentation d'<xref:System.Activities.ActivityAction>.  
  
 Un <xref:System.Activities.ActivityAction> permet à un auteur d'activité d'exposer des « espaces » avec des signatures spécifiques où l'utilisateur de l'activité peut incorporer un comportement personnalisé.Par exemple, l'activité <xref:System.Activities.Statements.ForEach> \(qui fonctionne sur une collection d'éléments\) a un <xref:System.Activities.ActivityAction> qui permet à l'utilisateur de l'activité d'incorporer un comportement qui fonctionne sur l'élément de l'itération en cours.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez l'exemple de solution **ActivityAction.sln** dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez et exécutez la solution.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`  
  
## Voir aussi