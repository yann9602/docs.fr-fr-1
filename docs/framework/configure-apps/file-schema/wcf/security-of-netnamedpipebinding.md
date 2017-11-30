---
title: '&lt;security&gt; de &lt;netNamedPipeBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: efb6289c63cdc98402336949ef5916e7568775a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="44739-102">&lt;security&gt; de &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="44739-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="44739-103">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="44739-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="44739-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="44739-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="44739-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="44739-105">\<bindings></span></span>  
<span data-ttu-id="44739-106">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="44739-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="44739-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="44739-107">\<binding></span></span>  
<span data-ttu-id="44739-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="44739-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44739-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44739-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44739-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="44739-110">Attributes and Elements</span></span>  
 <span data-ttu-id="44739-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="44739-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44739-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="44739-112">Attributes</span></span>  
  
|<span data-ttu-id="44739-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="44739-113">Attribute</span></span>|<span data-ttu-id="44739-114">Description</span><span class="sxs-lookup"><span data-stu-id="44739-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44739-115">mode</span><span class="sxs-lookup"><span data-stu-id="44739-115">mode</span></span>|<span data-ttu-id="44739-116">Spécifie le type de sécurité appliqué à cette liaison.</span><span class="sxs-lookup"><span data-stu-id="44739-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="44739-117">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="44739-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="44739-118">-None : La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="44739-118">-   None: This disables security.</span></span><br /><span data-ttu-id="44739-119">-Transport : La sécurité est fournie à l’aide de la sécurité basée sur le transport sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="44739-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="44739-120">Il est possible de contrôler le niveau de protection avec ce mode.</span><span class="sxs-lookup"><span data-stu-id="44739-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="44739-121">-La valeur par défaut est Transport.</span><span class="sxs-lookup"><span data-stu-id="44739-121">-   The default value is Transport.</span></span> <span data-ttu-id="44739-122">Cet attribut est de type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="44739-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44739-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="44739-123">Child Elements</span></span>  
  
|<span data-ttu-id="44739-124">Élément</span><span class="sxs-lookup"><span data-stu-id="44739-124">Element</span></span>|<span data-ttu-id="44739-125">Description</span><span class="sxs-lookup"><span data-stu-id="44739-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44739-126">transport</span><span class="sxs-lookup"><span data-stu-id="44739-126">transport</span></span>|<span data-ttu-id="44739-127">Définit les paramètres de sécurité pour le transport.</span><span class="sxs-lookup"><span data-stu-id="44739-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="44739-128">Cet élément est de type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="44739-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="44739-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="44739-129">Parent Elements</span></span>  
  
|<span data-ttu-id="44739-130">Élément</span><span class="sxs-lookup"><span data-stu-id="44739-130">Element</span></span>|<span data-ttu-id="44739-131">Description</span><span class="sxs-lookup"><span data-stu-id="44739-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44739-132">liaison</span><span class="sxs-lookup"><span data-stu-id="44739-132">binding</span></span>|<span data-ttu-id="44739-133">L’élément de liaison de la [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="44739-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44739-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44739-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="44739-135">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="44739-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="44739-136">Sélection d’un Type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="44739-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="44739-137">Liaisons</span><span class="sxs-lookup"><span data-stu-id="44739-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="44739-138">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="44739-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="44739-139">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="44739-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="44739-140">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="44739-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
