---
title: "Sécurisation des services et des clients"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: ed37992b5488d33b9292bdd54eef47f9eb12f225
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="83ae3-102">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="83ae3-102">Securing Services and Clients</span></span>
<span data-ttu-id="83ae3-103">Les informations présentées dans cette section portent sur la programmation de la sécurité dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83ae3-103">The information in this section focuses on programming security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="83ae3-104">En général, l’opération inclut la sélection d’une liaison appropriée fournie par le système, la définition des propriétés de l’élément de sécurité, puis la définition des propriétés des comportements du service qui déterminent la manière dont les informations d’identification sont récupérées pour être utilisées par le service ou le client.</span><span class="sxs-lookup"><span data-stu-id="83ae3-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="83ae3-105">Ces techniques couvrent les exigences de sécurité de la plupart des utilisateurs pour la plupart des scénarios, comme indiqué dans [des scénarios de sécurité courants](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="83ae3-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="83ae3-106">Si votre scénario requiert plus de fonctionnalités, consultez tout d’abord [fonctionnalités de sécurité avec les liaisons personnalisées](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); si une solution n’est pas visible, consultez [extension de sécurité](../../../../docs/framework/wcf/extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="83ae3-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="83ae3-107">Si vous créez (ou il interagit avec) un système qui utilise des revendications riche, consultez les rubriques de [autorisation](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="83ae3-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83ae3-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="83ae3-108">In This Section</span></span>  
 [<span data-ttu-id="83ae3-109">Programmation de la sécurité WCF</span><span class="sxs-lookup"><span data-stu-id="83ae3-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="83ae3-110">Vue d'ensemble du modèle de programmation utilisé pour sécuriser des messages.</span><span class="sxs-lookup"><span data-stu-id="83ae3-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="83ae3-111">Vue d’ensemble de la sécurité du transport</span><span class="sxs-lookup"><span data-stu-id="83ae3-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="83ae3-112">Vue d'ensemble de la sécurisation des messages par le biais de la couche transport.</span><span class="sxs-lookup"><span data-stu-id="83ae3-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="83ae3-113">Sécurité des messages</span><span class="sxs-lookup"><span data-stu-id="83ae3-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="83ae3-114">Récapitule les raisons d'utiliser la sécurité au niveau du message dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83ae3-114">Summarizes reasons for using message-level security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
 [<span data-ttu-id="83ae3-115">Sessions sécurisées</span><span class="sxs-lookup"><span data-stu-id="83ae3-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="83ae3-116">Examen des éléments à prendre en compte lors de la sécurisation d'une session [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83ae3-116">A discussion of the considerations required when securing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] session.</span></span>  
  
 [<span data-ttu-id="83ae3-117">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="83ae3-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="83ae3-118">Explication de quelques-unes des tâches courantes requises lors de l’utilisation de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="83ae3-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="83ae3-119">Référence</span><span class="sxs-lookup"><span data-stu-id="83ae3-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="83ae3-120">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="83ae3-120">Related Sections</span></span>  
 [<span data-ttu-id="83ae3-121">Concepts de sécurité</span><span class="sxs-lookup"><span data-stu-id="83ae3-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="83ae3-122">Extension de la sécurité</span><span class="sxs-lookup"><span data-stu-id="83ae3-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="83ae3-123">Scénarios de sécurité courants</span><span class="sxs-lookup"><span data-stu-id="83ae3-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="83ae3-124">Liaisons et sécurité</span><span class="sxs-lookup"><span data-stu-id="83ae3-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="83ae3-125">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="83ae3-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="83ae3-126">Extension de la sécurité</span><span class="sxs-lookup"><span data-stu-id="83ae3-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="83ae3-127">Autorisation</span><span class="sxs-lookup"><span data-stu-id="83ae3-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="83ae3-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83ae3-128">See Also</span></span>  
 [<span data-ttu-id="83ae3-129">Programmation WCF de base</span><span class="sxs-lookup"><span data-stu-id="83ae3-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="83ae3-130">Modèle de sécurité pour Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="83ae3-130">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
