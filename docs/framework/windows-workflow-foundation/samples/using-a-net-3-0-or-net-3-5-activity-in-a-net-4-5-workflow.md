---
title: "Utilisation d&#39;une activit&#233;&#160;.NET Framework&#160;3.0 ou&#160;.NET Framework&#160;3.5 dans un Workflow&#160;.NET Framework&#160;4.5 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c53fd4c-5dd0-4fb4-ab6b-111302629548
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Utilisation d&#39;une activit&#233;&#160;.NET Framework&#160;3.0 ou&#160;.NET Framework&#160;3.5 dans un Workflow&#160;.NET Framework&#160;4.5
L'activité <xref:System.Activities.Statements.Interop> vous permet d'exécuter une activité [!INCLUDE[wf](../../../../includes/wf-md.md)] de .NET Framework 3.0 dans un workflow [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].Cet exemple montre comment utiliser l'activité <xref:System.Activities.Statements.Interop> pour passer une chaîne en tant qu'argument à une activité [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] personnalisée.  
  
## Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier solution SimpleInterop.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl\+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Migration\SimpleInterop`  
  
## Voir aussi