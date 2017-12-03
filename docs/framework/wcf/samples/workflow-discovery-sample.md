---
title: Exemple Workflow Discovery
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bba400a4476ffd2589af1d5e7d3e0ca5661102f3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="1348f-102">Exemple Workflow Discovery</span><span class="sxs-lookup"><span data-stu-id="1348f-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="1348f-103">Cet exemple montre comment rendre un service de workflow détectable et comment créer une activité de code personnalisée qui recherche un service particulier.</span><span class="sxs-lookup"><span data-stu-id="1348f-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="1348f-104">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="1348f-104">Demonstrates</span></span>  
 <span data-ttu-id="1348f-105">Activité de recherche de découverte et utilisation de workflow</span><span class="sxs-lookup"><span data-stu-id="1348f-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="1348f-106">Discussion</span><span class="sxs-lookup"><span data-stu-id="1348f-106">Discussion</span></span>  
 <span data-ttu-id="1348f-107">Dans la première partie de l'exemple, un service de workflow est rendu détectable à l'aide de la configuration.</span><span class="sxs-lookup"><span data-stu-id="1348f-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="1348f-108">La configuration peut également être utilisée pour appliquer convenablement le service avec des métadonnées personnalisées (telles que des portées).</span><span class="sxs-lookup"><span data-stu-id="1348f-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="1348f-109">Sur le client, l'exemple utilise une activité de code personnalisée, qui utilise la découverte pour rechercher un service correspondant à un contrat particulier.</span><span class="sxs-lookup"><span data-stu-id="1348f-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="1348f-110">L'activité de code produit un URI, utilisé ultérieurement par une activité d'envoi.</span><span class="sxs-lookup"><span data-stu-id="1348f-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1348f-111">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="1348f-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1348f-112">Cet exemple utilise des points de terminaison HTTP, qui doivent avoir des ACL URL appropriée à exécuter (consultez [configuration de HTTP et HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) pour plus d’informations).</span><span class="sxs-lookup"><span data-stu-id="1348f-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details).</span></span> <span data-ttu-id="1348f-113">L'exécution de la commande suivante à partir d'une invite de commandes avec élévation de privilèges doit ajouter les ACL appropriées.</span><span class="sxs-lookup"><span data-stu-id="1348f-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="1348f-114">Substituez vos domaine et nom d’utilisateur aux arguments suivants si votre interpréteur de commandes ne comprend pas le format variable.</span><span class="sxs-lookup"><span data-stu-id="1348f-114">Substitute your Domain and Username for the following arguments if your shell does not understand the variable format.</span></span>  
  
     <span data-ttu-id="1348f-115">**netsh http ajouter urlacl url = http : / / + : 8000 / utilisateur = domaine %\\%UserName%**</span><span class="sxs-lookup"><span data-stu-id="1348f-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1348f-116">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1348f-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1348f-117">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="1348f-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1348f-118">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1348f-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1348f-119">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="1348f-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
