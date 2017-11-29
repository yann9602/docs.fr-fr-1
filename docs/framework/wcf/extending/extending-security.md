---
title: "Extension de la sécurité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
caps.latest.revision: "23"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: a3950b156ede806382bbe4e013db5d94a8b20a23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="extending-security"></a><span data-ttu-id="284ed-102">Extension de la sécurité</span><span class="sxs-lookup"><span data-stu-id="284ed-102">Extending Security</span></span>
<span data-ttu-id="284ed-103">Pour vous adapter aux nouveaux types de revendications et jetons personnalisés, vous pouvez étendre l'infrastructure de sécurité de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="284ed-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="284ed-104">Les rubriques de cette section vous montrent comment procéder.</span><span class="sxs-lookup"><span data-stu-id="284ed-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="284ed-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="284ed-105">In This Section</span></span>  
 [<span data-ttu-id="284ed-106">Architecture de sécurité</span><span class="sxs-lookup"><span data-stu-id="284ed-106">Security Architecture</span></span>](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)  
 <span data-ttu-id="284ed-107">Présente en détail l'architecture du système de sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="284ed-107">Walks through the architecture of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security system.</span></span>  
  
 [<span data-ttu-id="284ed-108">Informations d’identification personnalisées et Validation des informations d’identification</span><span class="sxs-lookup"><span data-stu-id="284ed-108">Custom Credential and Credential Validation</span></span>](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 <span data-ttu-id="284ed-109">Explique comment le modèle d'identité est utilisé lors de la validation d'informations d'identification personnalisées.</span><span class="sxs-lookup"><span data-stu-id="284ed-109">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="284ed-110">Jetons personnalisés</span><span class="sxs-lookup"><span data-stu-id="284ed-110">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 <span data-ttu-id="284ed-111">Les jetons émis par un service de jeton de sécurité sont en général des jetons SAML.</span><span class="sxs-lookup"><span data-stu-id="284ed-111">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="284ed-112">Cette rubrique explique comment créer un type de jeton personnalisé.</span><span class="sxs-lookup"><span data-stu-id="284ed-112">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="284ed-113">Autorisation personnalisée</span><span class="sxs-lookup"><span data-stu-id="284ed-113">Custom Authorization</span></span>](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 <span data-ttu-id="284ed-114">Explique comment implémenter une autorisation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="284ed-114">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="284ed-115">Substitution de l’identité d’un Service pour l’authentification</span><span class="sxs-lookup"><span data-stu-id="284ed-115">Overriding the Identity of a Service for Authentication</span></span>](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="284ed-116">Décrit comment remplacer l'identité d'un service pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="284ed-116">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="284ed-117">Comment : créer un vérificateur d’identité Client personnalisés</span><span class="sxs-lookup"><span data-stu-id="284ed-117">How to: Create a Custom Client Identity Verifier</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="284ed-118">Montre comment valider une identité de point de terminaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="284ed-118">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="284ed-119">Comment : utiliser des certificats X.509 distincts pour la signature et chiffrement</span><span class="sxs-lookup"><span data-stu-id="284ed-119">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="284ed-120">Les messages sont généralement signés et chiffrés à l'aide d'un certificat unique.</span><span class="sxs-lookup"><span data-stu-id="284ed-120">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="284ed-121">Cette rubrique explique comment deux certificats peuvent être utilisés, s'ils sont requis.</span><span class="sxs-lookup"><span data-stu-id="284ed-121">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="284ed-122">Comment : modifier le fournisseur de services de chiffrement pour la clé privée d’un certificat X.509</span><span class="sxs-lookup"><span data-stu-id="284ed-122">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="284ed-123">Explique comment modifier le fournisseur de services de chiffrement utilisé pour fournir la clé privée d'un certificat X.509 et comment intégrer ce fournisseur dans l'infrastructure [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="284ed-123">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="284ed-124">Référence</span><span class="sxs-lookup"><span data-stu-id="284ed-124">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="284ed-125">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="284ed-125">Related Sections</span></span>  
 [<span data-ttu-id="284ed-126">Sécurité</span><span class="sxs-lookup"><span data-stu-id="284ed-126">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="284ed-127">Programmation WCF de base</span><span class="sxs-lookup"><span data-stu-id="284ed-127">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="284ed-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="284ed-128">See Also</span></span>  
 [<span data-ttu-id="284ed-129">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="284ed-129">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
