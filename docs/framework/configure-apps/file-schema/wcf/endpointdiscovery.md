---
title: '&lt;endpointDiscovery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a997ddffa2267cdeb9e54bb98d4122db254104d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltendpointdiscoverygt"></a><span data-ttu-id="4149a-102">&lt;endpointDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="4149a-102">&lt;endpointDiscovery&gt;</span></span>
<span data-ttu-id="4149a-103">Spécifie les différents paramètres de découverte d’un point de terminaison, tels que la fonctionnalité de découverte, les portées et toutes les extensions personnalisées de ses métadonnées.</span><span class="sxs-lookup"><span data-stu-id="4149a-103">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="4149a-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4149a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4149a-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="4149a-105">\<behaviors></span></span>  
<span data-ttu-id="4149a-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4149a-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="4149a-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="4149a-107">\<behavior></span></span>  
<span data-ttu-id="4149a-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="4149a-108">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4149a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4149a-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4149a-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4149a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4149a-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4149a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4149a-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="4149a-112">Attributes</span></span>  
  
|<span data-ttu-id="4149a-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="4149a-113">Attribute</span></span>|<span data-ttu-id="4149a-114">Description</span><span class="sxs-lookup"><span data-stu-id="4149a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4149a-115">enabled</span><span class="sxs-lookup"><span data-stu-id="4149a-115">enabled</span></span>|<span data-ttu-id="4149a-116">Valeur booléenne qui spécifie si la fonctionnalité de découverte est activée sur ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4149a-116">A Boolean value that that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="4149a-117">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="4149a-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4149a-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4149a-118">Child Elements</span></span>  
  
|<span data-ttu-id="4149a-119">Élément</span><span class="sxs-lookup"><span data-stu-id="4149a-119">Element</span></span>|<span data-ttu-id="4149a-120">Description</span><span class="sxs-lookup"><span data-stu-id="4149a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4149a-121">\<étendues ></span><span class="sxs-lookup"><span data-stu-id="4149a-121">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="4149a-122">Collection d’URI de portée pour le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4149a-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="4149a-123">Plusieurs URI de portée peuvent être associés au même point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4149a-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="4149a-124">[\<extensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [de \<endpointDiscovery >]</span><span class="sxs-lookup"><span data-stu-id="4149a-124">[\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="4149a-125">Collection d’éléments XML qui vous permet de spécifier des métadonnées personnalisées à publier pour un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4149a-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="4149a-126">\<types ></span><span class="sxs-lookup"><span data-stu-id="4149a-126">\<types></span></span>|<span data-ttu-id="4149a-127">Collection d’interfaces à rechercher.</span><span class="sxs-lookup"><span data-stu-id="4149a-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4149a-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4149a-128">Parent Elements</span></span>  
  
|<span data-ttu-id="4149a-129">Élément</span><span class="sxs-lookup"><span data-stu-id="4149a-129">Element</span></span>|<span data-ttu-id="4149a-130">Description</span><span class="sxs-lookup"><span data-stu-id="4149a-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4149a-131">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="4149a-131">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4149a-132">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="4149a-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="4149a-133">Notes</span><span class="sxs-lookup"><span data-stu-id="4149a-133">Remarks</span></span>  
 <span data-ttu-id="4149a-134">Lorsqu'il est ajouté à la configuration de comportement du point de terminaison et si le jeu d'attributs `enabled` a la valeur `true`, cet élément de configuration devient détectable.</span><span class="sxs-lookup"><span data-stu-id="4149a-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="4149a-135">En outre, vous pouvez utiliser la [ \<étendues >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)élément enfant à la spécification d’étendue personnalisée URI qui peut être utilisé pour filtrer des points de terminaison de service pendant la requête, ainsi que le [ \<extensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) élément enfant à spécifier des métadonnées personnalisées qui doivent être publiées, ainsi que les métadonnées détectables standard (EPR, ContractTypeName, BindingName, étendue et ListenURI).</span><span class="sxs-lookup"><span data-stu-id="4149a-135">In addition, you can use the [\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="4149a-136">Cet élément de configuration est dépendant de la [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) élément qui fournit le contrôle au niveau du service de découverte.</span><span class="sxs-lookup"><span data-stu-id="4149a-136">This configuration element is dependent on the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="4149a-137">Cela signifie que les paramètres de cet élément sont ignorés si [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) n’est pas présent dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="4149a-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4149a-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="4149a-138">Example</span></span>  
 <span data-ttu-id="4149a-139">L’exemple de configuration suivant spécifie des portées de filtrage et des métadonnées d’extension à publier pour un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4149a-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
```xml  
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
     <endpoint binding="basicHttpBinding"  
              address="calculator"  
              contract="ICalculatorService"  
              behaviorConfiguration="calculatorEndpointBehavior" />  
  </service>  
</services>  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDiscovery />  
    </behavior>  
  </serviceBehaviors>  
  <endpointBehaviors>  
    <behavior name="calculatorEndpointBehavior">  
      <endpointDiscovery enabled="true">  
        <scopes>  
          <add scope="http://contoso/test1"/>  
          <add scope="http://contoso/test2"/>  
        </scopes>  
        <extensions>  
          <e:Publisher xmlns:e="http://example.org">  
            <e:Name>The Example Organization</e:Name>  
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>  
            <e:Contact>support@example.org</e:Contact>  
          </e:Publisher>  
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>  
        </extensions>  
      </endpointDiscovery>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4149a-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4149a-140">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
