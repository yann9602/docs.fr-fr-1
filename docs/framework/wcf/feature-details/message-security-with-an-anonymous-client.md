---
title: "Sécurité de message avec un client anonyme"
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
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: edf1dd36fe8c0f3e6c1ae8087d1bacbc00cf307a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="aab9a-102">Sécurité de message avec un client anonyme</span><span class="sxs-lookup"><span data-stu-id="aab9a-102">Message Security with an Anonymous Client</span></span>
<span data-ttu-id="aab9a-103">Le scénario suivant illustre un client et le service sécurisé par la sécurité de message [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aab9a-103">The following scenario shows a client and service secured by [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] message security.</span></span> <span data-ttu-id="aab9a-104">L'un des objectifs de conception consiste à utiliser la sécurité de message plutôt que la sécurité de transport, afin qu'à l'avenir il puisse prendre en charge un modèle plus riche basé sur les revendications.</span><span class="sxs-lookup"><span data-stu-id="aab9a-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="aab9a-105">l’utilisation des revendications riche pour l’autorisation, consultez [la gestion des revendications et autorisation avec le modèle d’identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="aab9a-105"> using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>  
  
 <span data-ttu-id="aab9a-106">Pour un exemple d’application, consultez [Message Security Anonymous](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="aab9a-106">For a sample application, see [Message Security Anonymous](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span></span>  
  
 <span data-ttu-id="aab9a-107">![Message de sécurité avec un client anonyme](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="aab9a-107">![Message security with an anynymous client](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>  
  
|<span data-ttu-id="aab9a-108">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="aab9a-108">Characteristic</span></span>|<span data-ttu-id="aab9a-109">Description</span><span class="sxs-lookup"><span data-stu-id="aab9a-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="aab9a-110">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="aab9a-110">Security Mode</span></span>|<span data-ttu-id="aab9a-111">Message</span><span class="sxs-lookup"><span data-stu-id="aab9a-111">Message</span></span>|  
|<span data-ttu-id="aab9a-112">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="aab9a-112">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="aab9a-113"> uniquement</span><span class="sxs-lookup"><span data-stu-id="aab9a-113"> only</span></span>|  
|<span data-ttu-id="aab9a-114">Authentification (serveur)</span><span class="sxs-lookup"><span data-stu-id="aab9a-114">Authentication (Server)</span></span>|<span data-ttu-id="aab9a-115">La négociation initiale requiert l'authentification du serveur, mais pas l'authentification du client</span><span class="sxs-lookup"><span data-stu-id="aab9a-115">Initial negotiation requires server authentication, but not client authentication</span></span>|  
|<span data-ttu-id="aab9a-116">Authentification (client)</span><span class="sxs-lookup"><span data-stu-id="aab9a-116">Authentication (Client)</span></span>|<span data-ttu-id="aab9a-117">None</span><span class="sxs-lookup"><span data-stu-id="aab9a-117">None</span></span>|  
|<span data-ttu-id="aab9a-118">Intégrité</span><span class="sxs-lookup"><span data-stu-id="aab9a-118">Integrity</span></span>|<span data-ttu-id="aab9a-119">Oui, à l'aide du contexte de sécurité partagé</span><span class="sxs-lookup"><span data-stu-id="aab9a-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="aab9a-120">Confidentialité</span><span class="sxs-lookup"><span data-stu-id="aab9a-120">Confidentiality</span></span>|<span data-ttu-id="aab9a-121">Oui, à l'aide du contexte de sécurité partagé</span><span class="sxs-lookup"><span data-stu-id="aab9a-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="aab9a-122">Transport</span><span class="sxs-lookup"><span data-stu-id="aab9a-122">Transport</span></span>|<span data-ttu-id="aab9a-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="aab9a-123">HTTP</span></span>|  
  
## <a name="service"></a><span data-ttu-id="aab9a-124">Service</span><span class="sxs-lookup"><span data-stu-id="aab9a-124">Service</span></span>  
 <span data-ttu-id="aab9a-125">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="aab9a-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="aab9a-126">Effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="aab9a-126">Do one of the following:</span></span>  
  
-   <span data-ttu-id="aab9a-127">Créez un service autonome à l'aide du code sans configuration.</span><span class="sxs-lookup"><span data-stu-id="aab9a-127">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="aab9a-128">Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="aab9a-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="aab9a-129">Code</span><span class="sxs-lookup"><span data-stu-id="aab9a-129">Code</span></span>  
 <span data-ttu-id="aab9a-130">Le code suivant montre comment créer un point de terminaison de service qui utilise la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="aab9a-130">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
 [!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]  
  
### <a name="configuration"></a><span data-ttu-id="aab9a-131">Configuration</span><span class="sxs-lookup"><span data-stu-id="aab9a-131">Configuration</span></span>  
 <span data-ttu-id="aab9a-132">La configuration ci-dessous peut être utilisée à la place du code.</span><span class="sxs-lookup"><span data-stu-id="aab9a-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="aab9a-133">L'élément de comportement du service est utilisé pour spécifier un certificat servant à authentifier le service auprès du client.</span><span class="sxs-lookup"><span data-stu-id="aab9a-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="aab9a-134">L'élément de service doit spécifier le comportement à l'aide de l'attribut `behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="aab9a-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="aab9a-135">L'élément de liaison spécifie que le type d'informations d'identification du client est `None`, ce qui permet aux clients anonymes d'utiliser le service.</span><span class="sxs-lookup"><span data-stu-id="aab9a-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="CalculatorService"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="aab9a-136">Client</span><span class="sxs-lookup"><span data-stu-id="aab9a-136">Client</span></span>  
 <span data-ttu-id="aab9a-137">La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment.</span><span class="sxs-lookup"><span data-stu-id="aab9a-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="aab9a-138">Effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="aab9a-138">Do one of the following:</span></span>  
  
-   <span data-ttu-id="aab9a-139">Créez un client autonome à l'aide du code (et du code client).</span><span class="sxs-lookup"><span data-stu-id="aab9a-139">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="aab9a-140">Créez un client qui ne définit pas d'adresse de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="aab9a-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="aab9a-141">Au lieu de cela, utilisez le constructeur client qui accepte le nom de configuration comme argument.</span><span class="sxs-lookup"><span data-stu-id="aab9a-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="aab9a-142">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="aab9a-142">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="aab9a-143">Code</span><span class="sxs-lookup"><span data-stu-id="aab9a-143">Code</span></span>  
 <span data-ttu-id="aab9a-144">Le code suivant crée une instance du client.</span><span class="sxs-lookup"><span data-stu-id="aab9a-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="aab9a-145">La liaison utilise le mode de sécurité au niveau du message, et le type d'informations d'identification du client a la valeur Aucun.</span><span class="sxs-lookup"><span data-stu-id="aab9a-145">The binding uses message mode security, and the client credential type is set to none.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
 [!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]  
  
### <a name="configuration"></a><span data-ttu-id="aab9a-146">Configuration</span><span class="sxs-lookup"><span data-stu-id="aab9a-146">Configuration</span></span>  
 <span data-ttu-id="aab9a-147">Le code ci-dessous configure le client.</span><span class="sxs-lookup"><span data-stu-id="aab9a-147">The following code configures the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"  
        binding="wsHttpBinding"  
        bindingConfiguration="WSHttpBinding_ICalculator"   
        contract="ICalculator"  
        name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aab9a-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aab9a-148">See Also</span></span>  
 [<span data-ttu-id="aab9a-149">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="aab9a-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="aab9a-150">Sécurité des applications distribuées</span><span class="sxs-lookup"><span data-stu-id="aab9a-150">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [<span data-ttu-id="aab9a-151">Sécurité des messages anonyme</span><span class="sxs-lookup"><span data-stu-id="aab9a-151">Message Security Anonymous</span></span>](../../../../docs/framework/wcf/samples/message-security-anonymous.md)  
 [<span data-ttu-id="aab9a-152">L’authentification et identité de Service</span><span class="sxs-lookup"><span data-stu-id="aab9a-152">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="aab9a-153">Modèle de sécurité pour Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="aab9a-153">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
