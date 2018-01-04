---
title: "Fonctionnalités de sécurité avec des liaisons personnalisées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2f26e68b9654ccd565328003596e324558f7505f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="e7898-102">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="e7898-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="e7898-103">Vous pouvez effectuer la plupart des tâches de sécurité courantes en utilisant l’une des liaisons fournies par le système.</span><span class="sxs-lookup"><span data-stu-id="e7898-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="e7898-104">Toutefois, si vous avez besoin de plus de contrôle, vous pouvez créer une liaison personnalisée à l'aide de <xref:System.ServiceModel.Channels.SecurityBindingElement>, comme expliqué dans les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="e7898-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e7898-105">liaisons personnalisées, consultez [des liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="e7898-105"> custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e7898-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e7898-106">In This Section</span></span>  
 [<span data-ttu-id="e7898-107">Modes d’authentification SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e7898-107">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="e7898-108">Décrit les modes d’authentification possibles avec une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="e7898-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="e7898-109">Guide pratique pour créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e7898-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="e7898-110">Décrit les étapes de base pour créer une liaison personnalisée avec un élément de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e7898-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="e7898-111">Guide pratique pour créer un SecurityBindingElement pour un mode d’authentification spécifié</span><span class="sxs-lookup"><span data-stu-id="e7898-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="e7898-112">Décrit comment créer un élément de sécurité pour un mode d'authentification spécifié.</span><span class="sxs-lookup"><span data-stu-id="e7898-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="e7898-113">Guide pratique pour désactiver des sessions sécurisées sur une classe WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e7898-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="e7898-114">Décrit comment désactiver des sessions sécurisées lors de la création d'un service FS.</span><span class="sxs-lookup"><span data-stu-id="e7898-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="e7898-115">Guide pratique pour activer la détection de relecture des messages</span><span class="sxs-lookup"><span data-stu-id="e7898-115">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="e7898-116">Décrit comment déterminer le moment où une attaque par relecture se produit.</span><span class="sxs-lookup"><span data-stu-id="e7898-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="e7898-117">Guide pratique pour créer une information d’identification de prise en charge</span><span class="sxs-lookup"><span data-stu-id="e7898-117">How to: Create a Supporting Credential</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="e7898-118">Décrit comment fournir des informations d'identification de prise en charge à un service, si ce dernier en a besoin.</span><span class="sxs-lookup"><span data-stu-id="e7898-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="e7898-119">Guide pratique pour configurer une confirmation de signature</span><span class="sxs-lookup"><span data-stu-id="e7898-119">How to: Set Up a Signature Confirmation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="e7898-120">Décrit les étapes permettant de confirmer des signatures lors de la signature numérique de messages.</span><span class="sxs-lookup"><span data-stu-id="e7898-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="e7898-121">Guide pratique pour définir une variation d’horloge maximale</span><span class="sxs-lookup"><span data-stu-id="e7898-121">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="e7898-122">Décrit comment définir la différence de temps maximale autorisée entre un service et un client.</span><span class="sxs-lookup"><span data-stu-id="e7898-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="e7898-123">Guide pratique pour désactiver le chiffrement des signatures numériques</span><span class="sxs-lookup"><span data-stu-id="e7898-123">How to: Disable Encryption of Digital Signatures</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="e7898-124">Décrit les avantages de la désactivation du chiffrement des signatures numériques en matière de performances.</span><span class="sxs-lookup"><span data-stu-id="e7898-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e7898-125">Référence</span><span class="sxs-lookup"><span data-stu-id="e7898-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [<span data-ttu-id="e7898-126">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="e7898-126">\<security></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="e7898-127">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="e7898-127">Related Sections</span></span>  
 [<span data-ttu-id="e7898-128">Présentation du niveau de protection</span><span class="sxs-lookup"><span data-stu-id="e7898-128">Understanding Protection Level</span></span>](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [<span data-ttu-id="e7898-129">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="e7898-129">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="e7898-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7898-130">See Also</span></span>  
 [<span data-ttu-id="e7898-131">Liaisons et sécurité</span><span class="sxs-lookup"><span data-stu-id="e7898-131">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [<span data-ttu-id="e7898-132">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="e7898-132">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="e7898-133">Liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="e7898-133">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
