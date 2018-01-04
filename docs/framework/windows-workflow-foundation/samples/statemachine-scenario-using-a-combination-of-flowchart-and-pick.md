---
title: "Scénario StateMachine à l'aide d'une combinaison de FlowChart et de Pick"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39ae1be025e3b888fff8b46ebbc45832c218dda7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a>Scénario StateMachine à l'aide d'une combinaison de FlowChart et de Pick
Cet exemple montre comment implémenter un scénario de chronomètre simple à l'aide d'une combinaison des activités <xref:System.Activities.Statements.Flowchart> et <xref:System.Activities.Statements.Pick>. Il utilise Receive et Send dans l'activité Pick pour écouter des événements de chronomètre.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez-vous sur la page de téléchargement pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a>Détails de l'exemple  
 Le tableau suivant répertorie les projets compris dans cet exemple.  
  
|Nom du projet|Description|  
|-|-|  
|StopWatchService|Ce projet contient l'implémentation d'une machine à états pour l'exemple de chronomètre à l'aide d'une combinaison des activités <xref:System.Activities.Statements.Flowchart> et <xref:System.Activities.Statements.Pick>.<br /><br /> L'activité <xref:System.Activities.Statements.Pick> a 3 instructions <xref:System.Activities.Statements.PickBranch> dans la propriété <xref:System.Activities.Statements.Pick.Branches%2A> qui écoutent les événements `GetStart`, `GetStop` et `GetOff`. En fonction de l'événement entrant, les déclencheurs pour l'une des branches s'activent et la propriété <xref:System.Activities.Statements.PickBranch.Action%2A> correspondante est déclenchée. Dans la propriété <xref:System.Activities.Statements.PickBranch.Action%2A>, il y a une instruction <xref:System.Activities.Statements.Switch%601> qui évalue si la transition est une transition légitime, et si tel est le cas, la propriété `currentState` est mise à jour avec l'état de transition et envoyée au client.<br /><br /> L'activité <xref:System.Activities.Statements.FlowDecision> à la fin de <xref:System.Activities.Statements.Flowchart> évalue la propriété `currentState` pour déterminer si l'état est terminal. Si tel est le cas, le workflow se termine ; sinon, le contrôle revient au début de l'activité <xref:System.Activities.Statements.Pick> où le workflow attend des événements de chronomètre supplémentaires.|  
|StopWatchClient|Il s'agit d'une application console de workflow séquentiel simple qui envoie différents événements de chronomètre avec des combinaisons de Send ou de Receive simples.|  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution StateMachineWithPick.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Démarrez StopWatchService.exe de [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] en tant qu’administrateur en cliquant avec le bouton droit sur le fichier .exe et en sélectionnant **exécuter en tant qu’administrateur**.  
  
    1.  Accédez au dossier StateMachineWithPick\CS\StopWatchService\bin\Debug.  
  
    2.  Cliquez sur le fichier StopWatchService.exe, puis sélectionnez **exécuter en tant qu’administrateur**.  
  
4.  Démarrez l'application cliente StopWatchClient à partir de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    1.  Dans **l’Explorateur de solutions**, sélectionnez le **StopWatchClient** de projet et avec le bouton droit **définir comme projet de démarrage**.  
  
    2.  Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
5.  Revenez à la fenêtre de console de StopWatchService.exe pour voir les transitions d'état.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`