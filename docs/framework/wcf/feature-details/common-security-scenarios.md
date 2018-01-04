---
title: "Scénarios de sécurité courants"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d8881768d66e95ce1391ce1be1663bdc3107a347
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="common-security-scenarios"></a><span data-ttu-id="d31b9-102">Scénarios de sécurité courants</span><span class="sxs-lookup"><span data-stu-id="d31b9-102">Common Security Scenarios</span></span>
<span data-ttu-id="d31b9-103">Les rubriques de cette section présentent un certain nombre de configurations de sécurité de service et client possibles.</span><span class="sxs-lookup"><span data-stu-id="d31b9-103">The topics in this section catalog a number of possible client and service security configurations.</span></span> <span data-ttu-id="d31b9-104">Les configurations varient selon un certain nombre de facteurs.</span><span class="sxs-lookup"><span data-stu-id="d31b9-104">Configurations vary according to a number of factors.</span></span> <span data-ttu-id="d31b9-105">Par exemple, si un service ou un client est sur un intranet, ou si la sécurité est fournie par Windows ou un transport (tel que HTTPS).</span><span class="sxs-lookup"><span data-stu-id="d31b9-105">For example, whether a service or client is on an intranet, or whether the security is provided by Windows or transport (such as HTTPS).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d31b9-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d31b9-106">In This Section</span></span>  
 [<span data-ttu-id="d31b9-107">Service et client Internet non sécurisés</span><span class="sxs-lookup"><span data-stu-id="d31b9-107">Internet Unsecured Client and Service</span></span>](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 <span data-ttu-id="d31b9-108">Exemple de client/service public non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="d31b9-108">An example of a public, unsecured client and service.</span></span>  
  
 [<span data-ttu-id="d31b9-109">Service et client intranet non sécurisés</span><span class="sxs-lookup"><span data-stu-id="d31b9-109">Intranet Unsecured Client and Service</span></span>](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 <span data-ttu-id="d31b9-110">Service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] de base développé pour fournir des informations sur un réseau privé sécurisé à une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d31b9-110">A basic [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service developed to provide information on a secure private network to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span>  
  
 [<span data-ttu-id="d31b9-111">Sécurité de transport avec authentification de base</span><span class="sxs-lookup"><span data-stu-id="d31b9-111">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 <span data-ttu-id="d31b9-112">L'application autorise les clients à se connecter à l'aide de l'authentification personnalisée.</span><span class="sxs-lookup"><span data-stu-id="d31b9-112">The application allows clients to log on using custom authentication.</span></span>  
  
 [<span data-ttu-id="d31b9-113">Sécurité de transport avec authentification Windows</span><span class="sxs-lookup"><span data-stu-id="d31b9-113">Transport Security with Windows Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 <span data-ttu-id="d31b9-114">Présente un client/service sécurisé par la sécurité Windows.</span><span class="sxs-lookup"><span data-stu-id="d31b9-114">Shows a client and service secured by Windows security.</span></span>  
  
 [<span data-ttu-id="d31b9-115">Sécurité de transport avec un client anonyme</span><span class="sxs-lookup"><span data-stu-id="d31b9-115">Transport Security with an Anonymous Client</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 <span data-ttu-id="d31b9-116">Ce scénario utilise la sécurité de transport (tel que HTTPS) pour assurer la confidentialité et l'intégrité.</span><span class="sxs-lookup"><span data-stu-id="d31b9-116">This scenario uses transport security (such as HTTPS) to ensure confidentiality and integrity.</span></span>  
  
 [<span data-ttu-id="d31b9-117">Sécurité de transport avec authentification par certificat</span><span class="sxs-lookup"><span data-stu-id="d31b9-117">Transport Security with Certificate Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 <span data-ttu-id="d31b9-118">Présente un client/service sécurisé par un certificat.</span><span class="sxs-lookup"><span data-stu-id="d31b9-118">Shows a client and service secured by a certificate.</span></span>  
  
 [<span data-ttu-id="d31b9-119">Sécurité de message avec un client anonyme</span><span class="sxs-lookup"><span data-stu-id="d31b9-119">Message Security with an Anonymous Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 <span data-ttu-id="d31b9-120">Présente un client/service sécurisé par la sécurité de message [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d31b9-120">Shows a client and service secured by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] message security.</span></span>  
  
 [<span data-ttu-id="d31b9-121">Sécurité de message avec un client de type Nom d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="d31b9-121">Message Security with a User Name Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 <span data-ttu-id="d31b9-122">Le client est une application Windows Forms qui autorise les clients à se connecter à l’aide d’un mot de passe et d’un nom d’utilisateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="d31b9-122">The client is a Windows Forms application that allows clients to log on using a domain user name and password.</span></span>  
  
 [<span data-ttu-id="d31b9-123">Sécurité de message avec un client de certificat</span><span class="sxs-lookup"><span data-stu-id="d31b9-123">Message Security with a Certificate Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 <span data-ttu-id="d31b9-124">Les serveurs ont des certificats, et chaque client a un certificat.</span><span class="sxs-lookup"><span data-stu-id="d31b9-124">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="d31b9-125">Un contexte de sécurité est établi via la négociation TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="d31b9-125">A security context is established through Transport Layer Security (TLS) negotiation.</span></span>  
  
 [<span data-ttu-id="d31b9-126">Sécurité de message avec un client Windows</span><span class="sxs-lookup"><span data-stu-id="d31b9-126">Message Security with a Windows Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 <span data-ttu-id="d31b9-127">Variante du client de certificat.</span><span class="sxs-lookup"><span data-stu-id="d31b9-127">A variation of the certificate client.</span></span> <span data-ttu-id="d31b9-128">Les serveurs ont des certificats, et chaque client a un certificat.</span><span class="sxs-lookup"><span data-stu-id="d31b9-128">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="d31b9-129">Un contexte de sécurité est établi via la négociation TLS.</span><span class="sxs-lookup"><span data-stu-id="d31b9-129">A security context is established through TLS negotiation.</span></span>  
  
 [<span data-ttu-id="d31b9-130">Sécurité de message avec un client Windows sans négociation d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="d31b9-130">Message Security with a Windows Client without Credential Negotiation</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 <span data-ttu-id="d31b9-131">Présente un client/service sécurisé par un domaine Kerberos.</span><span class="sxs-lookup"><span data-stu-id="d31b9-131">Shows a client and service secured by a Kerberos domain.</span></span>  
  
 [<span data-ttu-id="d31b9-132">Sécurité de message avec certificats mutuels</span><span class="sxs-lookup"><span data-stu-id="d31b9-132">Message Security with Mutual Certificates</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 <span data-ttu-id="d31b9-133">Les serveurs ont des certificats, et chaque client a un certificat.</span><span class="sxs-lookup"><span data-stu-id="d31b9-133">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="d31b9-134">Le certificat de serveur est distribué avec l'application et est disponible hors bande.</span><span class="sxs-lookup"><span data-stu-id="d31b9-134">The server certificate is distributed with the application and is available out of band.</span></span>  
  
 [<span data-ttu-id="d31b9-135">Sécurité de message avec jetons émis</span><span class="sxs-lookup"><span data-stu-id="d31b9-135">Message Security with Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 <span data-ttu-id="d31b9-136">Sécurité fédérée qui permet d'établir la confiance entre des domaines indépendants.</span><span class="sxs-lookup"><span data-stu-id="d31b9-136">Federated security that enables the establishment of trust between independent domains.</span></span>  
  
 [<span data-ttu-id="d31b9-137">Sous-système approuvé</span><span class="sxs-lookup"><span data-stu-id="d31b9-137">Trusted Subsystem</span></span>](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 <span data-ttu-id="d31b9-138">Un client accède à un ou plusieurs services Web distribués sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="d31b9-138">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="d31b9-139">Les services Web accèdent aux ressources supplémentaires (telles que les bases de données ou autres services Web) qui doivent être sécurisées.</span><span class="sxs-lookup"><span data-stu-id="d31b9-139">The Web services access additional resources (such as databases or other Web services) that must be secured.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d31b9-140">Référence</span><span class="sxs-lookup"><span data-stu-id="d31b9-140">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="d31b9-141">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="d31b9-141">Related Sections</span></span>  
 [<span data-ttu-id="d31b9-142">Autorisation</span><span class="sxs-lookup"><span data-stu-id="d31b9-142">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [<span data-ttu-id="d31b9-143">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="d31b9-143">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
 [<span data-ttu-id="d31b9-144">Sécurité</span><span class="sxs-lookup"><span data-stu-id="d31b9-144">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="d31b9-145">Liaisons et sécurité</span><span class="sxs-lookup"><span data-stu-id="d31b9-145">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="d31b9-146">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="d31b9-146">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
 [<span data-ttu-id="d31b9-147">Authentification</span><span class="sxs-lookup"><span data-stu-id="d31b9-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="d31b9-148">Autorisation</span><span class="sxs-lookup"><span data-stu-id="d31b9-148">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [<span data-ttu-id="d31b9-149">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="d31b9-149">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="d31b9-150">Audit</span><span class="sxs-lookup"><span data-stu-id="d31b9-150">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
  
## <a name="see-also"></a><span data-ttu-id="d31b9-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d31b9-151">See Also</span></span>  
 [<span data-ttu-id="d31b9-152">Aide sur la sécurité et bonnes pratiques</span><span class="sxs-lookup"><span data-stu-id="d31b9-152">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 [<span data-ttu-id="d31b9-153">Modèle de sécurité pour Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="d31b9-153">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
