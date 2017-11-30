---
title: '&lt;clientCertificate&gt; de &lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bc4b3251a85a6926c93f418c154b4eabbd44092f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientcertificategt-of-ltservicecredentialsgt"></a><span data-ttu-id="92786-102">&lt;clientCertificate&gt; de &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="92786-102">&lt;clientCertificate&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="92786-103">Définit un certificat X.509 permettant de signer et de chiffrer des messages destinés à un client et envoyés à partir d’un service selon un modèle de communication duplex.</span><span class="sxs-lookup"><span data-stu-id="92786-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="92786-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="92786-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="92786-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="92786-105">\<behaviors></span></span>  
<span data-ttu-id="92786-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="92786-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="92786-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="92786-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="92786-108">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="92786-108">\<behavior></span></span>  
<span data-ttu-id="92786-109">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="92786-109">\<serviceCredentials></span></span>  
<span data-ttu-id="92786-110">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="92786-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92786-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92786-111">Syntax</span></span>  
  
```xml  
<clientCertificate>  
 <certificate/>  
 <authentication/>  
</clientCertificate>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92786-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="92786-112">Attributes and Elements</span></span>  
 <span data-ttu-id="92786-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="92786-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92786-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="92786-114">Attributes</span></span>  
 <span data-ttu-id="92786-115">Aucun</span><span class="sxs-lookup"><span data-stu-id="92786-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="92786-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="92786-116">Child Elements</span></span>  
  
|<span data-ttu-id="92786-117">Élément</span><span class="sxs-lookup"><span data-stu-id="92786-117">Element</span></span>|<span data-ttu-id="92786-118">Description</span><span class="sxs-lookup"><span data-stu-id="92786-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92786-119">\<authentification ></span><span class="sxs-lookup"><span data-stu-id="92786-119">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|<span data-ttu-id="92786-120">Spécifie des options d'authentification pour le certificat client.</span><span class="sxs-lookup"><span data-stu-id="92786-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="92786-121">\<certificat ></span><span class="sxs-lookup"><span data-stu-id="92786-121">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|<span data-ttu-id="92786-122">Spécifie le certificat à utiliser.</span><span class="sxs-lookup"><span data-stu-id="92786-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="92786-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="92786-123">Parent Elements</span></span>  
  
|<span data-ttu-id="92786-124">Élément</span><span class="sxs-lookup"><span data-stu-id="92786-124">Element</span></span>|<span data-ttu-id="92786-125">Description</span><span class="sxs-lookup"><span data-stu-id="92786-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92786-126">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="92786-126">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="92786-127">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="92786-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92786-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="92786-128">Remarks</span></span>  
 <span data-ttu-id="92786-129">Cet élément est utilisé lorsque le service doit disposer du certificat du client à l'avance afin de communiquer de manière sécurisée avec le client.</span><span class="sxs-lookup"><span data-stu-id="92786-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="92786-130">Cela se produit lors de l'utilisation du modèle de communication duplex.</span><span class="sxs-lookup"><span data-stu-id="92786-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="92786-131">Dans le modèle demande-réponse classique, le client inclut son certificat dans la demande que le service utilise pour sécuriser à nouveau sa réponse au client.</span><span class="sxs-lookup"><span data-stu-id="92786-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="92786-132">Dans le modèle de communication duplex, toutefois, le service ne dispose pas de demande du client et, par conséquent, requiert le certificat du client à l'avance pour sécuriser l'envoi du message au client.</span><span class="sxs-lookup"><span data-stu-id="92786-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="92786-133">C'est pourquoi vous devez obtenir le certificat du client dans une négociation hors bande et l'indiquer à l'aide de cet élément.</span><span class="sxs-lookup"><span data-stu-id="92786-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="92786-134">Pour plus d’informations sur les services duplex, consultez [Comment : créer un contrat Duplex](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="92786-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="92786-135">Le certificat défini dans cet élément est utilisé pour chiffrer les messages au client uniquement pour les liaisons configurées avec le mode d'authentification de sécurité des messages `MutualCertificateDuplex`.</span><span class="sxs-lookup"><span data-stu-id="92786-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92786-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92786-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>  
 [<span data-ttu-id="92786-137">Comment : créer un contrat Duplex</span><span class="sxs-lookup"><span data-stu-id="92786-137">How to: Create a Duplex Contract</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="92786-138">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="92786-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="92786-139">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="92786-139">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
