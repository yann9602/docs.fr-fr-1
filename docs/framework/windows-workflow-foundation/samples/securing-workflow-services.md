---
title: "Sécurisation des services de workflow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cd7620186ed51110a32e251d5239c85bb90e0f0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="securing-workflow-services"></a><span data-ttu-id="c5e08-102">Sécurisation des services de workflow</span><span class="sxs-lookup"><span data-stu-id="c5e08-102">Securing Workflow Services</span></span>
<span data-ttu-id="c5e08-103">L'exemple de service de workflow sécurisé présente les procédures suivantes :</span><span class="sxs-lookup"><span data-stu-id="c5e08-103">The Secured Workflow Service sample shows the following procedures:</span></span>  
  
-   <span data-ttu-id="c5e08-104">Création d'un service de workflow de base à l'aide des activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply>.</span><span class="sxs-lookup"><span data-stu-id="c5e08-104">Creating a basic workflow service using the <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
-   <span data-ttu-id="c5e08-105">Utilisation de la configuration [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour définir des points de terminaison sécurisés en vue d'une utilisation par le service de workflow.</span><span class="sxs-lookup"><span data-stu-id="c5e08-105">Using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] configuration to define secure endpoints for use by the workflow service.</span></span>  
  
-   <span data-ttu-id="c5e08-106">Création de revendications à l'intérieure d'une stratégie personnalisée et utilisation de <xref:System.ServiceModel.ServiceAuthorizationManager> pour valider les revendications.</span><span class="sxs-lookup"><span data-stu-id="c5e08-106">Creating claims inside a custom policy and using the <xref:System.ServiceModel.ServiceAuthorizationManager> to validate claims.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c5e08-107">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="c5e08-107">Demonstrates</span></span>  
 <span data-ttu-id="c5e08-108">Utilisation de la sécurité WCF pour sécuriser la communication entre le client et service de workflow. Autorisation basée sur des revendications</span><span class="sxs-lookup"><span data-stu-id="c5e08-108">Using WCF security to secure communication between client and Workflow service, Claims based authorization</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c5e08-109">Discussion</span><span class="sxs-lookup"><span data-stu-id="c5e08-109">Discussion</span></span>  
 <span data-ttu-id="c5e08-110">Cet exemple illustre l'utilisation de l'infrastructure de sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour sécuriser un service de workflow exactement comme vous le feriez avec un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] normal.</span><span class="sxs-lookup"><span data-stu-id="c5e08-110">This sample demonstrates the use of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security infrastructure to secure a workflow service just like you would with a normal [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="c5e08-111">Plus particulièrement, il utilise une revendication personnalisée pour spécifier l'autorisation.</span><span class="sxs-lookup"><span data-stu-id="c5e08-111">Specifically, it uses a custom claim for authorization.</span></span> <span data-ttu-id="c5e08-112">Dans ce cas, il utilise <xref:System.ServiceModel.WSHttpBinding> et la sécurité en mode de message avec les informations d'identification Windows.</span><span class="sxs-lookup"><span data-stu-id="c5e08-112">In this case, it uses <xref:System.ServiceModel.WSHttpBinding> and message mode security with Windows credentials.</span></span>  
  
 <span data-ttu-id="c5e08-113">L'<xref:System.IdentityModel.Policy.IAuthorizationPolicy> personnalisé (`CustomNameCheckerPolicy`) vérifie le nom d'utilisateur Windows du client et recherche un caractère spécifique.</span><span class="sxs-lookup"><span data-stu-id="c5e08-113">The custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) checks the client's Windows username and for a specific character.</span></span> <span data-ttu-id="c5e08-114">Si ce caractère est présent, il crée et ajoute la revendication à <xref:System.IdentityModel.Policy.EvaluationContext>.</span><span class="sxs-lookup"><span data-stu-id="c5e08-114">If that character is present, it creates and adds the claim to the <xref:System.IdentityModel.Policy.EvaluationContext>.</span></span> <span data-ttu-id="c5e08-115">Ainsi, la stratégie personnalisée établit le constat selon lequel le nom d'utilisateur du client contient ce caractère.</span><span class="sxs-lookup"><span data-stu-id="c5e08-115">By doing this, the custom policy is making the statement that the client has this character in the username.</span></span> <span data-ttu-id="c5e08-116">Cette revendication peut être faire l'objet d'une requête pendant toute la durée de vie de l'appel.</span><span class="sxs-lookup"><span data-stu-id="c5e08-116">This claim can be queried throughout the lifetime of the call.</span></span> <span data-ttu-id="c5e08-117">Vous trouverez ce caractère dans `Constants.cs`.</span><span class="sxs-lookup"><span data-stu-id="c5e08-117">You can find that character in `Constants.cs`.</span></span>  
  
 <span data-ttu-id="c5e08-118">La stratégie d'autorisation recherche la revendication à l'intérieur de `SecureWorkFlowAuthZManager`.</span><span class="sxs-lookup"><span data-stu-id="c5e08-118">The authorization policy looks for the claim inside the `SecureWorkFlowAuthZManager`.</span></span> <span data-ttu-id="c5e08-119">Si elle le trouve, elle retourne `true` et autorise le workflow à continuer.</span><span class="sxs-lookup"><span data-stu-id="c5e08-119">If it finds it, it returns `true` and allow the workflow to proceed.</span></span> <span data-ttu-id="c5e08-120">Sinon, elle retourne `false`, ce qui entraîne le retour d'un message 'Accès refusé' au client.</span><span class="sxs-lookup"><span data-stu-id="c5e08-120">Otherwise, it returns `false`, which causes an 'Access Denied' message to be returned to the client.</span></span> <span data-ttu-id="c5e08-121">D'autres revendications sont présentes dans le contexte et peuvent également être examinées à l'intérieur de `SecureWorkFlowAuthZManager`.</span><span class="sxs-lookup"><span data-stu-id="c5e08-121">Other claims are present in the context and can be examined as well inside the `SecureWorkFlowAuthZManager`.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="c5e08-122">Pour exécuter cet exemple</span><span class="sxs-lookup"><span data-stu-id="c5e08-122">To run this sample</span></span>  
  
1.  <span data-ttu-id="c5e08-123">Exécutez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="c5e08-123">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="c5e08-124">Chargez SecuringWorkflowServices.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c5e08-124">Load SecuringWorkflowServices.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="c5e08-125">Pour compiler la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="c5e08-125">Press CTRL+SHIFT+B to compile the solution.</span></span>  
  
4.  <span data-ttu-id="c5e08-126">Définissez le projet Service comme projet de démarrage pour la solution.</span><span class="sxs-lookup"><span data-stu-id="c5e08-126">Set the Service project as the start-up project for the solution.</span></span>  
  
5.  <span data-ttu-id="c5e08-127">Appuyez sur CTRL+F5 pour démarrer le service sans débogage.</span><span class="sxs-lookup"><span data-stu-id="c5e08-127">Press CTRL+F5 to start the service without debugging.</span></span>  
  
6.  <span data-ttu-id="c5e08-128">Définissez le projet Client comme projet de démarrage pour la solution.</span><span class="sxs-lookup"><span data-stu-id="c5e08-128">Set the Client project as the start-up project for the solution.</span></span>  
  
7.  <span data-ttu-id="c5e08-129">Appuyez sur CTRL+F5 pour démarrer le client sans débogage.</span><span class="sxs-lookup"><span data-stu-id="c5e08-129">Press CTRL+F5 to start the client without debugging.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c5e08-130">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c5e08-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c5e08-131">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="c5e08-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c5e08-132">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c5e08-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c5e08-133">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="c5e08-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
