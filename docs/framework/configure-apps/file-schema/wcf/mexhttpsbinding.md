---
title: '&lt;mexHttpsBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e259eec6fcbf34bf4e6f175f47a62d91f951206
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmexhttpsbindinggt"></a><span data-ttu-id="86e2a-102">&lt;mexHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="86e2a-102">&lt;mexHttpsBinding&gt;</span></span>
<span data-ttu-id="86e2a-103">Spécifie les paramètres pour une liaison utilisée dans le cadre de l’échange de messages WS-MetadataExchange (WS-MEX) sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="86e2a-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="86e2a-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="86e2a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="86e2a-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="86e2a-105">\<bindings></span></span>  
<span data-ttu-id="86e2a-106">\<mexHttpsBinding ></span><span class="sxs-lookup"><span data-stu-id="86e2a-106">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86e2a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86e2a-107">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexHttpsBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86e2a-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="86e2a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="86e2a-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="86e2a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86e2a-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="86e2a-110">Attributes</span></span>  
  
|<span data-ttu-id="86e2a-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="86e2a-111">Attribute</span></span>|<span data-ttu-id="86e2a-112">Description</span><span class="sxs-lookup"><span data-stu-id="86e2a-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="86e2a-113"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="86e2a-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="86e2a-114">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="86e2a-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="86e2a-115">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="86e2a-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="86e2a-116">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="86e2a-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="86e2a-117">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="86e2a-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="86e2a-118">Chaque liaison porte un `name` et a un attribut `namespace` qui l'identifient de façon unique dans les métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="86e2a-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="86e2a-119">De plus, ce nom est unique parmi les liaisons du même type.</span><span class="sxs-lookup"><span data-stu-id="86e2a-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="86e2a-120">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="86e2a-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="86e2a-121">Pour plus d’informations sur la configuration par défaut et nommées liaisons et comportements, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [simplifié la Configuration des Services WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="86e2a-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="86e2a-122"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="86e2a-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="86e2a-123">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="86e2a-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="86e2a-124">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="86e2a-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="86e2a-125"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="86e2a-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="86e2a-126">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="86e2a-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="86e2a-127">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="86e2a-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="86e2a-128"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="86e2a-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="86e2a-129">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="86e2a-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="86e2a-130">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="86e2a-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86e2a-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="86e2a-131">Child Elements</span></span>  
 <span data-ttu-id="86e2a-132">Aucun.</span><span class="sxs-lookup"><span data-stu-id="86e2a-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86e2a-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="86e2a-133">Parent Elements</span></span>  
  
|<span data-ttu-id="86e2a-134">Élément</span><span class="sxs-lookup"><span data-stu-id="86e2a-134">Element</span></span>|<span data-ttu-id="86e2a-135">Description</span><span class="sxs-lookup"><span data-stu-id="86e2a-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86e2a-136">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="86e2a-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="86e2a-137">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="86e2a-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86e2a-138">Remarques</span><span class="sxs-lookup"><span data-stu-id="86e2a-138">Remarks</span></span>  
 <span data-ttu-id="86e2a-139">Cette liaison est essentiellement une liaison `WSHttpBinding` qui prend en charge la sécurité au niveau du transport à l'aide de certificats.</span><span class="sxs-lookup"><span data-stu-id="86e2a-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="86e2a-140">Pour plus d’informations sur la configuration et à l’aide de ce un point de terminaison de métadonnées, consultez [Comment : configurer une liaison de personnalisé WS-Metadata Exchange](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [Comment : récupérer des métadonnées sur une liaison non - MEX](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)et le exemple [personnalisé sécuriser les métadonnées de point de terminaison](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="86e2a-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e2a-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86e2a-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>  
 [<span data-ttu-id="86e2a-142">Comment : publier des métadonnées pour un Service à l’aide d’un fichier de Configuration</span><span class="sxs-lookup"><span data-stu-id="86e2a-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="86e2a-143">Publication et la récupération des métadonnées sur une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="86e2a-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="86e2a-144">Comment : configurer un WS-Metadata personnalisée liaison d’échange</span><span class="sxs-lookup"><span data-stu-id="86e2a-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [<span data-ttu-id="86e2a-145">Comment : récupérer des métadonnées sur une liaison non - MEX</span><span class="sxs-lookup"><span data-stu-id="86e2a-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)  
 [<span data-ttu-id="86e2a-146">Point de terminaison de métadonnées de sécurisé personnalisée</span><span class="sxs-lookup"><span data-stu-id="86e2a-146">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 [<span data-ttu-id="86e2a-147">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="86e2a-147">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="86e2a-148">Liaisons</span><span class="sxs-lookup"><span data-stu-id="86e2a-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="86e2a-149">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="86e2a-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="86e2a-150">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="86e2a-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="86e2a-151">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="86e2a-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
