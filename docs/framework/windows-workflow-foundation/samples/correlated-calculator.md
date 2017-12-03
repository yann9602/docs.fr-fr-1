---
title: "Calculatrice corrélée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6296ecb5c708d344624cac6e24247d2163fd66b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="correlated-calculator"></a><span data-ttu-id="642b4-102">Calculatrice corrélée</span><span class="sxs-lookup"><span data-stu-id="642b4-102">Correlated Calculator</span></span>
<span data-ttu-id="642b4-103">Cet exemple montre comment utiliser les activités de messagerie (<xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply>) dans le concepteur avec une corrélation basée sur le contenu selon un paramètre dans le message.</span><span class="sxs-lookup"><span data-stu-id="642b4-103">This sample demonstrates how to use the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>) in the designer with content-based correlation based on a parameter in the message.</span></span> <span data-ttu-id="642b4-104">Dans ce scénario, les opérations de la calculatrice sont dans un convoi parallèle.</span><span class="sxs-lookup"><span data-stu-id="642b4-104">In this scenario, the operations of the calculator are in a parallel convoy.</span></span> <span data-ttu-id="642b4-105">Une instance et une corrélation (selon `CalculatorId`) sont toutes deux créées lorsque le premier message est envoyé au workflow et les messages suivants avec le même `CalculatorId` sont distribués à cette instance jusqu'à l'appel de l'opération de réinitialisation.</span><span class="sxs-lookup"><span data-stu-id="642b4-105">Both an instance and a correlation (based on `CalculatorId`) are created when the first message is sent to the workflow, and subsequent messages with the same `CalculatorId` are dispatched to that instance until the Reset operation is called.</span></span> <span data-ttu-id="642b4-106">Le client est implémenté comme une application WPF qui utilise un proxy client basé sur du code pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="642b4-106">The client is implemented as a WPF application that uses a code-based client proxy to communicate with the service.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="642b4-107">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="642b4-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="642b4-108">Démarrez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] avec des autorisations élevées, ouvrez le fichier solution For.sln.</span><span class="sxs-lookup"><span data-stu-id="642b4-108">Start [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] in elevated permissions, open the For.sln solution file.</span></span>  
  
    1.  <span data-ttu-id="642b4-109">Naviguez jusqu'au dossier qui contient [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="642b4-109">Navigate to the folder that contains [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    2.  <span data-ttu-id="642b4-110">Cliquez sur Devenv.exe et sélectionnez **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="642b4-110">Right-click Devenv.exe and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="642b4-111">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution CorrelatedCalculator.sln.</span><span class="sxs-lookup"><span data-stu-id="642b4-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CorrelatedCalculator.sln solution file.</span></span>  
  
3.  <span data-ttu-id="642b4-112">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="642b4-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="642b4-113">Pour exécuter le projet de service, appuyez sur CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="642b4-113">To run the service project, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="642b4-114">Une fois que le service est prêt et qu'il écoute les messages, dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet Client et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="642b4-114">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="642b4-115">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="642b4-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="642b4-116">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="642b4-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="642b4-117">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="642b4-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="642b4-118">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="642b4-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`