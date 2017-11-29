---
title: "Protocoles de sécurité version 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f40c79ad1a6eedc2b1de4dffa9de5b48aeb8e6f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="f9c1e-102">Protocoles de sécurité version 1.0</span><span class="sxs-lookup"><span data-stu-id="f9c1e-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="f9c1e-103">Les protocoles Web Services Security fournissent des mécanismes de sécurité des services Web qui couvrent l’ensemble des exigences de sécurité de la messagerie de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="f9c1e-104">Cette section décrit dans le détail la version 1.0 de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] (implémentée dans <xref:System.ServiceModel.Channels.SecurityBindingElement>) pour les protocoles de sécurité des services Web suivants.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-104">This section describes the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="f9c1e-105">Spécification/Document</span><span class="sxs-lookup"><span data-stu-id="f9c1e-105">Specification/Document</span></span>|<span data-ttu-id="f9c1e-106">Link</span><span class="sxs-lookup"><span data-stu-id="f9c1e-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="f9c1e-107">WSS : SOAP Message Security 1,0</span><span class="sxs-lookup"><span data-stu-id="f9c1e-107">WSS: SOAP Message Security 1.0</span></span>|<span data-ttu-id="f9c1e-108">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf</span><span class="sxs-lookup"><span data-stu-id="f9c1e-108">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf</span></span>|  
|<span data-ttu-id="f9c1e-109">WSS : Username Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="f9c1e-109">WSS: Username Token Profile 1.0</span></span>|<span data-ttu-id="f9c1e-110">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span><span class="sxs-lookup"><span data-stu-id="f9c1e-110">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="f9c1e-111">WSS : X509 Token Profile 1,0</span><span class="sxs-lookup"><span data-stu-id="f9c1e-111">WSS: X509 Token Profile 1.0</span></span>|<span data-ttu-id="f9c1e-112">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf</span><span class="sxs-lookup"><span data-stu-id="f9c1e-112">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="f9c1e-113">WSS: SAML 1.1 Token Profile 1,0</span><span class="sxs-lookup"><span data-stu-id="f9c1e-113">WSS: SAML 1.1 Token Profile 1.0</span></span>|<span data-ttu-id="f9c1e-114">http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf</span><span class="sxs-lookup"><span data-stu-id="f9c1e-114">http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="f9c1e-115">WSS : SOAP Message Security 1.1</span><span class="sxs-lookup"><span data-stu-id="f9c1e-115">WSS: SOAP Message Security 1.1</span></span>|<span data-ttu-id="f9c1e-116">http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf</span><span class="sxs-lookup"><span data-stu-id="f9c1e-116">http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf</span></span>|  
|<span data-ttu-id="f9c1e-117">WSS Username Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="f9c1e-117">WSS Username Token Profile 1.1</span></span>|<span data-ttu-id="f9c1e-118">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span><span class="sxs-lookup"><span data-stu-id="f9c1e-118">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="f9c1e-119">WSS : X.509 Token Profile 1,1</span><span class="sxs-lookup"><span data-stu-id="f9c1e-119">WSS: X.509 Token Profile 1.1</span></span>|<span data-ttu-id="f9c1e-120">http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf</span><span class="sxs-lookup"><span data-stu-id="f9c1e-120">http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf</span></span>|  
|<span data-ttu-id="f9c1e-121">WSS: Kerberos Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="f9c1e-121">WSS: Kerberos Token Profile 1.1</span></span>|<span data-ttu-id="f9c1e-122">http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf</span><span class="sxs-lookup"><span data-stu-id="f9c1e-122">http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf</span></span>|  
|<span data-ttu-id="f9c1e-123">WSS: SAML 1.1 Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="f9c1e-123">WSS: SAML 1.1 Token Profile 1.1</span></span>|<span data-ttu-id="f9c1e-124">http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf</span><span class="sxs-lookup"><span data-stu-id="f9c1e-124">http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf</span></span>|  
|<span data-ttu-id="f9c1e-125">WS-Secure Conversation</span><span class="sxs-lookup"><span data-stu-id="f9c1e-125">WS-Secure Conversation</span></span>|<span data-ttu-id="f9c1e-126">http://msdn.microsoft.com/ws/2005/02/ws-secure-conversation/</span><span class="sxs-lookup"><span data-stu-id="f9c1e-126">http://msdn.microsoft.com/ws/2005/02/ws-secure-conversation/</span></span>|  
|<span data-ttu-id="f9c1e-127">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="f9c1e-127">WS-Trust</span></span>|<span data-ttu-id="f9c1e-128">http://msdn.microsoft.com/ws/2005/02/ws-trust/</span><span class="sxs-lookup"><span data-stu-id="f9c1e-128">http://msdn.microsoft.com/ws/2005/02/ws-trust/</span></span>|  
|<span data-ttu-id="f9c1e-129">Note d'application :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-129">Application Note:</span></span><br /><br /> <span data-ttu-id="f9c1e-130">Utilisation de WS-Trust pour la négociation TLS</span><span class="sxs-lookup"><span data-stu-id="f9c1e-130">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="f9c1e-131">À publier</span><span class="sxs-lookup"><span data-stu-id="f9c1e-131">To be published</span></span>|  
|<span data-ttu-id="f9c1e-132">Note d'application :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-132">Application Note:</span></span><br /><br /> <span data-ttu-id="f9c1e-133">Utilisation de WS-Trust pour SPNEGO</span><span class="sxs-lookup"><span data-stu-id="f9c1e-133">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="f9c1e-134">À publier</span><span class="sxs-lookup"><span data-stu-id="f9c1e-134">To be published</span></span>|  
|<span data-ttu-id="f9c1e-135">Note d'application :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-135">Application Note:</span></span><br /><br /> <span data-ttu-id="f9c1e-136">Identité et références de point de terminaison Web Services Addressing</span><span class="sxs-lookup"><span data-stu-id="f9c1e-136">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="f9c1e-137">À publier</span><span class="sxs-lookup"><span data-stu-id="f9c1e-137">To be published</span></span>|  
|<span data-ttu-id="f9c1e-138">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="f9c1e-138">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="f9c1e-139">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="f9c1e-139">(2005/07)</span></span>|<span data-ttu-id="f9c1e-140">http://msdn.microsoft.com/ws/2005/07/ws-security-policy/</span><span class="sxs-lookup"><span data-stu-id="f9c1e-140">http://msdn.microsoft.com/ws/2005/07/ws-security-policy/</span></span><br /><br /> <span data-ttu-id="f9c1e-141">tel qu'amendé par les errata soumis au comité technique OASIS WS-SX http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span><span class="sxs-lookup"><span data-stu-id="f9c1e-141">as amended by errata submitted to OASIS WS-SX Technical Committee http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span></span>|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-142"> version 1 fournit 17 modes d'authentification qui peuvent être utilisés comme base pour la configuration de sécurité des services Web.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-142">, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="f9c1e-143">Chaque mode est optimisé pour un jeu commun de spécifications de déploiement, tel que :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-143">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
-   <span data-ttu-id="f9c1e-144">Informations d'identification utilisées pour authentifier le client et le service.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-144">Credentials used to authenticate client and service.</span></span>  
  
-   <span data-ttu-id="f9c1e-145">Mécanismes de protection de la sécurité des messages et du transport.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-145">Message or transport security protection mechanisms.</span></span>  
  
