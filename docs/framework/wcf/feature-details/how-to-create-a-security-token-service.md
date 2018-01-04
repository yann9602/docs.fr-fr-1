---
title: "Comment : créer un service de jeton de sécurité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
caps.latest.revision: "12"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 53ae64af0612cb905a2342491761b1e27ef19c06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-security-token-service"></a><span data-ttu-id="17e1a-102">Comment : créer un service de jeton de sécurité</span><span class="sxs-lookup"><span data-stu-id="17e1a-102">How to: Create a Security Token Service</span></span>
<span data-ttu-id="17e1a-103">Un service de jeton de sécurité implémente le protocole défini dans la spécification WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="17e1a-103">A security token service implements the protocol defined in the WS-Trust specification.</span></span> <span data-ttu-id="17e1a-104">Ce protocole définit des formats de message et des modèles d'échange de message pour émettre, renouveler, annuler et valider des jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="17e1a-104">This protocol defines message formats and message exchange patterns for issuing, renewing, canceling, and validating security tokens.</span></span> <span data-ttu-id="17e1a-105">Un service de jeton de sécurité donné fournit une ou plusieurs de ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="17e1a-105">A given security token service provides one or more of these capabilities.</span></span> <span data-ttu-id="17e1a-106">Cette rubrique examine le scénario le plus courant : l'implémentation de l'émission de jeton.</span><span class="sxs-lookup"><span data-stu-id="17e1a-106">This topic looks at the most common scenario: implementing token issuance.</span></span>  
  
## <a name="issuing-tokens"></a><span data-ttu-id="17e1a-107">Émission de jetons</span><span class="sxs-lookup"><span data-stu-id="17e1a-107">Issuing Tokens</span></span>  
 <span data-ttu-id="17e1a-108">La spécification WS-Trust définit des formats de message, basés sur l'élément de schéma XSD (XML Schema Definition) `RequestSecurityToken` et sur l'élément de schéma XSD `RequestSecurityTokenResponse` pour réaliser une émission de jetons.</span><span class="sxs-lookup"><span data-stu-id="17e1a-108">WS-Trust defines message formats, based on the `RequestSecurityToken` XML Schema definition language (XSD) schema element, and `RequestSecurityTokenResponse` XSD schema element for performing token issuance.</span></span> <span data-ttu-id="17e1a-109">De plus, elle définit les URI (Uniform Resource Identifier) d'action associés.</span><span class="sxs-lookup"><span data-stu-id="17e1a-109">In addition, it defines the associated Action Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="17e1a-110">L'URI d'action associé au message `RequestSecurityToken` est http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue.</span><span class="sxs-lookup"><span data-stu-id="17e1a-110">The action URI associated with the `RequestSecurityToken` message is http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue.</span></span> <span data-ttu-id="17e1a-111">L'URI d'action associé au message `RequestSecurityTokenResponse` est http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue.</span><span class="sxs-lookup"><span data-stu-id="17e1a-111">The action URI associated with the `RequestSecurityTokenResponse` message is   http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue.</span></span>  
  
### <a name="request-message-structure"></a><span data-ttu-id="17e1a-112">Structure d'un message de demande</span><span class="sxs-lookup"><span data-stu-id="17e1a-112">Request Message Structure</span></span>  
 <span data-ttu-id="17e1a-113">La structure d'un message de demande d'émission se compose en général des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="17e1a-113">The issue request message structure typically consists of the following items:</span></span>  
  
-   <span data-ttu-id="17e1a-114">Un URI de type de demande avec une valeur http://schemas.xmlsoap.org/ws/2005/02/trust/Issue.</span><span class="sxs-lookup"><span data-stu-id="17e1a-114">A request type URI with a value of    http://schemas.xmlsoap.org/ws/2005/02/trust/Issue.</span></span>  
  
-   <span data-ttu-id="17e1a-115">Un URI de type de jeton.</span><span class="sxs-lookup"><span data-stu-id="17e1a-115">A token type URI.</span></span> <span data-ttu-id="17e1a-116">Pour les jetons SAML (Security Assertions Markup Language) 1.1, la valeur de cet URI est http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1.</span><span class="sxs-lookup"><span data-stu-id="17e1a-116">For Security Assertions Markup Language (SAML) 1.1 tokens, the value of this URI is http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1.</span></span>  
  
