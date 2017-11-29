---
title: '&lt;message&gt; de &lt;netMsmqBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3b03fcce02c51563ed006e62a3f77f76bede777
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="484ef-102">&lt;message&gt; de &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="484ef-102">&lt;message&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="484ef-103">Définit les paramètres de sécurité des messages SOAP sur cette liaison `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="484ef-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>  
  
 <span data-ttu-id="484ef-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="484ef-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="484ef-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="484ef-105">\<bindings></span></span>  
<span data-ttu-id="484ef-106">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="484ef-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="484ef-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="484ef-107">\<binding></span></span>  
<span data-ttu-id="484ef-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="484ef-108">\<security></span></span>  
<span data-ttu-id="484ef-109">\<message ></span><span class="sxs-lookup"><span data-stu-id="484ef-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="484ef-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="484ef-110">Syntax</span></span>  
  
```xml  
<netMsmqBinding>  
    <binding>  
      <security>  
         <message   
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
    </security>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="484ef-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="484ef-111">Attributes and Elements</span></span>  
 <span data-ttu-id="484ef-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="484ef-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="484ef-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="484ef-113">Attributes</span></span>  
  
|<span data-ttu-id="484ef-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="484ef-114">Attribute</span></span>|<span data-ttu-id="484ef-115">Description</span><span class="sxs-lookup"><span data-stu-id="484ef-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="484ef-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="484ef-116">algorithmSuite</span></span>|<span data-ttu-id="484ef-117">Définit le chiffrement des messages et algorithmes de clé de type WRAP utilisés pour obtenir la sécurité basée sur des messages pour les messages envoyés via le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="484ef-117">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="484ef-118">La valeur par défaut est `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="484ef-118">The default value is `Aes256`.</span></span> <span data-ttu-id="484ef-119">Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="484ef-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|  
|<span data-ttu-id="484ef-120">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="484ef-120">clientCredentialType</span></span>|<span data-ttu-id="484ef-121">Spécifie le type d'information d'identification à utiliser lors de l'exécution de l'authentification du client pour les messages envoyés via le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="484ef-121">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="484ef-122">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="484ef-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="484ef-123">-None : Permet au service d’interagir avec les clients anonymes.</span><span class="sxs-lookup"><span data-stu-id="484ef-123">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="484ef-124">Ni le service ni le client n'exigent d'informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="484ef-124">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="484ef-125">-Windows : Ainsi, les échanges SOAP d’être dans le contexte authentifié d’informations d’identification Windows.</span><span class="sxs-lookup"><span data-stu-id="484ef-125">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="484ef-126">Exécute toujours une authentification basée sur Kerberos.</span><span class="sxs-lookup"><span data-stu-id="484ef-126">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="484ef-127">-UserName : Permet au service d’exiger que le client soit authentifié à l’aide des informations d’identification de nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="484ef-127">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="484ef-128">Les informations d’identification dans ce cas doivent être spécifiées à l’aide du `clientCredentials` comportement **attention :** [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ne prend pas en charge l’envoi d’un mot de passe digest ou la dérivation de clés à l’aide du mot de passe et de l’utilisation de telles clés pour la sécurité de message.  </span><span class="sxs-lookup"><span data-stu-id="484ef-128">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="484ef-129">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] s'assure ainsi que l'échange est sécurisé lors de l'utilisation d'informations d'identification UserName.</span><span class="sxs-lookup"><span data-stu-id="484ef-129">Therefore, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="484ef-130">Ce mode requiert que le certificat de service soit spécifié côté client à l'aide du comportement `clientCredential` et de `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="484ef-130">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="484ef-131">-Certificate : Permet au service d’exiger que le client soit authentifié à l’aide d’un certificat.</span><span class="sxs-lookup"><span data-stu-id="484ef-131">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="484ef-132">Les informations d'identification du client dans ce cas doivent être spécifiées à l'aide du comportement `clientCredentials`.</span><span class="sxs-lookup"><span data-stu-id="484ef-132">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="484ef-133">Les informations d'identification du service dans ce cas doivent être spécifiées à l'aide du comportement `clientCredentials` en spécifiant le `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="484ef-133">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="484ef-134">-CardSpace : Permet au service d’exiger que le client soit authentifié à l’aide d’un CardSpace.</span><span class="sxs-lookup"><span data-stu-id="484ef-134">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="484ef-135">Le `serviceCertiifcate` doit être configuré dans le comportement `clientCredential`.</span><span class="sxs-lookup"><span data-stu-id="484ef-135">The `serviceCertiifcate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="484ef-136">La valeur par défaut est `Windows`.</span><span class="sxs-lookup"><span data-stu-id="484ef-136">The default value is `Windows`.</span></span> <span data-ttu-id="484ef-137">Cet attribut est de type <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="484ef-137">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="484ef-138">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="484ef-138">Child Elements</span></span>  
 <span data-ttu-id="484ef-139">None</span><span class="sxs-lookup"><span data-stu-id="484ef-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="484ef-140">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="484ef-140">Parent Elements</span></span>  
  
|<span data-ttu-id="484ef-141">Élément</span><span class="sxs-lookup"><span data-stu-id="484ef-141">Element</span></span>|<span data-ttu-id="484ef-142">Description</span><span class="sxs-lookup"><span data-stu-id="484ef-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="484ef-143">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="484ef-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="484ef-144">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="484ef-144">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="484ef-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="484ef-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq>  
 [<span data-ttu-id="484ef-146">Files d’attente dans WCF</span><span class="sxs-lookup"><span data-stu-id="484ef-146">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="484ef-147">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="484ef-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="484ef-148">Liaisons</span><span class="sxs-lookup"><span data-stu-id="484ef-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="484ef-149">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="484ef-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="484ef-150">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="484ef-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="484ef-151">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="484ef-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
