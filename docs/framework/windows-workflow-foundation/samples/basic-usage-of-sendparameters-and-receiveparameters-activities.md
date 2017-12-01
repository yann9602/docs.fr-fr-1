---
title: "Utilisation de base des activités SendParameters et ReceiveParameters"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a45e04c4368406255736312503e19de95ed12150
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a>Utilisation de base des activités SendParameters et ReceiveParameters
Cet exemple illustre l'utilisation des activités <xref:System.ServiceModel.Activities.SendParametersContent> et <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Le service expose une opération qui accepte un argument de type chaîne et retourne l'entrée au client. L'exemple montre comment configurer les paramètres pour ces activités de messagerie.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a>Utilisation de cet exemple  
  
1.  Chargez la solution du projet dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] et générez le projet.  
  
2.  En premier lieu, exécutez l'application EchoWorkflowService, générée dans [répertoire de base de la solution]\EchoWorkflowService\bin\debug.  
  
3.  En second lieu, exécutez l'application EchoWorkflowClient, générée dans [répertoire de base de la solution]\EchoWorkflowClient\bin\debug.  
  
4.  Le client appelle l'opération Echo sur le service et imprime les résultats. Une fois cette opération terminée, appuyez sur ENTRÉE pour quitter le client, puis le service.