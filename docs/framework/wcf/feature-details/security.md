---
title: "Sécurité dans Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
caps.latest.revision: "21"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2f2314c8def27bac9e64685d2af3cdd7639332f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="9b75f-102">Sécurité dans Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9b75f-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="9b75f-103">Les rubriques de cette section décrivent les fonctionnalités de sécurité [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et comment les utiliser pour aider à sécuriser les messages.</span><span class="sxs-lookup"><span data-stu-id="9b75f-103">The topics in this section describe [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] security features and how to use them to help secure messages.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9b75f-104">Windows Server AppFabric et la sécurité, consultez [modèle de sécurité pour Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="9b75f-104"> Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b75f-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9b75f-105">In This Section</span></span>  
 [<span data-ttu-id="9b75f-106">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="9b75f-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="9b75f-107">Décrit les fonctionnalités de sécurité de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b75f-107">Describes the security features in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="9b75f-108">Concepts relatifs à la sécurité</span><span class="sxs-lookup"><span data-stu-id="9b75f-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="9b75f-109">Décrit la terminologie et les concepts de base utilisés dans la sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b75f-109">Describes the basic terminology and concepts used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security.</span></span>  
  
 [<span data-ttu-id="9b75f-110">Scénarios de sécurité courants</span><span class="sxs-lookup"><span data-stu-id="9b75f-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="9b75f-111">Décrit des scénarios et des topologies que vous pouvez configurer avec [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b75f-111">Describes scenarios and topologies you can configure with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="9b75f-112">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="9b75f-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="9b75f-113">Fournit une vue d'ensemble des comportements WCF qui affectent la sécurité, comme la définition des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="9b75f-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="9b75f-114">Liaisons et sécurité</span><span class="sxs-lookup"><span data-stu-id="9b75f-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="9b75f-115">Une vue orientée sécurité des liaisons, y compris des rubriques qui montrent comment créer des liaisons de sécurité personnalisées.</span><span class="sxs-lookup"><span data-stu-id="9b75f-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="9b75f-116">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="9b75f-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="9b75f-117">Décrit comment sécuriser des messages à l'aide des fonctionnalités de sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b75f-117">Describes how to secure messages using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security features.</span></span>  
  
 [<span data-ttu-id="9b75f-118">Authentification</span><span class="sxs-lookup"><span data-stu-id="9b75f-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="9b75f-119">Illustre des tâches d’authentification courantes.</span><span class="sxs-lookup"><span data-stu-id="9b75f-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="9b75f-120">Autorisation</span><span class="sxs-lookup"><span data-stu-id="9b75f-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="9b75f-121">Décrit des scénarios d'autorisation courants avec des implémentations de sécurité.</span><span class="sxs-lookup"><span data-stu-id="9b75f-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="9b75f-122">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="9b75f-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="9b75f-123">Décrit les principes de base de la fédération et comment créer des clients qui communiquent avec des serveurs fédérés.</span><span class="sxs-lookup"><span data-stu-id="9b75f-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="9b75f-124">Confiance partielle</span><span class="sxs-lookup"><span data-stu-id="9b75f-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="9b75f-125">Décrit comment exécuter des scénarios à approbation partielle et certaines limitations de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lors de l'exécution en mode d'approbation partielle.</span><span class="sxs-lookup"><span data-stu-id="9b75f-125">Describes how to run partially-trusted scenarios and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="9b75f-126">Audit</span><span class="sxs-lookup"><span data-stu-id="9b75f-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="9b75f-127">Décrit comment effectuer un audit des événements de sécurité.</span><span class="sxs-lookup"><span data-stu-id="9b75f-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="9b75f-128">Aide sur la sécurité et bonnes pratiques</span><span class="sxs-lookup"><span data-stu-id="9b75f-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="9b75f-129">Instructions pour la création d'applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sécurisées.</span><span class="sxs-lookup"><span data-stu-id="9b75f-129">Guidelines for creating secure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9b75f-130">Référence</span><span class="sxs-lookup"><span data-stu-id="9b75f-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="9b75f-131">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="9b75f-131">Related Sections</span></span>  
 [<span data-ttu-id="9b75f-132">Informations détaillées sur les fonctionnalités de WCF</span><span class="sxs-lookup"><span data-stu-id="9b75f-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="9b75f-133">Programmation WCF de base</span><span class="sxs-lookup"><span data-stu-id="9b75f-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="9b75f-134">Didacticiel Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="9b75f-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="9b75f-135">Vue d’ensemble conceptuelle</span><span class="sxs-lookup"><span data-stu-id="9b75f-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="9b75f-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b75f-136">See Also</span></span>  
 [<span data-ttu-id="9b75f-137">Configuration de votre application</span><span class="sxs-lookup"><span data-stu-id="9b75f-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
