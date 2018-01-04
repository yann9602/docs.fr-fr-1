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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bdfd50253c71bfc9edd737964e771546cb797b9e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="c5e3e-102">Informations d’identification personnalisées et validation d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="c5e3e-102">Custom Credential and Credential Validation</span></span>
<span data-ttu-id="c5e3e-103">La sécurité dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est basée sur l'échange d'informations d'identification entre les services et les clients.</span><span class="sxs-lookup"><span data-stu-id="c5e3e-103">Security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="c5e3e-104">La plupart des besoins en matière de sécurité peuvent être satisfaits à l'aide de types d'informations d'identification communs, tels que Windows (Kerberos), le nom d'utilisateur et les mots de passe et les certificats.</span><span class="sxs-lookup"><span data-stu-id="c5e3e-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="c5e3e-105">Toutefois, si un nouveau type d'informations d'identification est requis, les rubriques de cette section expliquent comment gérer et valider des types nouveaux.</span><span class="sxs-lookup"><span data-stu-id="c5e3e-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5e3e-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c5e3e-106">In This Section</span></span>  
 [<span data-ttu-id="c5e3e-107">Guide pratique pour créer un service qui utilise un validateur de certificat personnalisé</span><span class="sxs-lookup"><span data-stu-id="c5e3e-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="c5e3e-108">Explique comment personnaliser la validation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en héritant de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="c5e3e-108">Explains how to customize [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="c5e3e-109">Procédure pas à pas : création d’informations d’identification de client et de service personnalisées</span><span class="sxs-lookup"><span data-stu-id="c5e3e-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="c5e3e-110">Montre comment étendre le <xref:System.ServiceModel.Description.ClientCredentials> et <xref:System.ServiceModel.Description.ServiceCredentials> pour prendre en charge de nouvelles classes les types d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="c5e3e-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="c5e3e-111">Il s'agit du premier volet d'une série de rubriques qui permettent de créer des types d'informations d'identification personnalisés.</span><span class="sxs-lookup"><span data-stu-id="c5e3e-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="c5e3e-112">Guide pratique pour créer un fournisseur de jetons de sécurité personnalisé</span><span class="sxs-lookup"><span data-stu-id="c5e3e-112">How to: Create a Custom Security Token Provider</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="c5e3e-113">Explique comment créer un fournisseur de jetons de sécurité pour gérer de nouveaux types d'informations d'identification et retourner de nouveaux jetons pour les informations d'authentification.</span><span class="sxs-lookup"><span data-stu-id="c5e3e-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="c5e3e-114">Il s'agit de la deuxième rubrique de la série.</span><span class="sxs-lookup"><span data-stu-id="c5e3e-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="c5e3e-115">Guide pratique pour créer un authentificateur de jetons de sécurité personnalisé</span><span class="sxs-lookup"><span data-stu-id="c5e3e-115">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="c5e3e-116">Explique comment créer un authentificateur personnalisé pour authentifier un nouveau type d'informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="c5e3e-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="c5e3e-117">Il s'agit de la troisième rubrique de la série.</span><span class="sxs-lookup"><span data-stu-id="c5e3e-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c5e3e-118">Référence</span><span class="sxs-lookup"><span data-stu-id="c5e3e-118">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="c5e3e-119">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="c5e3e-119">Related Sections</span></span>  
 [<span data-ttu-id="c5e3e-120">Authentification</span><span class="sxs-lookup"><span data-stu-id="c5e3e-120">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="c5e3e-121">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="c5e3e-121">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="c5e3e-122">Autorisation</span><span class="sxs-lookup"><span data-stu-id="c5e3e-122">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="c5e3e-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5e3e-123">See Also</span></span>  
 [<span data-ttu-id="c5e3e-124">Sécurité</span><span class="sxs-lookup"><span data-stu-id="c5e3e-124">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
