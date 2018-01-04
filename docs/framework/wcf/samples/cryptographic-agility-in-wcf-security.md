---
title: "Agilité de chiffrement dans sécurité WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7d99ada67255d0ced8bbabc2ab6fc645e6ba9e35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="5ff68-102">Agilité de chiffrement dans sécurité WCF</span><span class="sxs-lookup"><span data-stu-id="5ff68-102">Cryptographic Agility in WCF Security</span></span>
<span data-ttu-id="5ff68-103">Cet exemple montre comment effectuer des spécifications dans un algorithme standard ou personnalisé afin de fournir une implémentation de chiffrement agile dans un client et un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5ff68-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service.</span></span> <span data-ttu-id="5ff68-104">Cet exemple est composé des projets suivants :</span><span class="sxs-lookup"><span data-stu-id="5ff68-104">The sample is composed of the following projects:</span></span>  
  
 <span data-ttu-id="5ff68-105">Service</span><span class="sxs-lookup"><span data-stu-id="5ff68-105">Service</span></span>  
 <span data-ttu-id="5ff68-106">Il s’agit d’un auto-hébergé [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service qui implémente le `ICalculator` d’interface et sécurise le point de terminaison à l’aide de la <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> avec la session sécurisée et la session fiable désactivée.</span><span class="sxs-lookup"><span data-stu-id="5ff68-106">This is a self-hosted [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that implements the `ICalculator` interface and secures the endpoint using the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with secure session and reliable session disabled.</span></span> <span data-ttu-id="5ff68-107">Le service définit une classe `SecurityAlgorithmSuite` personnalisée pour spécifier les algorithmes de chiffrement à utiliser pour la sécurité du message.</span><span class="sxs-lookup"><span data-stu-id="5ff68-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
 <span data-ttu-id="5ff68-108">Client</span><span class="sxs-lookup"><span data-stu-id="5ff68-108">Client</span></span>  
 <span data-ttu-id="5ff68-109">Client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui accède au service après une authentification réussie.</span><span class="sxs-lookup"><span data-stu-id="5ff68-109">This is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]client that accesses the service after successful authentication.</span></span> <span data-ttu-id="5ff68-110">Il appelle les opérations exposées par l'interface `ICalculator` et implémentées par le service.</span><span class="sxs-lookup"><span data-stu-id="5ff68-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="5ff68-111">Le client définit également la même classe `SecurityAlgorithmSuite` personnalisée pour spécifier les algorithmes de chiffrement à utiliser pour la sécurité du message.</span><span class="sxs-lookup"><span data-stu-id="5ff68-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="5ff68-112">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="5ff68-112">To use this sample</span></span>  
  
1.  <span data-ttu-id="5ff68-113">Ouvrez la solution CryptoAgility.sln dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5ff68-113">Open the CryptoAgility.sln solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="5ff68-114">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="5ff68-114">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="5ff68-115">Ouvrez [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] , accédez au répertoire \WCF\Basic\Security\CryptoAgility\Service\bin et exécutez le fichier service.exe avec des privilèges d’administrateur en cliquant sur service.exe et en sélectionnant **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="5ff68-115">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="5ff68-116">Accédez au répertoire \WCF\Basic\Security\CryptoAgility\Client\bin et exécutez le fichier client.exe normalement.</span><span class="sxs-lookup"><span data-stu-id="5ff68-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5ff68-117">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5ff68-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5ff68-118">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="5ff68-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5ff68-119">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5ff68-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5ff68-120">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="5ff68-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a><span data-ttu-id="5ff68-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ff68-121">See Also</span></span>  
 [<span data-ttu-id="5ff68-122">Sécurité</span><span class="sxs-lookup"><span data-stu-id="5ff68-122">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