-   <span data-ttu-id="17e1a-117">Une valeur de taille de clé qui indique le nombre de bits inclus dans la clé à associer au jeton émis.</span><span class="sxs-lookup"><span data-stu-id="17e1a-117">A key size value that indicates the number of bits in the key to be associated with the issued token.</span></span>  
  
-   <span data-ttu-id="17e1a-118">Un URI de type de clé.</span><span class="sxs-lookup"><span data-stu-id="17e1a-118">A key type URI.</span></span> <span data-ttu-id="17e1a-119">Pour les clés symétriques, la valeur de cet URI est http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="17e1a-119">For symmetric keys, the value of this URI is http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey.</span></span>  
  
 <span data-ttu-id="17e1a-120">De plus, plusieurs autres éléments peuvent être présents :</span><span class="sxs-lookup"><span data-stu-id="17e1a-120">In addition, a couple of other items might be present:</span></span>  
  
-   <span data-ttu-id="17e1a-121">Le matériel de clé fourni par le client.</span><span class="sxs-lookup"><span data-stu-id="17e1a-121">Key material provided by the client.</span></span>  
  
-   <span data-ttu-id="17e1a-122">Des informations d'étendue qui indiquent avec quel service cible le jeton émis sera utilisé.</span><span class="sxs-lookup"><span data-stu-id="17e1a-122">Scope information that indicates the target service that the issued token will be used with.</span></span>  
  
 <span data-ttu-id="17e1a-123">Le service de jeton de sécurité utilise les informations incluses dans le message de demande d'émission lorsqu'il construit le message de réponse d'émission.</span><span class="sxs-lookup"><span data-stu-id="17e1a-123">The security token service uses the information in the issue request message when it constructs the Issue Response message.</span></span>  
  
## <a name="response-message-structure"></a><span data-ttu-id="17e1a-124">Structure d'un message de réponse</span><span class="sxs-lookup"><span data-stu-id="17e1a-124">Response Message Structure</span></span>  
 <span data-ttu-id="17e1a-125">La structure d'un message de réponse d'émission se compose en général des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="17e1a-125">The issue response message structure typically consists of the following items;</span></span>  
  
-   <span data-ttu-id="17e1a-126">Le jeton de sécurité émis, par exemple, une assertion SAML 1.1.</span><span class="sxs-lookup"><span data-stu-id="17e1a-126">The issued security token, for example, a SAML 1.1 assertion.</span></span>  
  
-   <span data-ttu-id="17e1a-127">Un jeton de preuve associé au jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="17e1a-127">A proof token associated with the security token.</span></span> <span data-ttu-id="17e1a-128">Pour des clés symétriques, il s'agit souvent d'une forme chiffrée du matériel de clé.</span><span class="sxs-lookup"><span data-stu-id="17e1a-128">For symmetric keys, this is often an encrypted form of the key material.</span></span>  
  
-   <span data-ttu-id="17e1a-129">Des références au jeton de sécurité émis.</span><span class="sxs-lookup"><span data-stu-id="17e1a-129">References to the issued security token.</span></span> <span data-ttu-id="17e1a-130">En général, le service de jeton de sécurité retourne une référence qui peut être utilisée lorsque le jeton émis apparaît dans un message ultérieur envoyé par le client et une autre référence qui peut être utilisée lorsque le jeton n'est pas présent dans les messages ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="17e1a-130">Typically, the security token service returns a reference that can be used when the issued token appears in a subsequent message sent by the client and another that can be used when the token is not present in subsequent messages.</span></span>  
  
 <span data-ttu-id="17e1a-131">De plus, plusieurs autres éléments peuvent être présents :</span><span class="sxs-lookup"><span data-stu-id="17e1a-131">In addition, a couple of other items might be present:</span></span>  
  
-   <span data-ttu-id="17e1a-132">Le matériel de clé fourni par le service de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="17e1a-132">Key material provided by the security token service.</span></span>  
  
-   <span data-ttu-id="17e1a-133">L'algorithme requis pour calculer la clé partagée.</span><span class="sxs-lookup"><span data-stu-id="17e1a-133">The algorithm needed to compute the shared key.</span></span>  
  
-   <span data-ttu-id="17e1a-134">Les informations de durée de vie du jeton émis.</span><span class="sxs-lookup"><span data-stu-id="17e1a-134">Lifetime information for the issued token.</span></span>  
  
