---
title: Authentification dans WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6fbd4a322153bd9f560b6c039f586100770a0216
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="1a479-102">Authentification dans WCF</span><span class="sxs-lookup"><span data-stu-id="1a479-102">Authentication in WCF</span></span>
<span data-ttu-id="1a479-103">Les rubriques suivantes montrent divers mécanismes dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] qui assurent une authentification, par exemple, l'authentification Windows, les certificats X.509, ainsi que le nom d'utilisateur et des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="1a479-103">The following topics show a number of different mechanisms in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1a479-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1a479-104">In This Section</span></span>  
 [<span data-ttu-id="1a479-105">Comment : utiliser le fournisseur d’appartenances ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1a479-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="1a479-106">Les fonctionnalités ASP.NET incluent une appartenance et un fournisseur de rôles, une base de données pour stocker des paires nom d’utilisateur/mot de passe pour l’authentification et des rôles d’utilisateur pour l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="1a479-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="1a479-107">Cette rubrique explique comment les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent utiliser la même base de données pour authentifier et autoriser des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="1a479-107">This topic explains how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="1a479-108">Comment : utiliser un nom d’utilisateur personnalisé et un programme de validation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="1a479-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="1a479-109">Montre comment intégrer un validateur personnalisé de nom d'utilisateur/mot de passe.</span><span class="sxs-lookup"><span data-stu-id="1a479-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="1a479-110">L’authentification et identité de Service</span><span class="sxs-lookup"><span data-stu-id="1a479-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="1a479-111">En tant qu’une sécurité supplémentaire, un client peut authentifier le service en spécifiant attendu *identité* du service.</span><span class="sxs-lookup"><span data-stu-id="1a479-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="1a479-112">Si l'identité attendue et l'identité retournée par le service ne correspondent pas, l'authentification échoue.</span><span class="sxs-lookup"><span data-stu-id="1a479-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="1a479-113">Délais d’attente et de la négociation de sécurité</span><span class="sxs-lookup"><span data-stu-id="1a479-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="1a479-114">Décrit comment utiliser la propriété <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> de la classe <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>.</span><span class="sxs-lookup"><span data-stu-id="1a479-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="1a479-115">Débogage des erreurs d’authentification Windows</span><span class="sxs-lookup"><span data-stu-id="1a479-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="1a479-116">Traite des problèmes courants rencontrés lors de l'utilisation de l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="1a479-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1a479-117">Référence</span><span class="sxs-lookup"><span data-stu-id="1a479-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="1a479-118">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="1a479-118">Related Sections</span></span>  
 [<span data-ttu-id="1a479-119">Scénarios de sécurité courants</span><span class="sxs-lookup"><span data-stu-id="1a479-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="1a479-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a479-120">See Also</span></span>  
 [<span data-ttu-id="1a479-121">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="1a479-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="1a479-122">Modèle de sécurité pour Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="1a479-122">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