-   <span data-ttu-id="f9c1e-146">Modèles d'échange de messages.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-146">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="f9c1e-147">Mode d'authentification</span><span class="sxs-lookup"><span data-stu-id="f9c1e-147">Authentication Mode</span></span>|<span data-ttu-id="f9c1e-148">Authentification de client</span><span class="sxs-lookup"><span data-stu-id="f9c1e-148">Client Authentication</span></span>|<span data-ttu-id="f9c1e-149">Authentification de serveur</span><span class="sxs-lookup"><span data-stu-id="f9c1e-149">Server Authentication</span></span>|<span data-ttu-id="f9c1e-150">Mode</span><span class="sxs-lookup"><span data-stu-id="f9c1e-150">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="f9c1e-151">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-151">UserNameOverTransport</span></span>|<span data-ttu-id="f9c1e-152">Nom d'utilisateur/mot de passe</span><span class="sxs-lookup"><span data-stu-id="f9c1e-152">User name/password</span></span>|<span data-ttu-id="f9c1e-153">X509</span><span class="sxs-lookup"><span data-stu-id="f9c1e-153">X509</span></span>|<span data-ttu-id="f9c1e-154">Transport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-154">Transport</span></span>|  
|<span data-ttu-id="f9c1e-155">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-155">CertificateOverTransport</span></span>|<span data-ttu-id="f9c1e-156">X509</span><span class="sxs-lookup"><span data-stu-id="f9c1e-156">X509</span></span>|<span data-ttu-id="f9c1e-157">X509</span><span class="sxs-lookup"><span data-stu-id="f9c1e-157">X509</span></span>|<span data-ttu-id="f9c1e-158">Transport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-158">Transport</span></span>|  
|<span data-ttu-id="f9c1e-159">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-159">KerberosOverTransport</span></span>|<span data-ttu-id="f9c1e-160">Windows</span><span class="sxs-lookup"><span data-stu-id="f9c1e-160">Windows</span></span>|<span data-ttu-id="f9c1e-161">X509</span><span class="sxs-lookup"><span data-stu-id="f9c1e-161">X509</span></span>|<span data-ttu-id="f9c1e-162">Transport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-162">Transport</span></span>|  
|<span data-ttu-id="f9c1e-163">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-163">IssuedTokenOverTransport</span></span>|<span data-ttu-id="f9c1e-164">Fédérée</span><span class="sxs-lookup"><span data-stu-id="f9c1e-164">Federated</span></span>|<span data-ttu-id="f9c1e-165">X509</span><span class="sxs-lookup"><span data-stu-id="f9c1e-165">X509</span></span>|<span data-ttu-id="f9c1e-166">Transport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-166">Transport</span></span>|  
|<span data-ttu-id="f9c1e-167">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-167">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="f9c1e-168">Windows Sspi Negotiated</span><span class="sxs-lookup"><span data-stu-id="f9c1e-168">Windows Sspi Negotiated</span></span>|<span data-ttu-id="f9c1e-169">Windows Sspi Negotiated</span><span class="sxs-lookup"><span data-stu-id="f9c1e-169">Windows Sspi Negotiated</span></span>|<span data-ttu-id="f9c1e-170">Transport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-170">Transport</span></span>|  
|<span data-ttu-id="f9c1e-171">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="f9c1e-171">AnonymousForCertificate</span></span>|<span data-ttu-id="f9c1e-172">None</span><span class="sxs-lookup"><span data-stu-id="f9c1e-172">None</span></span>|<span data-ttu-id="f9c1e-173">X509</span><span class="sxs-lookup"><span data-stu-id="f9c1e-173">X509</span></span>|<span data-ttu-id="f9c1e-174">Message</span><span class="sxs-lookup"><span data-stu-id="f9c1e-174">Message</span></span>|  
|<span data-ttu-id="f9c1e-175">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="f9c1e-175">UserNameForCertificate</span></span>|<span data-ttu-id="f9c1e-176">Nom d'utilisateur/mot de passe</span><span class="sxs-lookup"><span data-stu-id="f9c1e-176">User name/password</span></span>|<span data-ttu-id="f9c1e-177">X509</span><span class="sxs-lookup"><span data-stu-id="f9c1e-177">X509</span></span>|<span data-ttu-id="f9c1e-178">Message</span><span class="sxs-lookup"><span data-stu-id="f9c1e-178">Message</span></span>|  
|<span data-ttu-id="f9c1e-179">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="f9c1e-179">MutualCertificate</span></span>|<span data-ttu-id="f9c1e-180">X509</span><span class="sxs-lookup"><span data-stu-id="f9c1e-180">X509</span></span>|<span data-ttu-id="f9c1e-181">X509</span><span class="sxs-lookup"><span data-stu-id="f9c1e-181">X509</span></span>|<span data-ttu-id="f9c1e-182">Message</span><span class="sxs-lookup"><span data-stu-id="f9c1e-182">Message</span></span>|  
|<span data-ttu-id="f9c1e-183">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="f9c1e-183">MutualCertificateDuplex</span></span>|<span data-ttu-id="f9c1e-184">X509</span><span class="sxs-lookup"><span data-stu-id="f9c1e-184">X509</span></span>|<span data-ttu-id="f9c1e-185">X509</span><span class="sxs-lookup"><span data-stu-id="f9c1e-185">X509</span></span>|<span data-ttu-id="f9c1e-186">Message</span><span class="sxs-lookup"><span data-stu-id="f9c1e-186">Message</span></span>|  
|<span data-ttu-id="f9c1e-187">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="f9c1e-187">IssuedTokenForCertificate</span></span>|<span data-ttu-id="f9c1e-188">Fédérée</span><span class="sxs-lookup"><span data-stu-id="f9c1e-188">Federated</span></span>|<span data-ttu-id="f9c1e-189">X509</span><span class="sxs-lookup"><span data-stu-id="f9c1e-189">X509</span></span>|<span data-ttu-id="f9c1e-190">Message</span><span class="sxs-lookup"><span data-stu-id="f9c1e-190">Message</span></span>|  
|<span data-ttu-id="f9c1e-191">Kerberos</span><span class="sxs-lookup"><span data-stu-id="f9c1e-191">Kerberos</span></span>|<span data-ttu-id="f9c1e-192">Windows</span><span class="sxs-lookup"><span data-stu-id="f9c1e-192">Windows</span></span>|<span data-ttu-id="f9c1e-193">Windows</span><span class="sxs-lookup"><span data-stu-id="f9c1e-193">Windows</span></span>|<span data-ttu-id="f9c1e-194">Message</span><span class="sxs-lookup"><span data-stu-id="f9c1e-194">Message</span></span>|  
|<span data-ttu-id="f9c1e-195">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="f9c1e-195">IssuedToken</span></span>|<span data-ttu-id="f9c1e-196">Fédérée</span><span class="sxs-lookup"><span data-stu-id="f9c1e-196">Federated</span></span>|<span data-ttu-id="f9c1e-197">Fédérée</span><span class="sxs-lookup"><span data-stu-id="f9c1e-197">Federated</span></span>|<span data-ttu-id="f9c1e-198">Message</span><span class="sxs-lookup"><span data-stu-id="f9c1e-198">Message</span></span>|  
|<span data-ttu-id="f9c1e-199">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="f9c1e-199">SspiNegotiated</span></span>|<span data-ttu-id="f9c1e-200">Windows Sspi Negotiated</span><span class="sxs-lookup"><span data-stu-id="f9c1e-200">Windows Sspi Negotiated</span></span>|<span data-ttu-id="f9c1e-201">Windows Sspi Negotiated</span><span class="sxs-lookup"><span data-stu-id="f9c1e-201">Windows Sspi Negotiated</span></span>|<span data-ttu-id="f9c1e-202">Message</span><span class="sxs-lookup"><span data-stu-id="f9c1e-202">Message</span></span>|  
|<span data-ttu-id="f9c1e-203">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="f9c1e-203">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="f9c1e-204">None</span><span class="sxs-lookup"><span data-stu-id="f9c1e-204">None</span></span>|<span data-ttu-id="f9c1e-205">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="f9c1e-205">X509, TLS-Nego</span></span>|<span data-ttu-id="f9c1e-206">Message</span><span class="sxs-lookup"><span data-stu-id="f9c1e-206">Message</span></span>|  
|<span data-ttu-id="f9c1e-207">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="f9c1e-207">UserNameForSslNegotiated</span></span>|<span data-ttu-id="f9c1e-208">Nom d'utilisateur/mot de passe</span><span class="sxs-lookup"><span data-stu-id="f9c1e-208">User name/password</span></span>|<span data-ttu-id="f9c1e-209">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="f9c1e-209">X509, TLS-Nego</span></span>|<span data-ttu-id="f9c1e-210">Message</span><span class="sxs-lookup"><span data-stu-id="f9c1e-210">Message</span></span>|  
|<span data-ttu-id="f9c1e-211">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="f9c1e-211">MutualSslNegotiated</span></span>|<span data-ttu-id="f9c1e-212">X509</span><span class="sxs-lookup"><span data-stu-id="f9c1e-212">X509</span></span>|<span data-ttu-id="f9c1e-213">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="f9c1e-213">X509, TLS-Nego</span></span>|<span data-ttu-id="f9c1e-214">Message</span><span class="sxs-lookup"><span data-stu-id="f9c1e-214">Message</span></span>|  
|<span data-ttu-id="f9c1e-215">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="f9c1e-215">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="f9c1e-216">Fédérée</span><span class="sxs-lookup"><span data-stu-id="f9c1e-216">Federated</span></span>|<span data-ttu-id="f9c1e-217">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="f9c1e-217">X509, TLS-Nego</span></span>|<span data-ttu-id="f9c1e-218">Message</span><span class="sxs-lookup"><span data-stu-id="f9c1e-218">Message</span></span>|  
  
 <span data-ttu-id="f9c1e-219">Les points de terminaison qui utilisent des modes d'authentification de ce type peuvent exprimer leurs conditions de sécurité à l'aide de WS-SP (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="f9c1e-219">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="f9c1e-220">Ce document décrit la structure des messages d'infrastructure et d'en-tête de sécurité pour chaque mode d'authentification et fournit des exemples de stratégies et de messages.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-220">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-221"> tire parti de WS-SecureConversation pour assurer la prise en charge des sessions sécurisées afin de protéger les échanges multi-messages entre les applications.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-221"> leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="f9c1e-222">Consultez la section « Sessions sécurisées » ci-après pour plus d'informations sur l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-222">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="f9c1e-223">Outre les modes d'authentification, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit des paramètres pour contrôler les mécanismes de protection courants qui s'appliquent à la plupart des modes d'authentification basés sur la sécurité du message, par exemple : ordre de signature et opérations de chiffrement, suites algorithmiques, dérivation de clé et confirmation de signature.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-223">In addition to authentication modes, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="f9c1e-224">Les préfixes et espaces de noms suivants sont utilisés dans ce document.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-224">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="f9c1e-225">Préfixe</span><span class="sxs-lookup"><span data-stu-id="f9c1e-225">Prefix</span></span>|<span data-ttu-id="f9c1e-226">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="f9c1e-226">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="f9c1e-227">s</span><span class="sxs-lookup"><span data-stu-id="f9c1e-227">s</span></span>|<span data-ttu-id="f9c1e-228">http://www.w3.org/2003/05/soap-envelope</span><span class="sxs-lookup"><span data-stu-id="f9c1e-228">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="f9c1e-229">sp</span><span class="sxs-lookup"><span data-stu-id="f9c1e-229">sp</span></span>|<span data-ttu-id="f9c1e-230">http://schemas.xmlsoap.org/ws/2005/07/securitypolicy</span><span class="sxs-lookup"><span data-stu-id="f9c1e-230">http://schemas.xmlsoap.org/ws/2005/07/securitypolicy</span></span>|  
|<span data-ttu-id="f9c1e-231">a</span><span class="sxs-lookup"><span data-stu-id="f9c1e-231">a</span></span>|<span data-ttu-id="f9c1e-232">http://www.w3.org/2005/08/addressing (page pouvant être en anglais)</span><span class="sxs-lookup"><span data-stu-id="f9c1e-232">http://www.w3.org/2005/08/addressing</span></span>|  
|<span data-ttu-id="f9c1e-233">wsse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-233">wsse</span></span>|<span data-ttu-id="f9c1e-234">TBD - URI OASIS WSS 1,0</span><span class="sxs-lookup"><span data-stu-id="f9c1e-234">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="f9c1e-235">wsse11</span><span class="sxs-lookup"><span data-stu-id="f9c1e-235">wsse11</span></span>|<span data-ttu-id="f9c1e-236">TBD - URI OASIS WSS 1.1</span><span class="sxs-lookup"><span data-stu-id="f9c1e-236">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="f9c1e-237">wsu</span><span class="sxs-lookup"><span data-stu-id="f9c1e-237">wsu</span></span>|<span data-ttu-id="f9c1e-238">TBD - URI OASIS WSS 1.0 Utility</span><span class="sxs-lookup"><span data-stu-id="f9c1e-238">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="f9c1e-239">ds</span><span class="sxs-lookup"><span data-stu-id="f9c1e-239">ds</span></span>|<span data-ttu-id="f9c1e-240">TBD - URI W3C XMLDSig</span><span class="sxs-lookup"><span data-stu-id="f9c1e-240">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="f9c1e-241">wst</span><span class="sxs-lookup"><span data-stu-id="f9c1e-241">wst</span></span>|<span data-ttu-id="f9c1e-242">TBD - URI WS-Trust 2005/02</span><span class="sxs-lookup"><span data-stu-id="f9c1e-242">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="f9c1e-243">wssc</span><span class="sxs-lookup"><span data-stu-id="f9c1e-243">wssc</span></span>|<span data-ttu-id="f9c1e-244">TBD - URI WS-SecureConversation 2005/02</span><span class="sxs-lookup"><span data-stu-id="f9c1e-244">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="f9c1e-245">wsaw</span><span class="sxs-lookup"><span data-stu-id="f9c1e-245">wsaw</span></span>|<span data-ttu-id="f9c1e-246">TBD - espace de noms de stratégie WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="f9c1e-246">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="f9c1e-247">wsp</span><span class="sxs-lookup"><span data-stu-id="f9c1e-247">wsp</span></span>|<span data-ttu-id="f9c1e-248">http://schemas.xmlsoap.org/ws/2004/09/policy</span><span class="sxs-lookup"><span data-stu-id="f9c1e-248">http://schemas.xmlsoap.org/ws/2004/09/policy</span></span>|  
|<span data-ttu-id="f9c1e-249">mssp</span><span class="sxs-lookup"><span data-stu-id="f9c1e-249">mssp</span></span>|<span data-ttu-id="f9c1e-250">http://schemas.microsoft.com/ws/2005/07/securitypolicy</span><span class="sxs-lookup"><span data-stu-id="f9c1e-250">http://schemas.microsoft.com/ws/2005/07/securitypolicy</span></span>|  
  
## <a name="1-token-profiles"></a><span data-ttu-id="f9c1e-251">1. Profils de jeton</span><span class="sxs-lookup"><span data-stu-id="f9c1e-251">1. Token Profiles</span></span>  
 <span data-ttu-id="f9c1e-252">Les spécifications Web Services Security représentent les informations d'identification sous forme de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-252">Web Services Security specifications represent credential as security tokens.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-253"> prend en charge les types de jetons suivants :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-253"> supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="f9c1e-254">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="f9c1e-254">1.1 UsernameToken</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-255"> suit les profils UsernameToken10 et UsernameToken11 avec les contraintes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-255"> follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="f9c1e-256">R1101 - L'attribut PasswordType sur l'élément UsernameToken\Password DOIT être omis ou avoir la valeur #PasswordText (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="f9c1e-256">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="f9c1e-257">Il est possible d'implémenter #PasswordDigest à l'aide de l'extensibilité.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-257">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="f9c1e-258">Il a été observé que #PasswordDigest était souvent considéré à tort comme un mécanisme de protection par mot de passe suffisamment sécurisé.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-258">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="f9c1e-259">Mais #PasswordDigest ne peut pas servir de substitut pour le chiffrement de UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-259">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="f9c1e-260">L'objectif principal de #PasswordDigest est la protection contre des attaques par relecture.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-260">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="f9c1e-261">En modes d'authentification [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les menaces d'attaque par relecture sont atténuées en utilisant des signatures de message.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-261">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="f9c1e-262">B1102 - [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'émet jamais les sous-éléments Nonce et Created de UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-262">B1102 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="f9c1e-263">Ces sous-éléments ont pour but de permettre la détection de relecture.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-263">These sub-elements are intended to help replay detection.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-264"> utilise à la place des signatures de message.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-264"> uses message signatures instead.</span></span>  
  
 <span data-ttu-id="f9c1e-265">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) a introduit la fonctionnalité de dérivation de clé à partir du mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-265">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="f9c1e-266">B1103 - Le mot de passe UsernameToken NE DOIT PAS être utilisé pour la dérivation de clé et, par conséquent, pour les opérations de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-266">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="f9c1e-267">Raisonnement : les mots de passe sont généralement considérés comme trop faibles pour être utilisés dans les opérations de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-267">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="f9c1e-268">1.2 Jeton X509</span><span class="sxs-lookup"><span data-stu-id="f9c1e-268">1.2 X509 Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-269"> traite les certificats X509v3 comme une information d'identification et suit X509TokenProfile1.0 et X509TokenProfile1.1 avec les contraintes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-269"> supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="f9c1e-270">R1201 - L'attribut ValueType sur l'élément BinarySecurityToken doit avoir la valeur #X509v3 lorsqu'il contient un certificat X509v3.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-270">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="f9c1e-271">WSS X509 Token Profile 1.0 et 1.1 définissent également #X509PKIPathv1 et #PKCS7 comme types de valeur.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-271">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-272"> ne prend pas en charge ces types.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-272"> does not support these types.</span></span>  
  
 <span data-ttu-id="f9c1e-273">R1202 - Si une extension SubjectKeyIdentifier (SKI) est présente dans un certificat X509, wsse:KeyIdentifier doit être utilisé pour les références externes au jeton, avec l'attribut ValueType comme #X509SubjectKeyIdentifier et son contenu comme valeur encodée en base 64 de l'extension SKI du certificat.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-273">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="f9c1e-274">Les références SKI sont largement implémentées et s'avèrent être un type de référence externe hautement interopérable.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-274">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="f9c1e-275">R1203 - Une Référence externe au jeton de sécurité X509 NE DOIT PAS utiliser ds:X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-275">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="f9c1e-276">R1204 - Si X509TokenProfile1.1 est utilisé, une référence externe au jeton de sécurité X509 DOIT utiliser l'empreinte numérique introduite par WS-Security 1.1.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-276">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-277"> prend en charge X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-277"> supports X509IssuerSerial.</span></span> <span data-ttu-id="f9c1e-278">Toutefois, X509IssuerSerial pose des problèmes d'interopérabilité : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise une chaîne pour comparer deux valeurs de X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-278">However There are interoperability issues with X509IssuerSerial: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="f9c1e-279">Par conséquent, si l'une réorganise des composants du nom de sujet et envoie à un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] une référence à un certificat, elle est introuvable.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-279">Therefore if one reorders components of the Subject Name and sends to an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="f9c1e-280">1.3 Jeton Kerberos</span><span class="sxs-lookup"><span data-stu-id="f9c1e-280">1.3 Kerberos Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-281"> prend en charge KerberosTokenProfile1.1 à des fins d'authentification Windows avec les contraintes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-281"> supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="f9c1e-282">R1301 - Un jeton Kerberos doit contenir la valeur d'un AP_REQ Kerberos v4 encapsulé GSS tel que défini dans GSS_API et la spécification Kerberos, et l'attribut ValueType doit avoir la valeur #GSS_Kerberosv5_AP_REQ.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-282">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-283"> utilise un AP-REQ Kerberos encapsulé GSS, et non pas un AP-REQ nu.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-283"> uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="f9c1e-284">Il s'agit d'une méthode conseillée en matière de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-284">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="f9c1e-285">1.4 Jeton SAML v1.1</span><span class="sxs-lookup"><span data-stu-id="f9c1e-285">1.4 SAML v1.1 Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-286"> prend en charge les profils de jeton WSS SAML 1.0 et 1.1 des jetons SAML v1.1.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-286"> supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="f9c1e-287">Il est possible d'implémenter d'autres versions de formats de jeton SAML.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-287">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="f9c1e-288">1.5 Jeton de contexte de sécurité</span><span class="sxs-lookup"><span data-stu-id="f9c1e-288">1.5 Security Context Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-289"> prend en charge le jeton de contexte de sécurité (SCT) introduit dans WS-SecureCoversation.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-289"> supports the Security Context Token (SCT) introduced in WS-SecureCoversation.</span></span> <span data-ttu-id="f9c1e-290">Le SCT est utilisé pour représenter un contexte de sécurité établi dans SecureConversation ainsi que les protocoles de négociation binaire TLS et SSPI, tel que décrit ci-après.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-290">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="f9c1e-291">2. Paramètres de sécurité de message courants</span><span class="sxs-lookup"><span data-stu-id="f9c1e-291">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="f9c1e-292">2.1 TimeStamp</span><span class="sxs-lookup"><span data-stu-id="f9c1e-292">2.1 TimeStamp</span></span>  
 <span data-ttu-id="f9c1e-293">La présence de l'horodatage est contrôlée à l'aide de la propriété <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> de la classe <xref:System.ServiceModel.Channels.SecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="f9c1e-293">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-294"> sérialise systématiquement wsse:TimeStamp avec les champs wsse:Created et wsse:Expires.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-294"> always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="f9c1e-295">wsse:TimeStamp est systématiquement signé en cas de signature.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-295">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="f9c1e-296">2.2 Ordre de protection</span><span class="sxs-lookup"><span data-stu-id="f9c1e-296">2.2 Protection Order</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-297"> prend en charge l'ordre de protection de message « Sign Before Encrypt » et « Encrypt Before Sign » (Security Policy 1.1).</span><span class="sxs-lookup"><span data-stu-id="f9c1e-297"> supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="f9c1e-298">« Sign Before Encrypt » est recommandé dans les cas suivants : les messages protégés à l'aide de Encrypt Before Sign sont ouverts aux attaques par substitution de signature, sauf si le mécanisme WS-Security 1.1 SignatureConfirmation est utilisé et qu'une signature sur contenu chiffré rend l'audit plus difficile.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-298">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="f9c1e-299">2.3 Protection de la signature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-299">2.3 Signature Protection</span></span>  
 <span data-ttu-id="f9c1e-300">Lorsque Encrypt Before Sign est utilisé, il est recommandé de protéger la signature afin d'empêcher les attaques par force brute de découvrir le contenu chiffré ou la clé de signature (en particulier lorsqu'un jeton personnalisé est utilisé avec du matériel de clé faible).</span><span class="sxs-lookup"><span data-stu-id="f9c1e-300">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="f9c1e-301">2.4 Suite algorithmique</span><span class="sxs-lookup"><span data-stu-id="f9c1e-301">2.4 Algorithm Suite</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-302"> prend en charge toutes les suites algorithmiques répertoriées dans Security Policy 1.1.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-302"> supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="f9c1e-303">2.5 Dérivation de clé</span><span class="sxs-lookup"><span data-stu-id="f9c1e-303">2.5 Key Derivation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-304"> utilise la « dérivation de clé pour clés symétriques », tel que décrit dans WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-304"> uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="f9c1e-305">2.6 Confirmation de signature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-305">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="f9c1e-306">La confirmation de signature peut se résumer à la protection contre les attaques de type « homme du milieu » afin de protéger le jeu de signatures.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-306">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="f9c1e-307">2.7 Disposition de l'en-tête de sécurité</span><span class="sxs-lookup"><span data-stu-id="f9c1e-307">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="f9c1e-308">Chaque mode d'authentification décrit une certaine disposition de l'en-tête de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-308">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="f9c1e-309">Ses éléments sont semi-organisés.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-309">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="f9c1e-310">Pour définir l'ordre des éléments enfants, WS-Security Policy définit les modes de disposition suivants :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-310">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f9c1e-311">Strict</span><span class="sxs-lookup"><span data-stu-id="f9c1e-311">Strict</span></span>|<span data-ttu-id="f9c1e-312">Les éléments sont ajoutés à l'en-tête de sécurité selon les règles de disposition numérotée décrites dans Stratégie de sécurité à la section 7.7.1 conformément à un principe général de « déclaration avant utilisation ».</span><span class="sxs-lookup"><span data-stu-id="f9c1e-312">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="f9c1e-313">Lax</span><span class="sxs-lookup"><span data-stu-id="f9c1e-313">Lax</span></span>|<span data-ttu-id="f9c1e-314">Les éléments sont ajoutés à l'en-tête de sécurité dans n'importe quel ordre conforme à WSS: SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-314">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="f9c1e-315">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="f9c1e-315">LaxTimestampFirst</span></span>|<span data-ttu-id="f9c1e-316">Identique à Lax, excepté que le premier élément dans l'en-tête de sécurité doit être un wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="f9c1e-316">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="f9c1e-317">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="f9c1e-317">LaxTimestampLast</span></span>|<span data-ttu-id="f9c1e-318">Identique à Lax, excepté que le dernier élément dans l'en-tête de sécurité doit être un wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="f9c1e-318">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-319"> prend en charge l'ensemble des quatre modes de disposition d'en-tête de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-319"> supports all four modes for security header layout.</span></span> <span data-ttu-id="f9c1e-320">Les exemples de message et de structure d'en-tête de sécurité fournis pour les modes d'authentification ci-après suivent le mode « Strict ».</span><span class="sxs-lookup"><span data-stu-id="f9c1e-320">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="f9c1e-321">2. Paramètres de sécurité de message courants</span><span class="sxs-lookup"><span data-stu-id="f9c1e-321">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="f9c1e-322">Cette section fournit des exemples de stratégie pour chaque mode d'authentification ainsi que des exemples qui présentent la structure d'entête de sécurité dans les messages échangés par le client et le service.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-322">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="f9c1e-323">6.1 Protection du transport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-323">6.1 Transport Protection</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9c1e-324"> fournit cinq modes d'authentification qui utilisent le transport sécurisé pour protéger les messages : UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport et SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-324"> provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="f9c1e-325">Ces modes d'authentification sont construits à l'aide de la liaison de transport décrite dans SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-325">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="f9c1e-326">Pour le mode d'authentification UserNameOverTransport, UsernameToken est un jeton de prise en charge signé.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-326">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="f9c1e-327">Pour les autres modes d'authentification, le jeton apparaît sous forme d'un jeton d'endossement signé.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-327">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="f9c1e-328">Les annexes C.1.2 et C.1.3 de SecurityPolicy décrivent en détail la disposition de l'en-tête de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-328">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="f9c1e-329">Les exemples suivants affichent la disposition Strict pour un mode d'authentification donné.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-329">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="f9c1e-330">La valeur de la propriété « Derived Keys » pour les jetons est dans tous les cas « false ».</span><span class="sxs-lookup"><span data-stu-id="f9c1e-330">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="f9c1e-331">Les valeurs des diverses propriétés de la liaison de transport sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-331">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="f9c1e-332">Horodateur : true</span><span class="sxs-lookup"><span data-stu-id="f9c1e-332">Timestamp: true</span></span>  
  
 <span data-ttu-id="f9c1e-333">Disposition de l'en-tête de sécurité : Strict</span><span class="sxs-lookup"><span data-stu-id="f9c1e-333">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="f9c1e-334">Suite algorithmique : Basic256</span><span class="sxs-lookup"><span data-stu-id="f9c1e-334">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="f9c1e-335">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-335">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="f9c1e-336">Avec ce mode d'authentification, le client s'authentifie à l'aide d'un jeton de nom d'utilisateur qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge signé qui est systématiquement envoyé de l'initiateur au destinataire.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-336">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="f9c1e-337">Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="f9c1e-338">La liaison utilisée est une liaison de transport.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-338">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="f9c1e-339">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-339">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='UsernameOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:SignedSupportingTokens >  
        <wsp:Policy>  
          <sp:UsernameToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:WssUsernameToken10 />   
            </wsp:Policy>  
          </sp:UsernameToken>  
        </wsp:Policy>  
      </sp:SignedSupportingTokens>  
      <sp:Wss11 >  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10 >  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="f9c1e-340">Disposition de l'en-tête de sécurité</span><span class="sxs-lookup"><span data-stu-id="f9c1e-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="f9c1e-341">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-341">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken ... >  
  ...  
  </wsse:UsernameToken>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-342">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="f9c1e-343">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-343">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="f9c1e-344">Avec ce mode d'authentification, le client s'authentifie à l'aide d'un certificat X.509 qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement qui est systématiquement envoyé de l'initiateur au destinataire.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-344">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="f9c1e-345">Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-345">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="f9c1e-346">La liaison utilisée est une liaison de transport.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-346">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="f9c1e-347">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-347">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CertificateOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding xmlns:sp='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy' >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
             <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:RequireThumbprintReference />   
              <sp:WssX509V3Token10 />   
            </wsp:Policy>  
          </sp:X509Token>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="f9c1e-348">Disposition de l'en-tête de sécurité</span><span class="sxs-lookup"><span data-stu-id="f9c1e-348">Security Header Layout</span></span>  
  
 <span data-ttu-id="f9c1e-349">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-349">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wse:Timestamp u:Id="_0">  
  ...  
  </wse:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-350">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-350">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="f9c1e-351">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-351">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="f9c1e-352">Avec ce mode d'authentification, le client ne s'authentifie pas auprès du service, en tant que tel, mais présente à la place un jeton émis par un service d'émission de jeton de sécurité (STS) et prouve qu'il connaît une clé partagée.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-352">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="f9c1e-353">Le jeton émis apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement qui est systématiquement envoyé de l'initiateur au destinataire.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-353">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="f9c1e-354">Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-354">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="f9c1e-355">La liaison utilisée est une liaison de transport.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-355">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="f9c1e-356">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-356">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='IssuedTokenOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:IssuedToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <sp:RequestSecurityTokenTemplate>  
              <wst:KeyType>  
              http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
              </wst:KeyType>   
            </sp:RequestSecurityTokenTemplate>  
            <wsp:Policy>  
              <sp:RequireInternalReference />   
            </wsp:Policy>  
          </sp:IssuedToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="f9c1e-357">Disposition de l'en-tête de sécurité</span><span class="sxs-lookup"><span data-stu-id="f9c1e-357">Security Header Layout</span></span>  
  
 <span data-ttu-id="f9c1e-358">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-358">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion ...>  
  ...  
  </saml:Assertion>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-359">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-359">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="f9c1e-360">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-360">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="f9c1e-361">Avec ce mode d'authentification, le client s'authentifie auprès du service à l'aide d'un ticket Kerberos.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-361">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="f9c1e-362">Le jeton Kerberos apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-362">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="f9c1e-363">Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-363">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="f9c1e-364">La liaison utilisée est une liaison de transport.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-364">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="f9c1e-365">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-365">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='KerberosOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:KerberosToken  
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
            <wsp:Policy>  
              <sp:WssGssKerberosV5ApReqToken11 />   
            </wsp:Policy>  
          </sp:KerberosToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="f9c1e-366">Disposition de l'en-tête de sécurité</span><span class="sxs-lookup"><span data-stu-id="f9c1e-366">Security Header Layout</span></span>  
  
 <span data-ttu-id="f9c1e-367">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-367">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken ValueType="...#GSS_Kerberosv5_AP_REQ">  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-368">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-368">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="f9c1e-369">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="f9c1e-369">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="f9c1e-370">Avec ce mode, un protocole de négociation est utilisé pour effectuer l'authentification du client et du serveur.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-370">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="f9c1e-371">Le protocole Kerberos est dans la mesure du possible utilisé, sinon c'est NTLM.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-371">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="f9c1e-372">Le SCT résultant apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement qui est systématiquement envoyé de l'initiateur au destinataire.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-372">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="f9c1e-373">Le service est en outre authentifié au niveau de la couche de transport par un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-373">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="f9c1e-374">La liaison utilisée est une liaison de transport.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-374">The binding used is a transport binding.</span></span> <span data-ttu-id="f9c1e-375">"SPNEGO" (négociation) décrit comment [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise le protocole de négociation binaire SSPI avec WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-375">"SPNEGO" (negotiation) describes how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="f9c1e-376">Les exemples d'en-tête de sécurité présentés dans cette section supposent que le SCT a déjà été établi via la négociation SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-376">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="f9c1e-377">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-377">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SspiNegotiatedOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:SpnegoContextToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy />   
          </sp:SpnegoContextToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples"></a><span data-ttu-id="f9c1e-378">Exemples d'en-tête de sécurité</span><span class="sxs-lookup"><span data-stu-id="f9c1e-378">Security Header Examples</span></span>  
 <span data-ttu-id="f9c1e-379">Une fois que le jeton de contexte de sécurité est établi via la négociation SPNEGO à l'aide de WS-Trust Binary Negotiation, les messages d'application ont des en-têtes de sécurité présentant la structure suivante.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-379">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="f9c1e-380">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-380">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:SecurityContextToken u:Id="uuid-2202746a-7725-453d-8747-809cb718dab0-29" >  
  ...  
  </wssc:SecurityContextToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-381">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-381">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="f9c1e-382">6.2 Utilisation des certificats X.509 pour l'authentification de service</span><span class="sxs-lookup"><span data-stu-id="f9c1e-382">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="f9c1e-383">Cette section décrit les modes d'authentification suivants : MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate et IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-383">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="f9c1e-384">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="f9c1e-384">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="f9c1e-385">Avec ce mode d'authentification, le client s'authentifie à l'aide d'un certificat X.509 qui apparaît au niveau de la couche SOAP sous forme de jeton d'initiateur.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="f9c1e-386">Le service est également authentifié à l'aide d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="f9c1e-387">La liaison utilisée est une liaison asymétrique avec les valeurs de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="f9c1e-388">Jeton d'initiateur : certificat X.509 du client, avec mode d'inclusion défini à …/IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="f9c1e-388">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="f9c1e-389">Jeton de destinataire : certificat X.509 du serveur, avec mode d'inclusion défini à …/IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="f9c1e-389">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="f9c1e-390">Jeton de protection : False</span><span class="sxs-lookup"><span data-stu-id="f9c1e-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="f9c1e-391">Signatures du corps et de l'intégralité de l'en-tête : True</span><span class="sxs-lookup"><span data-stu-id="f9c1e-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="f9c1e-392">Ordre de protection : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="f9c1e-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="f9c1e-393">Chiffrement de la signature : True</span><span class="sxs-lookup"><span data-stu-id="f9c1e-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="f9c1e-394">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-394">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificate_WSS10_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="f9c1e-395">Exemples d'en-tête de sécurité : SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="f9c1e-396">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-396">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-397">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-397">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-398">Exemples d'en-tête de sécurité : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="f9c1e-398">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="f9c1e-399">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-399">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-400">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-400">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="f9c1e-401">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="f9c1e-401">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="f9c1e-402">Avec ce mode d'authentification, le client s'authentifie à l'aide d'un certificat X.509 qui apparaît au niveau de la couche SOAP sous forme de jeton d'initiateur.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-402">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="f9c1e-403">Le service est également authentifié à l'aide d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-403">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="f9c1e-404">La liaison utilisée est une liaison asymétrique avec les valeurs de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-404">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="f9c1e-405">Jeton d'initiateur : certificat X509 du client, avec mode d'inclusion défini à …/IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="f9c1e-405">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="f9c1e-406">Jeton de destinataire : certificat X509 du serveur, avec mode d'inclusion défini à …/IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="f9c1e-406">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="f9c1e-407">Jeton de protection : False</span><span class="sxs-lookup"><span data-stu-id="f9c1e-407">Token Protection: False</span></span>  
  
 <span data-ttu-id="f9c1e-408">Signatures du corps et de l'intégralité de l'en-tête : True</span><span class="sxs-lookup"><span data-stu-id="f9c1e-408">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="f9c1e-409">Ordre de protection : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="f9c1e-409">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="f9c1e-410">Chiffrement de la signature : True</span><span class="sxs-lookup"><span data-stu-id="f9c1e-410">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="f9c1e-411">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-411">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificateDuplex_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToInitiator' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="f9c1e-412">Exemples d'en-tête de sécurité : SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-412">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="f9c1e-413">Demande et réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-413">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="f9c1e-414">Exemples d'en-tête de sécurité : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="f9c1e-414">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="f9c1e-415">Demande et réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-415">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="f9c1e-416">6.2.3 Utilisation de SymmetricBinding avec l'authentification de service X.509</span><span class="sxs-lookup"><span data-stu-id="f9c1e-416">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="f9c1e-417">« WSS10 » a fourni un support limité aux scénarios avec jetons X509.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-417">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="f9c1e-418">Par exemple, il n'était pas possible d'assurer la protection des signatures et du chiffrement des messages qui utilisent uniquement le jeton X509 du service.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-418">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="f9c1e-419">« WSS11 » a introduit l'utilisation de EncryptedKey sous forme d'un jeton symétrique.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-419">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="f9c1e-420">Une clé temporaire chiffrée pour le certificat X.509 du service peut maintenant être utilisée à la fois pour la protection des messages de demande et de réponse.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-420">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="f9c1e-421">Les modes d'authentification décrits dans la section 6.4 ci-après utilisent ce modèle.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-421">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="f9c1e-422">WS-SecurityPolicy décrit ce modèle à l'aide de SymmetricBinding avec le jeton X509 du service sous forme de jeton de protection.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-422">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="f9c1e-423">Les modes d'authentification AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 et IssuedTokenForCertificate utilisent tous une instance similaire de sp:SymmetricBinding avec les valeurs de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-423">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="f9c1e-424">Jeton de protection : certificat X509 du serveur, avec mode d'inclusion défini à .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="f9c1e-424">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="f9c1e-425">Jeton de protection : False</span><span class="sxs-lookup"><span data-stu-id="f9c1e-425">Token Protection: False</span></span>  
  
 <span data-ttu-id="f9c1e-426">Signatures du corps et de l'intégralité de l'en-tête : True</span><span class="sxs-lookup"><span data-stu-id="f9c1e-426">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="f9c1e-427">Ordre de protection : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="f9c1e-427">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="f9c1e-428">Chiffrement de la signature : True</span><span class="sxs-lookup"><span data-stu-id="f9c1e-428">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="f9c1e-429">Les modes d'authentification précédemment cités diffèrent uniquement par les jetons de prise en charge qu'ils utilisent.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-429">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="f9c1e-430">AnonymousForCertificate n'a pas de jeton de prise en charge, MutualCertificate WSS 1.1 a le certificat X509 du client comme jeton de prise en charge d'endossement, UserNameForCertificate a un jeton de nom d'utilisateur comme jeton de prise en charge signé, et IssuedTokenForCertificate a le jeton émis sous forme d'un jeton de prise en charge d'endossement.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-430">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="f9c1e-431">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-431">Policy</span></span>  
  
 <span data-ttu-id="f9c1e-432">Liaison symétrique</span><span class="sxs-lookup"><span data-stu-id="f9c1e-432">Symmetric Binding</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SymmetricCert_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireThumbprintReference />   
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />  
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting Token Assertions appear here -->  
      ...  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
          <sp:RequireSignatureConfirmation />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="f9c1e-433">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="f9c1e-433">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="f9c1e-434">Avec ce mode d'authentification, le client est anonyme et le service est authentifié à l'aide d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-434">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="f9c1e-435">La liaison utilisée est une instance de liaison symétrique, tel que décrit à la section 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-435">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="f9c1e-436">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-436">Policy</span></span>  
  
 <span data-ttu-id="f9c1e-437">Consultez « Stratégie » à la section 6.2.3 ci-dessus pour plus d'informations sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-437">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="f9c1e-438">Exemples d'en-tête de sécurité : SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-438">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="f9c1e-439">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-439">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-440">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-440">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="f9c1e-441">Exemples d'en-tête de sécurité : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="f9c1e-441">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="f9c1e-442">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-442">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-443">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-443">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="f9c1e-444">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="f9c1e-444">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="f9c1e-445">Avec ce mode d'authentification, le client s'authentifie auprès du service à l'aide d'un jeton de nom d'utilisateur qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge signé.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-445">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="f9c1e-446">Le service s'authentifie auprès du client à l'aide d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-446">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="f9c1e-447">La liaison utilisée est une liaison symétrique, le jeton de protection étant une clé générée par le client, chiffrée avec la clé publique du service.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-447">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="f9c1e-448">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-448">Policy</span></span>  
  
 <span data-ttu-id="f9c1e-449">Consultez « Stratégie » à la section 6.2.3 ci-dessus pour plus d'informations sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-449">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="f9c1e-450">Jeton de prise en charge signé</span><span class="sxs-lookup"><span data-stu-id="f9c1e-450">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="f9c1e-451">Exemples d'en-tête de sécurité : SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-451">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="f9c1e-452">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-452">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-453">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-453">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="f9c1e-454">Exemples d'en-tête de sécurité : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="f9c1e-454">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="f9c1e-455">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-455">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-456">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-456">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="f9c1e-457">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="f9c1e-457">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="f9c1e-458">Avec ce mode d'authentification, le client s'authentifie à l'aide d'un certificat X.509 qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-458">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="f9c1e-459">Le service est également authentifié à l'aide d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-459">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="f9c1e-460">La liaison utilisée est une liaison symétrique, le jeton de protection étant une clé générée par le client, chiffrée avec la clé publique du service.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-460">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="f9c1e-461">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-461">Policy</span></span>  
  
 <span data-ttu-id="f9c1e-462">Consultez « Stratégie » à la section 6.2.3 ci-dessus pour plus d'informations sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-462">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="f9c1e-463">Jeton de prise en charge d'endossement</span><span class="sxs-lookup"><span data-stu-id="f9c1e-463">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="f9c1e-464">Exemples d'en-tête de sécurité : SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-464">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="f9c1e-465">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-465">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-466">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-466">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="f9c1e-467">Exemples d'en-tête de sécurité : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="f9c1e-467">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="f9c1e-468">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-468">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-469">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-469">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="f9c1e-470">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="f9c1e-470">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="f9c1e-471">Avec ce mode d'authentification, le client ne s'authentifie pas auprès du service, en tant que tel, mais présente à la place un jeton émis par un STS et prouve qu'il connaît une clé partagée.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-471">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="f9c1e-472">Le jeton émis apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-472">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="f9c1e-473">Le service s'authentifie auprès du client à l'aide d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-473">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="f9c1e-474">La liaison utilisée est une liaison symétrique, le jeton de protection étant une clé générée par le client, chiffrée avec la clé publique du service.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-474">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="f9c1e-475">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-475">Policy</span></span>  
  
 <span data-ttu-id="f9c1e-476">Consultez « Stratégie » à la section 6.2.3 ci-dessus pour plus d'informations sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-476">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="f9c1e-477">Jeton de prise en charge d'endossement</span><span class="sxs-lookup"><span data-stu-id="f9c1e-477">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
       </wst:KeyType>  
     </sp:RequestSecurityTokenTemplate>  
     <wsp:Policy>  
       <sp:RequireDerivedKeys />   
       <sp:RequireInternalReference />   
     </wsp:Policy>  
   </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="f9c1e-478">Exemples d'en-tête de sécurité : SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-478">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="f9c1e-479">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-479">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-480">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-480">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="f9c1e-481">Exemples d'en-tête de sécurité : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="f9c1e-481">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="f9c1e-482">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-482">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-483">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-483">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
