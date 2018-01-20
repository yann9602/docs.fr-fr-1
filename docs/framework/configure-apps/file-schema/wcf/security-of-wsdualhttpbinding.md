---
title: '&lt;security&gt; de &lt;wsDualHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 6680d01b068a6ac1c4f9abcda69779c9cd0786a0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="21d98-102">&lt;security&gt; de &lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="21d98-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="21d98-103">Définit les fonctionnalités de sécurité le [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="21d98-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="21d98-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="21d98-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="21d98-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="21d98-105">\<bindings></span></span>  
<span data-ttu-id="21d98-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="21d98-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="21d98-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="21d98-107">\<binding></span></span>  
<span data-ttu-id="21d98-108">\<security></span><span class="sxs-lookup"><span data-stu-id="21d98-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21d98-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21d98-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21d98-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="21d98-110">Attributes and Elements</span></span>  
 <span data-ttu-id="21d98-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="21d98-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21d98-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="21d98-112">Attributes</span></span>  
  
|<span data-ttu-id="21d98-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="21d98-113">Attribute</span></span>|<span data-ttu-id="21d98-114">Description</span><span class="sxs-lookup"><span data-stu-id="21d98-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="21d98-115">mode</span><span class="sxs-lookup"><span data-stu-id="21d98-115">mode</span></span>|<span data-ttu-id="21d98-116">-Facultatif.</span><span class="sxs-lookup"><span data-stu-id="21d98-116">-   Optional.</span></span> <span data-ttu-id="21d98-117">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="21d98-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="21d98-118">La valeur par défaut est `Message`.</span><span class="sxs-lookup"><span data-stu-id="21d98-118">The default value is `Message`.</span></span> <span data-ttu-id="21d98-119">Cet attribut est de type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="21d98-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="21d98-120">Mode, attribut</span><span class="sxs-lookup"><span data-stu-id="21d98-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="21d98-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="21d98-121">Value</span></span>|<span data-ttu-id="21d98-122">Description</span><span class="sxs-lookup"><span data-stu-id="21d98-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="21d98-123">None</span><span class="sxs-lookup"><span data-stu-id="21d98-123">None</span></span>|<span data-ttu-id="21d98-124">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="21d98-124">Security is disabled.</span></span>|  
|<span data-ttu-id="21d98-125">Message</span><span class="sxs-lookup"><span data-stu-id="21d98-125">Message</span></span>|<span data-ttu-id="21d98-126">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="21d98-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21d98-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="21d98-127">Child Elements</span></span>  
  
|<span data-ttu-id="21d98-128">Élément</span><span class="sxs-lookup"><span data-stu-id="21d98-128">Element</span></span>|<span data-ttu-id="21d98-129">Description</span><span class="sxs-lookup"><span data-stu-id="21d98-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21d98-130">\<message></span><span class="sxs-lookup"><span data-stu-id="21d98-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="21d98-131">Définit les paramètres de sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="21d98-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="21d98-132">Cet élément est de type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="21d98-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21d98-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="21d98-133">Parent Elements</span></span>  
  
|<span data-ttu-id="21d98-134">Élément</span><span class="sxs-lookup"><span data-stu-id="21d98-134">Element</span></span>|<span data-ttu-id="21d98-135">Description</span><span class="sxs-lookup"><span data-stu-id="21d98-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21d98-136">\<binding></span><span class="sxs-lookup"><span data-stu-id="21d98-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="21d98-137">Définit toutes les fonctions de liaison de la [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="21d98-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21d98-138">Notes</span><span class="sxs-lookup"><span data-stu-id="21d98-138">Remarks</span></span>  
 <span data-ttu-id="21d98-139">Une liaison double expose l’adresse IP du client au service.</span><span class="sxs-lookup"><span data-stu-id="21d98-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="21d98-140">Ce client doit utiliser un mode de sécurité qui vérifiera qu'il se connecte uniquement à des services de confiance.</span><span class="sxs-lookup"><span data-stu-id="21d98-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21d98-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21d98-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="21d98-142">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="21d98-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="21d98-143">Liaisons</span><span class="sxs-lookup"><span data-stu-id="21d98-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="21d98-144">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="21d98-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="21d98-145">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="21d98-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="21d98-146">\<binding></span><span class="sxs-lookup"><span data-stu-id="21d98-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
