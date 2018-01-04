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
ms.workload: dotnet
ms.openlocfilehash: 017d3e51022ad9980dc8f058415697c80a2a6b35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="federation-and-issued-tokens"></a><span data-ttu-id="504fb-102">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="504fb-102">Federation and Issued Tokens</span></span>
<span data-ttu-id="504fb-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vous permet de créer des clients qui communiquent de manière sécurisée avec les services qui implémentent les spécifications WS-Federation et WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="504fb-103">With [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], you can create clients that communicate securely with services that implement the WS-Federation and WS-Trust specifications.</span></span> <span data-ttu-id="504fb-104">Ces spécifications utilisent XML, SOAP et WSDL (Web Services Description Language) pour fournir des mécanismes permettant d'activer l'authentification et l'autorisation sur différents domaines de confiance.</span><span class="sxs-lookup"><span data-stu-id="504fb-104">The specifications use XML, SOAP, and Web Services Description Language (WSDL) to provide mechanisms that enable authentication and authorization across different trust realms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="504fb-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="504fb-105">In This Section</span></span>  
 [<span data-ttu-id="504fb-106">Fédération</span><span class="sxs-lookup"><span data-stu-id="504fb-106">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 <span data-ttu-id="504fb-107">Fournit une vue d'ensemble de la fédération.</span><span class="sxs-lookup"><span data-stu-id="504fb-107">Provides an overview of federation.</span></span>  
  
 [<span data-ttu-id="504fb-108">Fédération et confiance</span><span class="sxs-lookup"><span data-stu-id="504fb-108">Federation and Trust</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 <span data-ttu-id="504fb-109">Répertorie les problèmes de conception dont il convient d'être informé lors de la création de services ou de clients fédérés.</span><span class="sxs-lookup"><span data-stu-id="504fb-109">Lists the design issues to be aware of when creating federated services or clients.</span></span>  
  
 [<span data-ttu-id="504fb-110">Guide pratique pour créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="504fb-110">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 <span data-ttu-id="504fb-111">Décrit les concepts de base de la création d'un client fédéré à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="504fb-111">Describes the basics of creating a federated client with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="504fb-112">Guide pratique pour configurer des informations d’identification sur un service FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="504fb-112">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 <span data-ttu-id="504fb-113">Décrit les étapes de création d'un service fédéré.</span><span class="sxs-lookup"><span data-stu-id="504fb-113">Describes the steps of creating a federated service.</span></span>  
  
 [<span data-ttu-id="504fb-114">Guide pratique pour créer une liaison WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="504fb-114">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="504fb-115">Décrit comment configurer des clients et des services qui utilisent `WSFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="504fb-115">Describes how to configure clients and services that use the `WSFederationHttpBinding`.</span></span>  
  
 [<span data-ttu-id="504fb-116">Guide pratique pour créer un service de jeton de sécurité</span><span class="sxs-lookup"><span data-stu-id="504fb-116">How to: Create a Security Token Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 <span data-ttu-id="504fb-117">Décrit les étapes de création d'un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="504fb-117">Describes the steps of creating a security token service.</span></span>  
  
 [<span data-ttu-id="504fb-118">Jetons SAML (Security Assertions Markup Language) et revendications</span><span class="sxs-lookup"><span data-stu-id="504fb-118">Security Assertions Markup Language (SAML) Tokens and Claims</span></span>](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 <span data-ttu-id="504fb-119">Décrit les jetons SAML (Security Assertions Markup Language), qui sont extensibles et vous permettent de créer des types de revendications enrichies.</span><span class="sxs-lookup"><span data-stu-id="504fb-119">Describes Security Assertions Markup Language (SAML) tokens, which are extensible and enable you to create rich claim types.</span></span>  
  
 [<span data-ttu-id="504fb-120">Guide pratique pour configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="504fb-120">How to: Configure a Local Issuer</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 <span data-ttu-id="504fb-121">Décrit comment créer un émetteur local de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="504fb-121">Describes how to create a local issuer of security tokens.</span></span>  
  
 [<span data-ttu-id="504fb-122">Guide pratique pour désactiver des sessions sécurisées sur une classe WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="504fb-122">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="504fb-123">Décrit comment désactiver des sessions sécurisées sur `WSFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="504fb-123">Describes how to disable secure sessions on a `WSFederationHttpBinding`.</span></span> <span data-ttu-id="504fb-124">La désactivation de sessions sécurisées est nécessaire lors de la création d'une batterie de serveurs Web qui requiert une session pour chaque client.</span><span class="sxs-lookup"><span data-stu-id="504fb-124">Disabling secure sessions is necessary when creating a Web farm that requires a session for each client.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="504fb-125">Référence</span><span class="sxs-lookup"><span data-stu-id="504fb-125">Reference</span></span>  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a><span data-ttu-id="504fb-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="504fb-126">See Also</span></span>  
 [<span data-ttu-id="504fb-127">Autorisation</span><span class="sxs-lookup"><span data-stu-id="504fb-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [<span data-ttu-id="504fb-128">Jetons personnalisés</span><span class="sxs-lookup"><span data-stu-id="504fb-128">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 [<span data-ttu-id="504fb-129">Modèle de sécurité pour Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="504fb-129">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
