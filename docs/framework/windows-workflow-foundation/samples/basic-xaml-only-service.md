---
title: "Service uniquement en XAML de base"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3fbf8a719647199439e2333ba5e26cbe51be3add
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="basic-xaml-only-service"></a><span data-ttu-id="95a67-102">Service uniquement en XAML de base</span><span class="sxs-lookup"><span data-stu-id="95a67-102">Basic XAML only Service</span></span>
<span data-ttu-id="95a67-103">Cet exemple montre comment créer un service uniquement en XAML.</span><span class="sxs-lookup"><span data-stu-id="95a67-103">This sample demonstrates how to create a XAML only service.</span></span> <span data-ttu-id="95a67-104">Le scénario est un service de diagnostic pour les problèmes liés à la voiture.</span><span class="sxs-lookup"><span data-stu-id="95a67-104">The scenario is a diagnostics service for car-related problems.</span></span> <span data-ttu-id="95a67-105">Le service est implémenté comme un workflow qui pose une série de questions au client afin de diagnostiquer le problème.</span><span class="sxs-lookup"><span data-stu-id="95a67-105">The service is implemented as a workflow that asks the client a series of questions to diagnose the problem.</span></span> <span data-ttu-id="95a67-106">Il existe deux types de problèmes que le service peut diagnostiquer (la voiture ne démarre pas ou l'air conditionné ne fonctionne pas).</span><span class="sxs-lookup"><span data-stu-id="95a67-106">There are two types of issues the service can diagnose (car does not start or air conditioning not working).</span></span> <span data-ttu-id="95a67-107">Le workflow utilise le modèle Demande/réponse du concepteur pour exposer trois opérations de service simples.</span><span class="sxs-lookup"><span data-stu-id="95a67-107">The workflow uses Request/Reply template from the designer to expose three simple service operations.</span></span> <span data-ttu-id="95a67-108">Le service est hébergé dans IIS en créant un répertoire virtuel dans IIS et en copiant le service1.xamlx et les fichiers Web.config dans le répertoire virtuel ; aucun code compilé n'est requis.</span><span class="sxs-lookup"><span data-stu-id="95a67-108">The service is hosted in IIS by creating a virtual directory in IIS and copying the service1.xamlx and Web.config files into the virtual directory, no compiled code is required.</span></span> <span data-ttu-id="95a67-109">Par défaut cet exemple copie automatiquement les fichiers nécessaires dans le répertoire virtuel créé lorsque vous suivez les instructions d’installation pour les exemples WCF et WF : [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) lors de la génération dans Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="95a67-109">By default this sample will automatically copy the needed files into the virtual directory created when you follow the setup instructions for the WCF and WF samples: [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) when built in Visual Studio 2010.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="95a67-110">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="95a67-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="95a67-111">Chargez la solution du projet dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] et générez le projet.</span><span class="sxs-lookup"><span data-stu-id="95a67-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="95a67-112">Exécutez l'application cliente générée dans [répertoire de base de la solution]\Client\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="95a67-112">Run the Client application generated in [solution base directory]\Client\bin\debug.</span></span>  
  
3.  <span data-ttu-id="95a67-113">L'application imprime les options, sélectionne une option.</span><span class="sxs-lookup"><span data-stu-id="95a67-113">The application prints out options, selects an option.</span></span> <span data-ttu-id="95a67-114">L'application pose ensuite des questions, répondez-y par oui ou non (à l'aide des touches O/N).</span><span class="sxs-lookup"><span data-stu-id="95a67-114">The application then asks some questions, answer them yes or no (using Y/N keys).</span></span> <span data-ttu-id="95a67-115">Lorsque le service a terminé le diagnostic des problèmes, l'application imprime un diagnostic.</span><span class="sxs-lookup"><span data-stu-id="95a67-115">When the service is done diagnosing the issues, the application prints out a diagnosis.</span></span>  
  
4.  <span data-ttu-id="95a67-116">L'application revient aux options.</span><span class="sxs-lookup"><span data-stu-id="95a67-116">The application goes back to the options.</span></span> <span data-ttu-id="95a67-117">Vous pouvez diagnostiquer un autre problème ou quitter l'application.</span><span class="sxs-lookup"><span data-stu-id="95a67-117">You can diagnose another problem or exit the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="95a67-118">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="95a67-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="95a67-119">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="95a67-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="95a67-120">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="95a67-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="95a67-121">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="95a67-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`  
  
## <a name="see-also"></a><span data-ttu-id="95a67-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95a67-122">See Also</span></span>