## <a name="processing-request-messages"></a><span data-ttu-id="17e1a-135">Traitement des messages de demande</span><span class="sxs-lookup"><span data-stu-id="17e1a-135">Processing Request Messages</span></span>  
 <span data-ttu-id="17e1a-136">Le service de jeton de sécurité traite la demande d'émission en examinant les différents éléments du message de demande et en s'assurant qu'il peut émettre un jeton satisfaisant la demande.</span><span class="sxs-lookup"><span data-stu-id="17e1a-136">The security token service processes the issue request by examining the various pieces of the request message and ensuring that it can issue a token that satisfies the request.</span></span> <span data-ttu-id="17e1a-137">Le service de jeton de sécurité doit déterminer les éléments suivants avant de créer le jeton à émettre :</span><span class="sxs-lookup"><span data-stu-id="17e1a-137">The security token service must determine the following before it constructs the token to be issued:</span></span>  
  
-   <span data-ttu-id="17e1a-138">La demande est vraiment une demande d'émission de jeton.</span><span class="sxs-lookup"><span data-stu-id="17e1a-138">The request really is a request for a token to be issued.</span></span>  
  
-   <span data-ttu-id="17e1a-139">Le service de jeton de sécurité prend en charge le type de jeton demandé.</span><span class="sxs-lookup"><span data-stu-id="17e1a-139">The security token service supports the requested token type.</span></span>  
  
-   <span data-ttu-id="17e1a-140">Le demandeur est autorisé à faire la demande.</span><span class="sxs-lookup"><span data-stu-id="17e1a-140">The requester is authorized to make the request.</span></span>  
  
-   <span data-ttu-id="17e1a-141">Le service de jeton de sécurité peut satisfaire les attentes du demandeur en ce qui concerne le matériel de clé.</span><span class="sxs-lookup"><span data-stu-id="17e1a-141">The security token service can meet the requester's expectations with respect to key material.</span></span>  
  
 <span data-ttu-id="17e1a-142">Deux parties essentielles de la construction d'un jeton correspondent à la détermination de la clé utilisée pour signer le jeton et de la clé utilisée pour chiffrer la clé partagée.</span><span class="sxs-lookup"><span data-stu-id="17e1a-142">Two vital parts of constructing a token are determining what key to sign the token with and what key to encrypt the shared key with.</span></span> <span data-ttu-id="17e1a-143">Le jeton doit être signé pour que, lorsque le client présente le jeton au service cible, ce service puisse déterminer que le jeton a été émis par un service de jeton de sécurité qu'il approuve.</span><span class="sxs-lookup"><span data-stu-id="17e1a-143">The token needs to be signed so that when the client presents the token to the target service, that service can determine that the token was issued by a security token service that it trusts.</span></span> <span data-ttu-id="17e1a-144">Le matériel de clé doit être chiffré de telle façon que le service cible puisse le déchiffrer.</span><span class="sxs-lookup"><span data-stu-id="17e1a-144">The key material needs to be encrypted in such a way that the target service can decrypt that key material.</span></span>  
  
 <span data-ttu-id="17e1a-145">La signature d'une assertion SAML implique la création d'une instance <xref:System.IdentityModel.Tokens.SigningCredentials>.</span><span class="sxs-lookup"><span data-stu-id="17e1a-145">Signing a SAML assertion involves creating a <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span></span> <span data-ttu-id="17e1a-146">Le constructeur pour cette classe utilise les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="17e1a-146">The constructor for this class takes the following:</span></span>  
  
-   <span data-ttu-id="17e1a-147">Un <xref:System.IdentityModel.Tokens.SecurityKey> pour la clé à utiliser pour signer l'assertion SAML.</span><span class="sxs-lookup"><span data-stu-id="17e1a-147">A <xref:System.IdentityModel.Tokens.SecurityKey> for the key to use to sign the SAML assertion.</span></span>  
  
-   <span data-ttu-id="17e1a-148">Une chaîne qui identifie l'algorithme de signature à utiliser.</span><span class="sxs-lookup"><span data-stu-id="17e1a-148">A string identifying the signature algorithm to use.</span></span>  
  
-   <span data-ttu-id="17e1a-149">Une chaîne qui identifie l’algorithme de condensat à utiliser.</span><span class="sxs-lookup"><span data-stu-id="17e1a-149">A string identifying the digest algorithm to use.</span></span>  
  
