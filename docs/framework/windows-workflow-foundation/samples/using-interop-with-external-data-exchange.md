---
title: "Utilisation d&#39;Interop avec l&#39;&#233;change interne de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Utilisation d&#39;Interop avec l&#39;&#233;change interne de donn&#233;es
L'activité <xref:System.Activities.Statements.Interop> peut être utilisée pour exécuter des activités [!INCLUDE[wf](../../../../includes/wf-md.md)] dans [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] et [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] \(WF3\), et des workflows [!INCLUDE[wf2](../../../../includes/wf2-md.md)] dans [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] \(WF4\).Cet exemple montre comment configurer et exécuter un workflow WF3 qui utilise <xref:System.Workflow.Activities.ExternalDataExchangeService> \(et les activités personnalisées correspondantes pour appeler les méthodes et gérer les événements\) à l'aide de l'activité <xref:System.Activities.Statements.Interop> dans un service de workflow WF4.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### Pour utiliser cet exemple  
  
1.  Ouvrez le fichier ExternalDataExchange.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Pour créer l'exemple, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter l'exemple, appuyez sur F5.