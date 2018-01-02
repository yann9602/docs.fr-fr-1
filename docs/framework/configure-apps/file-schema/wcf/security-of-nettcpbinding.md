---
title: '&lt;security&gt; de &lt;netTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 08e9f1f3b2145d94f491933639211a6eabd3c9fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a><span data-ttu-id="3b7fd-102">&lt;security&gt; de &lt;netTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="3b7fd-102">&lt;security&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="3b7fd-103">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="3b7fd-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3b7fd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3b7fd-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="3b7fd-105">\<bindings></span></span>  
<span data-ttu-id="3b7fd-106">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="3b7fd-106">\<netTcpBinding></span></span>  
<span data-ttu-id="3b7fd-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="3b7fd-107">\<binding></span></span>  
<span data-ttu-id="3b7fd-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="3b7fd-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b7fd-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b7fd-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
           protectionLevel="None/Sign/EncryptAndSign" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b7fd-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3b7fd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3b7fd-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b7fd-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="3b7fd-112">Attributes</span></span>  
  
|<span data-ttu-id="3b7fd-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="3b7fd-113">Attribute</span></span>|<span data-ttu-id="3b7fd-114">Description</span><span class="sxs-lookup"><span data-stu-id="3b7fd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3b7fd-115">mode</span><span class="sxs-lookup"><span data-stu-id="3b7fd-115">mode</span></span>|<span data-ttu-id="3b7fd-116">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-116">Optional.</span></span> <span data-ttu-id="3b7fd-117">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="3b7fd-118">Les valeurs autorisées sont présentées ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-118">Valid values are shown below.</span></span> <span data-ttu-id="3b7fd-119">La valeur par défaut est `Transport`.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-119">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="3b7fd-120">Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="3b7fd-121">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="3b7fd-121">mode Attribute</span></span>  
  
|<span data-ttu-id="3b7fd-122">Valeur</span><span class="sxs-lookup"><span data-stu-id="3b7fd-122">Value</span></span>|<span data-ttu-id="3b7fd-123">Description</span><span class="sxs-lookup"><span data-stu-id="3b7fd-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3b7fd-124">None</span><span class="sxs-lookup"><span data-stu-id="3b7fd-124">None</span></span>|<span data-ttu-id="3b7fd-125">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-125">Security is disabled.</span></span>|  
|<span data-ttu-id="3b7fd-126">Transport</span><span class="sxs-lookup"><span data-stu-id="3b7fd-126">Transport</span></span>|<span data-ttu-id="3b7fd-127">La sécurité de transport est fournie à l'aide du TLS sur le TCP ou SPNego.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-127">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="3b7fd-128">Le service peut devoir être configuré avec les certificats SSL.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-128">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="3b7fd-129">Il est possible de contrôler le niveau de protection avec ce mode.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-129">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="3b7fd-130">Message</span><span class="sxs-lookup"><span data-stu-id="3b7fd-130">Message</span></span>|<span data-ttu-id="3b7fd-131">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="3b7fd-132">Par défaut, le corps SOAP est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-132">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="3b7fd-133">Ce mode offre diverses fonctionnalités, telles que, si les informations d'identification du service sont disponibles pour le client hors bande, la suite algorithmique à utiliser et quel niveau de protection à appliquer au corps du message.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-133">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="3b7fd-134">L'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-134">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="3b7fd-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="3b7fd-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="3b7fd-136">La sécurité de transport est associée à la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-136">Transport security is coupled with message security.</span></span> <span data-ttu-id="3b7fd-137">La sécurité de transport est fournie par le TLS sur le TCP ou SPNego, et garantit l'intégrité, la confidentialité et l'authentification du serveur.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-137">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="3b7fd-138">La sécurité des messages SOAP fournit l'authentification du client.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-138">SOAP message security provides client authentication.</span></span> <span data-ttu-id="3b7fd-139">Par défaut, l'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b7fd-140">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3b7fd-140">Child Elements</span></span>  
  
|<span data-ttu-id="3b7fd-141">Élément</span><span class="sxs-lookup"><span data-stu-id="3b7fd-141">Element</span></span>|<span data-ttu-id="3b7fd-142">Description</span><span class="sxs-lookup"><span data-stu-id="3b7fd-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b7fd-143">\<transport ></span><span class="sxs-lookup"><span data-stu-id="3b7fd-143">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|<span data-ttu-id="3b7fd-144">Définit les paramètres de sécurité pour le transport.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-144">Defines the security settings for the transport.</span></span> <span data-ttu-id="3b7fd-145">Cet élément est de type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-145">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="3b7fd-146">\<message ></span><span class="sxs-lookup"><span data-stu-id="3b7fd-146">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|<span data-ttu-id="3b7fd-147">Définit les paramètres de sécurité pour le message.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-147">Defines the security settings for the message.</span></span> <span data-ttu-id="3b7fd-148">Cet élément est de type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-148">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3b7fd-149">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3b7fd-149">Parent Elements</span></span>  
  
|<span data-ttu-id="3b7fd-150">Élément</span><span class="sxs-lookup"><span data-stu-id="3b7fd-150">Element</span></span>|<span data-ttu-id="3b7fd-151">Description</span><span class="sxs-lookup"><span data-stu-id="3b7fd-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3b7fd-152">liaison</span><span class="sxs-lookup"><span data-stu-id="3b7fd-152">binding</span></span>|<span data-ttu-id="3b7fd-153">L’élément de liaison de la [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3b7fd-153">The binding element of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b7fd-154">Notes</span><span class="sxs-lookup"><span data-stu-id="3b7fd-154">Remarks</span></span>  
 <span data-ttu-id="3b7fd-155">Chaque liaison standard fournit des paramètres pour le contrôle des exigences de sécurité de transfert.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-155">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="3b7fd-156">Ces paramètres incluent généralement le mode de sécurité qui indique si la sécurité au niveau du message ou du transport est utilisée et le choix du type d'informations d'identification du client.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-156">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="3b7fd-157">Selon le choix d'options présentées par ces paramètres, une pile de canaux est construite avec la sécurité appropriée.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-157">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="3b7fd-158">Les liaisons fournies par le système par Windows Communication Foundation (WCF) constituent un ensemble conçu pour satisfaire aux impératifs de scénario les plus courants.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-158">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="3b7fd-159">Chaque liaison permet la spécification des conditions de sécurité pour des scénarios spécifiques.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-159">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="3b7fd-160">Cet élément de configuration fournit les caractéristiques de sécurité pour `netTcpBinding`.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-160">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="3b7fd-161">Il s'agit d'une liaison sécurisée, fiable et optimisée, adaptée à la communication entre ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-161">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="3b7fd-162">Par défaut, elle génère une pile de communication d'exécution prenant en charge le TCP pour la remise des messages, Windows Security pour l'authentification et la sécurité des messages, WS-ReliableMessaging pour la fiabilité et l'encodage de messages binaires.</span><span class="sxs-lookup"><span data-stu-id="3b7fd-162">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b7fd-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b7fd-163">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="3b7fd-164">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="3b7fd-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="3b7fd-165">Liaisons</span><span class="sxs-lookup"><span data-stu-id="3b7fd-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3b7fd-166">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="3b7fd-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="3b7fd-167">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3b7fd-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="3b7fd-168">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="3b7fd-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