## <a name="63-kerberos"></a><span data-ttu-id="f9c1e-484">6.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="f9c1e-484">6.3 Kerberos</span></span>  
 <span data-ttu-id="f9c1e-485">Avec ce mode d'authentification, le client s'authentifie auprès du service à l'aide d'un ticket Kerberos.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-485">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="f9c1e-486">Ce même ticket fournit également l'authentification de serveur.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-486">That same ticket also provides server authentication.</span></span> <span data-ttu-id="f9c1e-487">La liaison utilisée est une liaison symétrique avec les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-487">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="f9c1e-488">Jeton de protection : Ticket Kerberos, avec mode d'inclusion défini à …/IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="f9c1e-488">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="f9c1e-489">Jeton de protection : False</span><span class="sxs-lookup"><span data-stu-id="f9c1e-489">Token Protection: False</span></span>  
  
 <span data-ttu-id="f9c1e-490">Signatures du corps et de l'intégralité de l'en-tête : True</span><span class="sxs-lookup"><span data-stu-id="f9c1e-490">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="f9c1e-491">Ordre de protection : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="f9c1e-491">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="f9c1e-492">Chiffrement de la signature : True</span><span class="sxs-lookup"><span data-stu-id="f9c1e-492">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="f9c1e-493">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-493">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='Kerberos_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:KerberosToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:WssGssKerberosV5ApReqToken11 />   
                </wsp:Policy>  
              </sp:KerberosToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="f9c1e-494">Exemples d'en-tête de sécurité : SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-494">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="f9c1e-495">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-495">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-496">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-496">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="f9c1e-497">Exemples d'en-tête de sécurité : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="f9c1e-497">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="f9c1e-498">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-498">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-499">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-499">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="f9c1e-500">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="f9c1e-500">6.4 IssuedToken</span></span>  
 <span data-ttu-id="f9c1e-501">Avec ce mode d'authentification, le client ne s'authentifie pas auprès du service, en tant que tel, mais présente à la place un jeton émis par un STS et prouve qu'il connaît une clé partagée.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-501">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="f9c1e-502">Le service n'est pas authentifié auprès du client, en tant que tel, mais le STS chiffre la clé partagée dans le cadre du jeton émis afin que seul le service puisse déchiffrer la clé.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-502">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="f9c1e-503">La liaison utilisée est une liaison symétrique avec les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-503">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="f9c1e-504">Jeton de protection : Jeton émis, avec mode d'inclusion défini à .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="f9c1e-504">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="f9c1e-505">Jeton de protection : False</span><span class="sxs-lookup"><span data-stu-id="f9c1e-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="f9c1e-506">Signatures du corps et de l'intégralité de l'en-tête : True</span><span class="sxs-lookup"><span data-stu-id="f9c1e-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="f9c1e-507">Ordre de protection : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="f9c1e-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="f9c1e-508">Chiffrement de la signature : True</span><span class="sxs-lookup"><span data-stu-id="f9c1e-508">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="f9c1e-509">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-509">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple3_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <sp:RequestSecurityTokenTemplate>  
                  <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
                  </wst:KeyType>   
                </sp:RequestSecurityTokenTemplate>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireInternalReference />   
                </wsp:Policy>  
              </sp:IssuedToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="f9c1e-510">Exemples d'en-tête de sécurité : SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-510">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="f9c1e-511">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-511">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-512">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-512">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="f9c1e-513">Exemples d'en-tête de sécurité : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="f9c1e-513">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="f9c1e-514">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-514">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-515">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-515">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="f9c1e-516">6.5 Utilisation de SslNegotiated pour l'authentification de service</span><span class="sxs-lookup"><span data-stu-id="f9c1e-516">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="f9c1e-517">Cette section décrit un groupe de modes d'authentification qui utilisent une liaison symétrique, le jeton de protection étant un jeton de contexte de sécurité tel que défini dans WS-SC (WS-SecureConversation) dont la valeur de clé est négociée en exécutant le protocole TLS sur les messages WS-T (WS-Trust) RST/RSTR.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-517">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="f9c1e-518">Les détails de l'implémentation de la négociation TLS à l'aide de WS-Trust sont décrits dans TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-518">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="f9c1e-519">Dans les exemples de message présentés, nous supposerons que le SCT avec un contexte de sécurité associé est déjà établi via une négociation.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-519">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="f9c1e-520">La liaison utilisée est une liaison symétrique avec les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-520">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="f9c1e-521">Jeton de protection : SslContextToken, avec mode d'inclusion défini à .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="f9c1e-521">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="f9c1e-522">Jeton de protection : False</span><span class="sxs-lookup"><span data-stu-id="f9c1e-522">Token Protection: False</span></span>  
  
 <span data-ttu-id="f9c1e-523">Signatures du corps et de l'intégralité de l'en-tête : True</span><span class="sxs-lookup"><span data-stu-id="f9c1e-523">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="f9c1e-524">Ordre de protection : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="f9c1e-524">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="f9c1e-525">Chiffrement de la signature : True</span><span class="sxs-lookup"><span data-stu-id="f9c1e-525">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="f9c1e-526">6.5.1 Stratégie d'authentification de service SslNegotiated</span><span class="sxs-lookup"><span data-stu-id="f9c1e-526">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="f9c1e-527">La stratégie utilisée pour tous les modes d'authentification présentés dans cette section est similaire et diffère uniquement par les jetons d'endossement ou de prise en charge signés spécifiques utilisés.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-527">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' />  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </mssp:SslContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting token assertions go here -->  
      ..  
      <sp:Wss11>   
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="f9c1e-528">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="f9c1e-528">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="f9c1e-529">Avec ce mode d'authentification, le client est anonyme et le service est authentifié à l'aide d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-529">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="f9c1e-530">La liaison utilisée est une instance de liaison symétrique, tel que décrit à la section 6.5.1 ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-530">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="f9c1e-531">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-531">Policy</span></span>  
  
 <span data-ttu-id="f9c1e-532">Consultez « Stratégie » à la section 6.5.1 ci-dessus pour plus d'informations sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-532">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="f9c1e-533">Exemples d'en-tête de sécurité : SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-533">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="f9c1e-534">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-534">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-535">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-535">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="f9c1e-536">Exemples d'en-tête de sécurité : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="f9c1e-536">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="f9c1e-537">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-537">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-538">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-538">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="f9c1e-539">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="f9c1e-539">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="f9c1e-540">Avec ce mode d'authentification, le client s'authentifie auprès du service à l'aide d'un jeton de nom d'utilisateur qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge signé.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-540">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="f9c1e-541">Le service est authentifié à l'aide d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-541">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="f9c1e-542">La liaison utilisée est une instance de liaison symétrique, tel que décrit à la section 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-542">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="f9c1e-543">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-543">Policy</span></span>  
  
 <span data-ttu-id="f9c1e-544">Consultez la section 6.5.1 ci-dessus pour plus d'informations sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-544">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="f9c1e-545">Jeton de prise en charge signé</span><span class="sxs-lookup"><span data-stu-id="f9c1e-545">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="f9c1e-546">Exemples d'en-tête de sécurité : SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-546">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="f9c1e-547">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-547">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-548">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-548">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="f9c1e-549">Exemples d'en-tête de sécurité : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="f9c1e-549">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="f9c1e-550">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-550">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-551">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-551">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="f9c1e-552">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="f9c1e-552">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="f9c1e-553">Avec ce mode d'authentification, le client ne s'authentifie pas auprès du service, en tant que tel, mais présente à la place un jeton émis par un STS et prouve qu'il connaît une clé partagée.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-553">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="f9c1e-554">Le jeton émis apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-554">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="f9c1e-555">Le service est authentifié à l'aide d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-555">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="f9c1e-556">La liaison utilisée est une instance de liaison symétrique, tel que décrit à la section 6.5.1 ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-556">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="f9c1e-557">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-557">Policy</span></span>  
  
 <span data-ttu-id="f9c1e-558">Consultez la section 6.5.1 ci-dessus pour plus d'informations sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-558">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="f9c1e-559">Jeton de prise en charge d'endossement</span><span class="sxs-lookup"><span data-stu-id="f9c1e-559">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
        </wst:KeyType>   
      </sp:RequestSecurityTokenTemplate>  
      <wsp:Policy>  
        <sp:RequireDerivedKeys />   
        <sp:RequireInternalReference />   
      </wsp:Policy>  
    </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="f9c1e-560">Exemples d'en-tête de sécurité : SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-560">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="f9c1e-561">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-561">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-562">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-562">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="f9c1e-563">Exemples d'en-tête de sécurité : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="f9c1e-563">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="f9c1e-564">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-564">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-565">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-565">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="f9c1e-566">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="f9c1e-566">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="f9c1e-567">Avec ce mode d'authentification, le client et le service s'authentifient à l'aide de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-567">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="f9c1e-568">La liaison utilisée est une instance de liaison symétrique, tel que décrit à la section 6.5.1 ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-568">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="f9c1e-569">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-569">Policy</span></span>  
  
 <span data-ttu-id="f9c1e-570">Consultez la section 6.5.1 ci-dessus pour plus d'informations sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-570">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="f9c1e-571">Jeton de prise en charge d'endossement</span><span class="sxs-lookup"><span data-stu-id="f9c1e-571">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="f9c1e-572">Exemples d'en-tête de sécurité : SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-572">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="f9c1e-573">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-573">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-574">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-574">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="f9c1e-575">Exemples d'en-tête de sécurité : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="f9c1e-575">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="f9c1e-576">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-576">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-577">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-577">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="f9c1e-578">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="f9c1e-578">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="f9c1e-579">Avec ce mode d'authentification, un protocole de négociation est utilisé pour effectuer l'authentification du client et du serveur.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-579">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="f9c1e-580">Le protocole Kerberos est dans la mesure du possible utilisé, sinon c'est NTLM.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-580">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="f9c1e-581">La liaison utilisée est une liaison symétrique avec les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9c1e-581">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="f9c1e-582">Jeton de protection : SpnegoContextToken, avec mode d'inclusion défini à .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="f9c1e-582">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="f9c1e-583">Jeton de protection : False</span><span class="sxs-lookup"><span data-stu-id="f9c1e-583">Token Protection: False</span></span>  
  
 <span data-ttu-id="f9c1e-584">Signatures du corps et de l'intégralité de l'en-tête : True</span><span class="sxs-lookup"><span data-stu-id="f9c1e-584">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="f9c1e-585">Ordre de protection : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="f9c1e-585">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="f9c1e-586">Chiffrement de la signature : True</span><span class="sxs-lookup"><span data-stu-id="f9c1e-586">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="f9c1e-587">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-587">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple13_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </sp:SpnegoContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="f9c1e-588">Exemples d'en-tête de sécurité : SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-588">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="f9c1e-589">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-589">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-590">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-590">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="f9c1e-591">Exemples d'en-tête de sécurité : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="f9c1e-591">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="f9c1e-592">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-592">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-593">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-593">Response</span></span>  
  
