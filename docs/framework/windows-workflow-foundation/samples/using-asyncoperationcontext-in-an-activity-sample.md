---
title: "Utilisation d'AsyncOperationContext dans un exemple d'activité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5aa36c3173e4e20d063f93b3583d063057b9bac7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a>Utilisation d'AsyncOperationContext dans un exemple d'activité
Cet exemple montre comment développer un <xref:System.Activities.CodeActivity> personnalisé qui utilise <xref:System.Activities.AsyncCodeActivityContext> pour effectuer un travail de façon asynchrone en dehors du workflow.  
  
## <a name="sample-details"></a>Détails de l'exemple  
 L'exemple d'activité utilise les méthodes <xref:System.IO.FileStream.BeginWrite%2A> et <xref:System.IO.FileStream.EndWrite%2A> sur la classe <xref:System.IO.FileStream> pour écrire, de façon asynchrone, des données dans un fichier. Le modèle présenté ici peut être adapté pour une utilisation avec d'autres méthodes asynchrones. Pendant que l'opération asynchrone est en cours d'exécution, d'autres activités du workflow peuvent s'exécuter, mais le workflow ne peut pas être rendu persistant.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez l'exemple de solution Async.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez et exécutez la solution.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`