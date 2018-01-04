---
title: Autorisation dans WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac43b2185048287d0edd4cb20561a936bce2f58b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="ac763-102">Autorisation dans WCF</span><span class="sxs-lookup"><span data-stu-id="ac763-102">Authorization in WCF</span></span>
<span data-ttu-id="ac763-103">L'autorisation est le processus qui consiste à contrôler l'accès et les droits aux ressources, telles que les services ou fichiers.</span><span class="sxs-lookup"><span data-stu-id="ac763-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="ac763-104">Les rubriques de cette section vous indiquent comment effectuer cette tâche de base dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] de diverses manières.</span><span class="sxs-lookup"><span data-stu-id="ac763-104">The topics in this section show you how to perform this basic task in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac763-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ac763-105">In This Section</span></span>  
 [<span data-ttu-id="ac763-106">Mécanismes de contrôle d’accès</span><span class="sxs-lookup"><span data-stu-id="ac763-106">Access Control Mechanisms</span></span>](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 <span data-ttu-id="ac763-107">Fournit une présentation des mécanismes d'autorisation dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et des suggestions d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="ac763-107">Provides a brief outline of the authorization mechanisms in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], and suggested uses.</span></span>  
  
 [<span data-ttu-id="ac763-108">Guide pratique pour restreindre l’accès avec la classe PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="ac763-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="ac763-109">Illustre le processus de limitation de l'accès à un service avec le <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ac763-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="ac763-110">Guide pratique pour utiliser le fournisseur de rôle ASP.NET avec un service</span><span class="sxs-lookup"><span data-stu-id="ac763-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="ac763-111">Décrit les différentes étapes de la configuration d'un service pour lui permettre d'utiliser la fonctionnalité de fournisseur de rôle de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac763-111">Walks through the configuration of a service to enable it to use the role provider feature of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span></span>  
  
 [<span data-ttu-id="ac763-112">Guide pratique pour utiliser le fournisseur de rôle du Gestionnaire d’autorisations ASP.NET avec un service</span><span class="sxs-lookup"><span data-stu-id="ac763-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="ac763-113"> peut utiliser le Gestionnaire d'autorisations pour gérer l'autorisation pour un site Web.</span><span class="sxs-lookup"><span data-stu-id="ac763-113"> can use the Authorization Manager to manage authorization for a Web site.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ac763-114"> peut de la même façon tirer parti de la combinaison [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]/Gestionnaire d'autorisations pour l'autorisation des clients.</span><span class="sxs-lookup"><span data-stu-id="ac763-114"> can similarly leverage the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="ac763-115">Gestion des revendications et autorisation avec le modèle d’identité</span><span class="sxs-lookup"><span data-stu-id="ac763-115">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="ac763-116">Explique les principes de base de l'utilisation de l'infrastructure Modèle d'identité pour l'autorisation basée sur les revendications.</span><span class="sxs-lookup"><span data-stu-id="ac763-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="ac763-117">Délégation et emprunt d’identité</span><span class="sxs-lookup"><span data-stu-id="ac763-117">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="ac763-118">Explique la différence entre la délégation et l'emprunt d'identité.</span><span class="sxs-lookup"><span data-stu-id="ac763-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ac763-119">Référence</span><span class="sxs-lookup"><span data-stu-id="ac763-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="ac763-120">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="ac763-120">Related Sections</span></span>  
 [<span data-ttu-id="ac763-121">Authentification</span><span class="sxs-lookup"><span data-stu-id="ac763-121">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="ac763-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac763-122">See Also</span></span>  
 [<span data-ttu-id="ac763-123">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="ac763-123">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="ac763-124">Modèle de sécurité pour Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="ac763-124">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