```xml  
<wsse:Security>  
<wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="67-secureconversation"></a><span data-ttu-id="f9c1e-594">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="f9c1e-594">6.7 SecureConversation</span></span>  
 <span data-ttu-id="f9c1e-595">La liaison utilisée est une liaison symétrique, le jeton de protection étant un SCT tel que défini dans WS-SC (WS-SecureConversation).</span><span class="sxs-lookup"><span data-stu-id="f9c1e-595">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="f9c1e-596">Le SCT est négocié à l'aide de WS-T (WS-Trust) ou WS-SC (WS-SecureConversation) d'après une liaison imbriquée, qui est elle-même une liaison symétrique utilisant un protocole de négociation.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-596">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="f9c1e-597">Le protocole de négociation utilisera Kerberos pour effectuer l'authentification du client et du serveur, si possible.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-597">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="f9c1e-598">Si Kerberos ne peut pas être utilisé, ce sera NTLM.</span><span class="sxs-lookup"><span data-stu-id="f9c1e-598">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="f9c1e-599">Stratégie</span><span class="sxs-lookup"><span data-stu-id="f9c1e-599">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SecureConversation_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SecureConversationToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:BootstrapPolicy>  
                    <wsp:Policy>  
                      <sp:SignedParts>  
                        <sp:Body />   
                        <sp:Header Name='To' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='From' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='FaultTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='ReplyTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='MessageID' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='RelatesTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='Action' Namespace='http://www.w3.org/2005/08/addressing' />   
                      </sp:SignedParts>  
                      <sp:EncryptedParts>  
                        <sp:Body />   
                      </sp:EncryptedParts>  
                      <sp:SymmetricBinding>  
                        <wsp:Policy>  
                          <sp:ProtectionToken>  
                            <wsp:Policy>  
                              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                                <wsp:Policy>  
                                  <sp:RequireDerivedKeys />   
                                </wsp:Policy>  
                              </sp:SpnegoContextToken>  
                            </wsp:Policy>  
                          </sp:ProtectionToken>  
                          <sp:AlgorithmSuite>  
                            <wsp:Policy>  
                              <sp:Basic256 />   
                            </wsp:Policy>  
                          </sp:AlgorithmSuite>  
                          <sp:Layout>  
                            <wsp:Policy>  
                              <sp:Strict />   
                            </wsp:Policy>  
                          </sp:Layout>  
                          <sp:IncludeTimestamp />   
                          <sp:EncryptSignature />   
                          <sp:OnlySignEntireHeadersAndBody />   
                        </wsp:Policy>  
                      </sp:SymmetricBinding>  
                      <sp:Wss11>  
                        <wsp:Policy>  
                          <sp:MustSupportRefKeyIdentifier />   
                          <sp:MustSupportRefIssuerSerial />   
                          <sp:MustSupportRefThumbprint />   
                          <sp:MustSupportRefEncryptedKey />   
                        </wsp:Policy>  
                      </sp:Wss11>  
                      <sp:Trust10>  
                        <wsp:Policy>  
                          <sp:MustSupportIssuedTokens />   
                          <sp:RequireClientEntropy />   
                          <sp:RequireServerEntropy />   
                        </wsp:Policy>  
                      </sp:Trust10>  
                    </wsp:Policy>  
                  </sp:BootstrapPolicy>  
                </wsp:Policy>  
              </sp:SecureConversationToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="f9c1e-600">Exemples d'en-tête de sécurité : SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="f9c1e-600">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="f9c1e-601">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-601">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-602">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-602">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="f9c1e-603">Exemples d'en-tête de sécurité : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="f9c1e-603">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="f9c1e-604">Requête</span><span class="sxs-lookup"><span data-stu-id="f9c1e-604">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="f9c1e-605">Réponse</span><span class="sxs-lookup"><span data-stu-id="f9c1e-605">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```
