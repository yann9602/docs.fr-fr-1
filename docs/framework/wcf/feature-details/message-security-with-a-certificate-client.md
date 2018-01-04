---
title: "Sécurité de message avec un client de certificat"
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
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
caps.latest.revision: "16"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e778b48b3ff00c3053992f8e754f674cd7705ece
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="41c94-102">Sécurité de message avec un client de certificat</span><span class="sxs-lookup"><span data-stu-id="41c94-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="41c94-103">Le scénario suivant montre un client et un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sécurisés à l'aide du mode de sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="41c94-103">The following scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service secured using message security mode.</span></span> <span data-ttu-id="41c94-104">Le client et le service sont tous les deux authentifiés à l'aide de certificats.</span><span class="sxs-lookup"><span data-stu-id="41c94-104">Both the client and the service are authenticated with certificates.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="41c94-105">[La sécurité de l’Application distribuée](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="41c94-105"> [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>  
  
 <span data-ttu-id="41c94-106">Pour un exemple d’application, consultez [certificat de sécurité de Message](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="41c94-106">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  
  
 <span data-ttu-id="41c94-107">![Client avec certificat](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span><span class="sxs-lookup"><span data-stu-id="41c94-107">![Client with certificate](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span></span>  
  
|<span data-ttu-id="41c94-108">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="41c94-108">Characteristic</span></span>|<span data-ttu-id="41c94-109">Description</span><span class="sxs-lookup"><span data-stu-id="41c94-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="41c94-110">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="41c94-110">Security Mode</span></span>|<span data-ttu-id="41c94-111">Message</span><span class="sxs-lookup"><span data-stu-id="41c94-111">Message</span></span>|  
|<span data-ttu-id="41c94-112">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="41c94-112">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="41c94-113"> uniquement</span><span class="sxs-lookup"><span data-stu-id="41c94-113"> only</span></span>|  
|<span data-ttu-id="41c94-114">Authentification (serveur)</span><span class="sxs-lookup"><span data-stu-id="41c94-114">Authentication (Server)</span></span>|<span data-ttu-id="41c94-115">Utilisation de certificat de service</span><span class="sxs-lookup"><span data-stu-id="41c94-115">Using service certificate</span></span>|  
|<span data-ttu-id="41c94-116">Authentification (client)</span><span class="sxs-lookup"><span data-stu-id="41c94-116">Authentication (Client)</span></span>|<span data-ttu-id="41c94-117">Utilisation de certificat client</span><span class="sxs-lookup"><span data-stu-id="41c94-117">Using client certificate</span></span>|  
|<span data-ttu-id="41c94-118">Intégrité</span><span class="sxs-lookup"><span data-stu-id="41c94-118">Integrity</span></span>|<span data-ttu-id="41c94-119">Oui</span><span class="sxs-lookup"><span data-stu-id="41c94-119">Yes</span></span>|  
|<span data-ttu-id="41c94-120">Confidentialité</span><span class="sxs-lookup"><span data-stu-id="41c94-120">Confidentiality</span></span>|<span data-ttu-id="41c94-121">Oui</span><span class="sxs-lookup"><span data-stu-id="41c94-121">Yes</span></span>|  
|<span data-ttu-id="41c94-122">Transport</span><span class="sxs-lookup"><span data-stu-id="41c94-122">Transport</span></span>|<span data-ttu-id="41c94-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="41c94-123">HTTP</span></span>|  
|<span data-ttu-id="41c94-124">Binding</span><span class="sxs-lookup"><span data-stu-id="41c94-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="41c94-125">Service</span><span class="sxs-lookup"><span data-stu-id="41c94-125">Service</span></span>  
 <span data-ttu-id="41c94-126">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="41c94-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="41c94-127">Effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="41c94-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="41c94-128">Créez un service autonome à l'aide du code sans configuration.</span><span class="sxs-lookup"><span data-stu-id="41c94-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="41c94-129">Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="41c94-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="41c94-130">Code</span><span class="sxs-lookup"><span data-stu-id="41c94-130">Code</span></span>  
 <span data-ttu-id="41c94-131">Le code ci-dessous montre comment créer un point de terminaison de service qui utilise la sécurité de message pour établir un contexte sécurisé.</span><span class="sxs-lookup"><span data-stu-id="41c94-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="41c94-132">Configuration</span><span class="sxs-lookup"><span data-stu-id="41c94-132">Configuration</span></span>  
 <span data-ttu-id="41c94-133">La configuration ci-dessous peut être utilisée à la place du code.</span><span class="sxs-lookup"><span data-stu-id="41c94-133">The following configuration can be used instead of the code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndCerficiateClient"   
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="41c94-134">Client</span><span class="sxs-lookup"><span data-stu-id="41c94-134">Client</span></span>  
 <span data-ttu-id="41c94-135">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="41c94-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="41c94-136">Effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="41c94-136">Do one of the following:</span></span>  
  
-   <span data-ttu-id="41c94-137">Créez un client autonome à l'aide du code (et du code client).</span><span class="sxs-lookup"><span data-stu-id="41c94-137">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="41c94-138">Créez un client qui ne définit pas d'adresse de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="41c94-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="41c94-139">Au lieu de cela, utilisez le constructeur client qui accepte le nom de configuration comme argument.</span><span class="sxs-lookup"><span data-stu-id="41c94-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="41c94-140">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="41c94-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="41c94-141">Code</span><span class="sxs-lookup"><span data-stu-id="41c94-141">Code</span></span>  
 <span data-ttu-id="41c94-142">Le code ci-dessous crée le client.</span><span class="sxs-lookup"><span data-stu-id="41c94-142">The following code creates the client.</span></span> <span data-ttu-id="41c94-143">La liaison s'effectue avec la sécurité en mode de message et le type d'informations d'identification client a la valeur `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="41c94-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="41c94-144">Configuration</span><span class="sxs-lookup"><span data-stu-id="41c94-144">Configuration</span></span>  
 <span data-ttu-id="41c94-145">La configuration ci-dessous spécifie le certificat client à l'aide d'un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="41c94-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="41c94-146">Pour plus d’informations sur les certificats, consultez [Utilisation de certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="41c94-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="41c94-147">Le code utilise également une <`identity`> élément pour spécifier un système DNS (Domain Name) de l’identité de serveur attendues.</span><span class="sxs-lookup"><span data-stu-id="41c94-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="41c94-148">identité, consultez [l’identité du Service et l’authentification](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="41c94-148"> identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"   
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="41c94-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41c94-149">See Also</span></span>  
 [<span data-ttu-id="41c94-150">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="41c94-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="41c94-151">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="41c94-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="41c94-152">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="41c94-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="41c94-153">Modèle de sécurité pour Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="41c94-153">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