-   <span data-ttu-id="17e1a-150">En option, un <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> qui identifie la clé à utiliser pour signer l'assertion.</span><span class="sxs-lookup"><span data-stu-id="17e1a-150">Optionally, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> that identifies the key to use to sign the assertion.</span></span>  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 <span data-ttu-id="17e1a-151">Le chiffrement de la clé partagée implique le traitement du matériel de clé et son chiffrement avec une clé que le service cible peut utiliser pour déchiffrer la clé partagée.</span><span class="sxs-lookup"><span data-stu-id="17e1a-151">Encrypting the shared key involves taking the key material and encrypting it with a key that the target service can use to decrypt the shared key.</span></span> <span data-ttu-id="17e1a-152">En général, la clé publique du service cible est utilisée.</span><span class="sxs-lookup"><span data-stu-id="17e1a-152">Typically, the public key of the target service is used.</span></span>  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 <span data-ttu-id="17e1a-153">De plus, un objet <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> pour la clé chiffrée est requis.</span><span class="sxs-lookup"><span data-stu-id="17e1a-153">In addition, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> for the encrypted key is needed.</span></span>  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 <span data-ttu-id="17e1a-154">Ensuite, cet objet <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> est utilisé pour créer un `SamlSubject` dans le cadre du `SamlToken`.</span><span class="sxs-lookup"><span data-stu-id="17e1a-154">This <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> is then used to create a `SamlSubject` as part of the `SamlToken`.</span></span>  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="17e1a-155">[Federation, exemple](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="17e1a-155"> [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="creating-response-messages"></a><span data-ttu-id="17e1a-156">Création de messages de réponse</span><span class="sxs-lookup"><span data-stu-id="17e1a-156">Creating Response Messages</span></span>  
 <span data-ttu-id="17e1a-157">Une fois que le service de jeton de sécurité traite la demande d'émission et construit le jeton à émettre avec la clé de vérification, le message de réponse doit être construit, qui inclut au moins le jeton demandé, le jeton de preuve et des références au jeton émis.</span><span class="sxs-lookup"><span data-stu-id="17e1a-157">Once the security token service processes the issue request and constructs the token to be issued along with the proof key, the response message needs to be constructed, including at least the requested token, the proof token, and the issued token references.</span></span> <span data-ttu-id="17e1a-158">Le jeton émis est en général un <xref:System.IdentityModel.Tokens.SamlSecurityToken> créé à partir de <xref:System.IdentityModel.Tokens.SamlAssertion>, comme le montre l'exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="17e1a-158">The issued token is typically a <xref:System.IdentityModel.Tokens.SamlSecurityToken> created from the <xref:System.IdentityModel.Tokens.SamlAssertion>, as shown in the following example.</span></span>  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 <span data-ttu-id="17e1a-159">Dans le cas où le service de jeton de sécurité fournit le matériel de clé partagée, le jeton de preuve est construit en créant un <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="17e1a-159">In the case where the security token service provides the shared key material, the proof token is constructed by creating a <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span></span>  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="17e1a-160">comment construire le jeton de preuve lorsque le client et le jeton de sécurité de service à la fois fournissent du matériel de clé pour la clé partagée, consultez [Federation, exemple](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="17e1a-160"> how to construct the proof token when the client and the security token service both provide key material for the shared key, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
 <span data-ttu-id="17e1a-161">Les références au jeton émis sont construites en créant des instances de la classe <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>.</span><span class="sxs-lookup"><span data-stu-id="17e1a-161">The issued token references are constructed by creating instances of the <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> class.</span></span>  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 <span data-ttu-id="17e1a-162">Ensuite, ces différentes valeurs sont sérialisées dans le message de réponse retourné au client.</span><span class="sxs-lookup"><span data-stu-id="17e1a-162">These various values are then serialized into the response message returned to the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17e1a-163">Exemple</span><span class="sxs-lookup"><span data-stu-id="17e1a-163">Example</span></span>  
 <span data-ttu-id="17e1a-164">Pour le code complet pour un service de jeton de sécurité, consultez [Federation, exemple](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="17e1a-164">For full code for a security token service, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e1a-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17e1a-165">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SigningCredentials>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
 <xref:System.IdentityModel.Tokens.SamlAssertion>  
 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>  
 [<span data-ttu-id="17e1a-166">Exemple de fédération</span><span class="sxs-lookup"><span data-stu-id="17e1a-166">Federation Sample</span></span>](../../../../docs/framework/wcf/samples/federation-sample.md)
