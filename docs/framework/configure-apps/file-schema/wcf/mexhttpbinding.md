---
title: '&lt;mexHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92e6054845a4f898c595e6b647ea3edeaf7d6114
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ltmexhttpbindinggt"></a><span data-ttu-id="a8b3b-102">&lt;mexHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="a8b3b-102">&lt;mexHttpBinding&gt;</span></span>
<span data-ttu-id="a8b3b-103">Spécifie les paramètres pour une liaison utilisée dans le cadre de l’échange de messages WS-MetadataExchange (WS-MEX) sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
 <span data-ttu-id="a8b3b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a8b3b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a8b3b-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a8b3b-105">\<bindings></span></span>  
<span data-ttu-id="a8b3b-106">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a8b3b-106">\<mexHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8b3b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8b3b-107">Syntax</span></span>  
  
```xml  
<mexHttpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8b3b-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a8b3b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a8b3b-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8b3b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="a8b3b-110">Attributes</span></span>  
  
|<span data-ttu-id="a8b3b-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="a8b3b-111">Attribute</span></span>|<span data-ttu-id="a8b3b-112">Description</span><span class="sxs-lookup"><span data-stu-id="a8b3b-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="a8b3b-113"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="a8b3b-114">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a8b3b-115">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="a8b3b-116">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="a8b3b-117">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="a8b3b-118">Chaque liaison porte un `name` et a un attribut `namespace` qui l'identifient de façon unique dans les métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="a8b3b-119">De plus, ce nom est unique parmi les liaisons du même type.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="a8b3b-120">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a8b3b-121">Pour plus d’informations sur la configuration par défaut et nommées liaisons et comportements, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [simplifié la Configuration des Services WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a8b3b-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="a8b3b-122"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="a8b3b-123">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a8b3b-124">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="a8b3b-125"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="a8b3b-126">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a8b3b-127">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="a8b3b-128"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="a8b3b-129">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a8b3b-130">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8b3b-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a8b3b-131">Child Elements</span></span>  
 <span data-ttu-id="a8b3b-132">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8b3b-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a8b3b-133">Parent Elements</span></span>  
  
|<span data-ttu-id="a8b3b-134">Élément</span><span class="sxs-lookup"><span data-stu-id="a8b3b-134">Element</span></span>|<span data-ttu-id="a8b3b-135">Description</span><span class="sxs-lookup"><span data-stu-id="a8b3b-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8b3b-136">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a8b3b-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="a8b3b-137">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8b3b-138">Notes</span><span class="sxs-lookup"><span data-stu-id="a8b3b-138">Remarks</span></span>  
 <span data-ttu-id="a8b3b-139">Cette liaison est essentiellement une liaison `WSHttpBinding` dont la sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-139">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="a8b3b-140">Elle prend en charge la plupart des demandes de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="a8b3b-140">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8b3b-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8b3b-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpBindingElement>  
 [<span data-ttu-id="a8b3b-142">Guide pratique pour publier les métadonnées d’un service à l’aide d’un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="a8b3b-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="a8b3b-143">Publication et récupération de métadonnées sur une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="a8b3b-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="a8b3b-144">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="a8b3b-144">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="a8b3b-145">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a8b3b-145">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a8b3b-146">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="a8b3b-146">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a8b3b-147">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a8b3b-147">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a8b3b-148">\<binding></span><span class="sxs-lookup"><span data-stu-id="a8b3b-148">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
