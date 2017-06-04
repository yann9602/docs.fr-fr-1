---
title: "Charge &#224; partir du XAML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Charge &#224; partir du XAML
Cet exemple montre comment charger dynamiquement un workflow XAML sans devoir exécuter l'outil XamlBuildTask.Au lieu de cela, l'exemple appelle la méthode <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>.L'exemple est une application cliente [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] qui charge des workflows XAML à l'aide de la classe <xref:System.Activities.XamlIntegration.ActivityXamlServices> et qui les exécute.Une fois qu'ils ont été chargés à l'aide de la classe <xref:System.Activities.XamlIntegration.ActivityXamlServices>, un <xref:System.Activities.DynamicActivity%601> pouvant être exécuté est retourné.  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution LoadFromXAML.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl\+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`  
  
## Voir aussi