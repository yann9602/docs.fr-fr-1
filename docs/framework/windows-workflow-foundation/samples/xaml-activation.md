---
title: XAML Activation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53665f39c6c0c7e5c7956912b05e3fd80659ddcb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-activation"></a><span data-ttu-id="6ef8d-102">XAML Activation</span><span class="sxs-lookup"><span data-stu-id="6ef8d-102">XAML Activation</span></span>
<span data-ttu-id="6ef8d-103">Cet exemple montre comment héberger un workflow déclaratif dans IIS.</span><span class="sxs-lookup"><span data-stu-id="6ef8d-103">This sample demonstrates how to host a declarative workflow in IIS.</span></span> <span data-ttu-id="6ef8d-104">C'est un workflow de base appelé `EchoService` qui comporte une opération.</span><span class="sxs-lookup"><span data-stu-id="6ef8d-104">The sample is a basic workflow called `EchoService` that has one operation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6ef8d-105">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6ef8d-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6ef8d-106">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="6ef8d-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6ef8d-107">Si ce répertoire n'existe pas, rendez-vous sur la page de téléchargement pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ef8d-107">If this directory does not exist, go to (download page) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6ef8d-108">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="6ef8d-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6ef8d-109">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="6ef8d-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6ef8d-110">Ouvrez la solution XAMLActivation.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ef8d-110">Open the XAMLActivation.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="6ef8d-111">Générez la solution en appuyant sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="6ef8d-111">Build the solution by pressing **F5**.</span></span>  
  
3.  <span data-ttu-id="6ef8d-112">Exécutez WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="6ef8d-112">Run WcfTestClient.exe.</span></span> <span data-ttu-id="6ef8d-113">À partir d'une invite de commandes, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="6ef8d-113">From a command prompt, type in the following:</span></span>  
  
    1.  <span data-ttu-id="6ef8d-114">cd %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE</span><span class="sxs-lookup"><span data-stu-id="6ef8d-114">cd %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE</span></span>  
  
    2.  <span data-ttu-id="6ef8d-115">Exécutez WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="6ef8d-115">Run WcfTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="6ef8d-116">Définissez l'adresse du service sur WcfTestClient.exe en appuyant sur CTRL+MAJ+A et en affectant à l'adresse du service la valeur http://localhost:56133/Service.xamlx.</span><span class="sxs-lookup"><span data-stu-id="6ef8d-116">Set the address of the service on WcfTestClient.exe by pressing CTRL+SHIFT+A and setting the service address to http://localhost:56133/Service.xamlx.</span></span>  
  
5.  <span data-ttu-id="6ef8d-117">Effectuez l'opération Echo pour tester le service.</span><span class="sxs-lookup"><span data-stu-id="6ef8d-117">Perform the echo operation to test the service.</span></span>  
  
6.  <span data-ttu-id="6ef8d-118">Déployez le service dans IIS en utilisant DeployToIIS.Bat dans une invite de commandes avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="6ef8d-118">Deploy the Service in IIS using DeployToIIS.Bat in a command prompt with administrator privileges.</span></span>  
  
7.  <span data-ttu-id="6ef8d-119">Mettez à jour l'adresse de service dans le client en spécifiant http://localhost/XAMLActivation/Service.xamlx et testez à nouveau le service à l'aide de WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="6ef8d-119">Update the service address in the client to http://localhost/XAMLActivation/Service.xamlx and test the service again using WcfTestClient.exe.</span></span>
