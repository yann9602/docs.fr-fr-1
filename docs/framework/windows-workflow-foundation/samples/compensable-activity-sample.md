---
title: "Exemple d'activité compensable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4ad3de1b3e9361e5de4803e06c8d257fbb9de76e
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="compensable-activity-sample"></a>Exemple d'activité compensable
Cet exemple montre comment utiliser l'activité `CompensableActivity` pour définir le travail à faire pour une action donnée pendant une exécution normale et le travail qui doit être fait pour compenser cette action, si nécessaire ultérieurement.  La première partie de l'exemple montre comment les unités de travail compensable peuvent être définies dans [!INCLUDE[wf](../../../../includes/wf-md.md)] à l'aide d'une activité `CompensableActivity` et comment elles sont exécutées avec succès.  La deuxième partie de l'exemple montre comment ces mêmes unités de travail compensable se chargent automatiquement de la compensation lorsqu'un événement inattendu est atteint et que l'instance de workflow est annulée.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  À l'aide de Visual Studio 2010, ouvrez CompensableActivity.sln.  
  
2.  Générez la solution en appuyant sur Ctrl+Maj+B.  
  
3.  Exécutez l'application en appuyant sur F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`