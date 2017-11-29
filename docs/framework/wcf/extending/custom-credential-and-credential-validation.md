---
title: "Informations d’identification personnalisées et validation d’informations d’identification"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c3ca7726f3a6a0c5faaab1cbbd0b31125ce0c1d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="e2e94-102">Informations d’identification personnalisées et validation d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="e2e94-102">Custom Credential and Credential Validation</span></span>
<span data-ttu-id="e2e94-103">La sécurité dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est basée sur l'échange d'informations d'identification entre les services et les clients.</span><span class="sxs-lookup"><span data-stu-id="e2e94-103">Security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="e2e94-104">La plupart des besoins en matière de sécurité peuvent être satisfaits à l'aide de types d'informations d'identification communs, tels que Windows (Kerberos), le nom d'utilisateur et les mots de passe et les certificats.</span><span class="sxs-lookup"><span data-stu-id="e2e94-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="e2e94-105">Toutefois, si un nouveau type d'informations d'identification est requis, les rubriques de cette section expliquent comment gérer et valider des types nouveaux.</span><span class="sxs-lookup"><span data-stu-id="e2e94-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2e94-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e2e94-106">In This Section</span></span>  
 [<span data-ttu-id="e2e94-107">Comment : créer un Service qui utilise un validateur de certificat personnalisé</span><span class="sxs-lookup"><span data-stu-id="e2e94-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="e2e94-108">Explique comment personnaliser la validation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en héritant de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="e2e94-108">Explains how to customize [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="e2e94-109">Procédure pas à pas : Création d’un Client personnalisé et informations d’identification de Service</span><span class="sxs-lookup"><span data-stu-id="e2e94-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="e2e94-110">Montre comment étendre le <xref:System.ServiceModel.Description.ClientCredentials> et <xref:System.ServiceModel.Description.ServiceCredentials> pour prendre en charge de nouvelles classes les types d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="e2e94-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="e2e94-111">Il s'agit du premier volet d'une série de rubriques qui permettent de créer des types d'informations d'identification personnalisés.</span><span class="sxs-lookup"><span data-stu-id="e2e94-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="e2e94-112">Comment : créer un fournisseur de jetons de sécurité personnalisé</span><span class="sxs-lookup"><span data-stu-id="e2e94-112">How to: Create a Custom Security Token Provider</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="e2e94-113">Explique comment créer un fournisseur de jetons de sécurité pour gérer de nouveaux types d'informations d'identification et retourner de nouveaux jetons pour les informations d'authentification.</span><span class="sxs-lookup"><span data-stu-id="e2e94-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="e2e94-114">Il s'agit de la deuxième rubrique de la série.</span><span class="sxs-lookup"><span data-stu-id="e2e94-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="e2e94-115">Comment : créer un authentificateur de jeton de sécurité personnalisé</span><span class="sxs-lookup"><span data-stu-id="e2e94-115">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="e2e94-116">Explique comment créer un authentificateur personnalisé pour authentifier un nouveau type d'informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="e2e94-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="e2e94-117">Il s'agit de la troisième rubrique de la série.</span><span class="sxs-lookup"><span data-stu-id="e2e94-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e2e94-118">Référence</span><span class="sxs-lookup"><span data-stu-id="e2e94-118">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="e2e94-119">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="e2e94-119">Related Sections</span></span>  
 [<span data-ttu-id="e2e94-120">Authentification</span><span class="sxs-lookup"><span data-stu-id="e2e94-120">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="e2e94-121">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="e2e94-121">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="e2e94-122">Autorisation</span><span class="sxs-lookup"><span data-stu-id="e2e94-122">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="e2e94-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2e94-123">See Also</span></span>  
 [<span data-ttu-id="e2e94-124">Sécurité</span><span class="sxs-lookup"><span data-stu-id="e2e94-124">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
