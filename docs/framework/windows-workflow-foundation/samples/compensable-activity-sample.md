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
# <a name="compensable-activity-sample"></a><span data-ttu-id="6c8ff-102">Exemple d'activité compensable</span><span class="sxs-lookup"><span data-stu-id="6c8ff-102">Compensable Activity Sample</span></span>
<span data-ttu-id="6c8ff-103">Cet exemple montre comment utiliser l'activité `CompensableActivity` pour définir le travail à faire pour une action donnée pendant une exécution normale et le travail qui doit être fait pour compenser cette action, si nécessaire ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="6c8ff-103">This sample demonstrates how to use the `CompensableActivity` activity to define the work to be done for a given action during normal execution and the work that is necessary to be done to compensate that action, if necessary at a later time.</span></span>  <span data-ttu-id="6c8ff-104">La première partie de l'exemple montre comment les unités de travail compensable peuvent être définies dans [!INCLUDE[wf](../../../../includes/wf-md.md)] à l'aide d'une activité `CompensableActivity` et comment elles sont exécutées avec succès.</span><span class="sxs-lookup"><span data-stu-id="6c8ff-104">The first part of the sample shows how units of compensable work can be defined in [!INCLUDE[wf](../../../../includes/wf-md.md)] using a `CompensableActivity` activity and how they are executed in a successful run.</span></span>  <span data-ttu-id="6c8ff-105">La deuxième partie de l'exemple montre comment ces mêmes unités de travail compensable se chargent automatiquement de la compensation lorsqu'un événement inattendu est atteint et que l'instance de workflow est annulée.</span><span class="sxs-lookup"><span data-stu-id="6c8ff-105">The second part of the sample shows how the same units of compensable work automatically take care of compensation when an unexpected event is hit and the workflow instance is canceled.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6c8ff-106">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="6c8ff-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6c8ff-107">À l'aide de Visual Studio 2010, ouvrez CompensableActivity.sln.</span><span class="sxs-lookup"><span data-stu-id="6c8ff-107">Using Visual Studio 2010, open the CompensableActivity.sln.</span></span>  
  
2.  <span data-ttu-id="6c8ff-108">Générez la solution en appuyant sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="6c8ff-108">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="6c8ff-109">Exécutez l'application en appuyant sur F5.</span><span class="sxs-lookup"><span data-stu-id="6c8ff-109">Run the application by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6c8ff-110">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6c8ff-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6c8ff-111">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="6c8ff-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6c8ff-112">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6c8ff-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6c8ff-113">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="6c8ff-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`