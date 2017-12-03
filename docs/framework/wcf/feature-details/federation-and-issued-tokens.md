---
title: "Fédération et jetons émis"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05a110318bbe92f18d0bc6becb453a5d7851821c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="federation-and-issued-tokens"></a><span data-ttu-id="f83c4-102">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="f83c4-102">Federation and Issued Tokens</span></span>
<span data-ttu-id="f83c4-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vous permet de créer des clients qui communiquent de manière sécurisée avec les services qui implémentent les spécifications WS-Federation et WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="f83c4-103">With [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], you can create clients that communicate securely with services that implement the WS-Federation and WS-Trust specifications.</span></span> <span data-ttu-id="f83c4-104">Ces spécifications utilisent XML, SOAP et WSDL (Web Services Description Language) pour fournir des mécanismes permettant d'activer l'authentification et l'autorisation sur différents domaines de confiance.</span><span class="sxs-lookup"><span data-stu-id="f83c4-104">The specifications use XML, SOAP, and Web Services Description Language (WSDL) to provide mechanisms that enable authentication and authorization across different trust realms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f83c4-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f83c4-105">In This Section</span></span>  
 [<span data-ttu-id="f83c4-106">Fédération</span><span class="sxs-lookup"><span data-stu-id="f83c4-106">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 <span data-ttu-id="f83c4-107">Fournit une vue d'ensemble de la fédération.</span><span class="sxs-lookup"><span data-stu-id="f83c4-107">Provides an overview of federation.</span></span>  
  
 [<span data-ttu-id="f83c4-108">Fédération et confiance</span><span class="sxs-lookup"><span data-stu-id="f83c4-108">Federation and Trust</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 <span data-ttu-id="f83c4-109">Répertorie les problèmes de conception dont il convient d'être informé lors de la création de services ou de clients fédérés.</span><span class="sxs-lookup"><span data-stu-id="f83c4-109">Lists the design issues to be aware of when creating federated services or clients.</span></span>  
  
 [<span data-ttu-id="f83c4-110">Comment : créer un Client fédéré</span><span class="sxs-lookup"><span data-stu-id="f83c4-110">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 <span data-ttu-id="f83c4-111">Décrit les concepts de base de la création d'un client fédéré à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f83c4-111">Describes the basics of creating a federated client with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="f83c4-112">Comment : configurer les informations d’identification sur un Service de fédération</span><span class="sxs-lookup"><span data-stu-id="f83c4-112">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 <span data-ttu-id="f83c4-113">Décrit les étapes de création d'un service fédéré.</span><span class="sxs-lookup"><span data-stu-id="f83c4-113">Describes the steps of creating a federated service.</span></span>  
  
 [<span data-ttu-id="f83c4-114">Comment : créer une liaison WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f83c4-114">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="f83c4-115">Décrit comment configurer des clients et des services qui utilisent `WSFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="f83c4-115">Describes how to configure clients and services that use the `WSFederationHttpBinding`.</span></span>  
  
 [<span data-ttu-id="f83c4-116">Comment : créer un Service de jeton de sécurité</span><span class="sxs-lookup"><span data-stu-id="f83c4-116">How to: Create a Security Token Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 <span data-ttu-id="f83c4-117">Décrit les étapes de création d'un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f83c4-117">Describes the steps of creating a security token service.</span></span>  
  
 [<span data-ttu-id="f83c4-118">Revendications et jetons de sécurité Assertions Markup Language (SAML)</span><span class="sxs-lookup"><span data-stu-id="f83c4-118">Security Assertions Markup Language (SAML) Tokens and Claims</span></span>](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 <span data-ttu-id="f83c4-119">Décrit les jetons SAML (Security Assertions Markup Language), qui sont extensibles et vous permettent de créer des types de revendications enrichies.</span><span class="sxs-lookup"><span data-stu-id="f83c4-119">Describes Security Assertions Markup Language (SAML) tokens, which are extensible and enable you to create rich claim types.</span></span>  
  
 [<span data-ttu-id="f83c4-120">Comment : configurer un émetteur Local</span><span class="sxs-lookup"><span data-stu-id="f83c4-120">How to: Configure a Local Issuer</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 <span data-ttu-id="f83c4-121">Décrit comment créer un émetteur local de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f83c4-121">Describes how to create a local issuer of security tokens.</span></span>  
  
 [<span data-ttu-id="f83c4-122">Comment : désactiver des Sessions sécurisées sur une liaison WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f83c4-122">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="f83c4-123">Décrit comment désactiver des sessions sécurisées sur `WSFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="f83c4-123">Describes how to disable secure sessions on a `WSFederationHttpBinding`.</span></span> <span data-ttu-id="f83c4-124">La désactivation de sessions sécurisées est nécessaire lors de la création d'une batterie de serveurs Web qui requiert une session pour chaque client.</span><span class="sxs-lookup"><span data-stu-id="f83c4-124">Disabling secure sessions is necessary when creating a Web farm that requires a session for each client.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f83c4-125">Référence</span><span class="sxs-lookup"><span data-stu-id="f83c4-125">Reference</span></span>  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a><span data-ttu-id="f83c4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f83c4-126">See Also</span></span>  
 [<span data-ttu-id="f83c4-127">Autorisation</span><span class="sxs-lookup"><span data-stu-id="f83c4-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [<span data-ttu-id="f83c4-128">Jetons personnalisés</span><span class="sxs-lookup"><span data-stu-id="f83c4-128">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 [<span data-ttu-id="f83c4-129">Modèle de sécurité pour Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="f83c4-129">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
