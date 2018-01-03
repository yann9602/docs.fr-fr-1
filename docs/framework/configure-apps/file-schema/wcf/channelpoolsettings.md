---
title: '&lt;channelPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09496add0adcc11756b6aae01a0236fe590f819f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltchannelpoolsettingsgt"></a><span data-ttu-id="fd9a5-102">&lt;channelPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="fd9a5-102">&lt;channelPoolSettings&gt;</span></span>
<span data-ttu-id="fd9a5-103">Spécifie les paramètres du pool du canal pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-103">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="fd9a5-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="fd9a5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fd9a5-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="fd9a5-105">\<bindings></span></span>  
<span data-ttu-id="fd9a5-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="fd9a5-106">\<customBinding></span></span>  
<span data-ttu-id="fd9a5-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="fd9a5-107">\<binding></span></span>  
<span data-ttu-id="fd9a5-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="fd9a5-108">\<oneWay></span></span>  
<span data-ttu-id="fd9a5-109">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="fd9a5-109">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd9a5-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd9a5-110">Syntax</span></span>  
  
```xml  
<channelPoolSettings  
    idleTimeout"TimeSpan"  
        leaseTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd9a5-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fd9a5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fd9a5-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd9a5-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="fd9a5-113">Attributes</span></span>  
  
|<span data-ttu-id="fd9a5-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="fd9a5-114">Attribute</span></span>|<span data-ttu-id="fd9a5-115">Description</span><span class="sxs-lookup"><span data-stu-id="fd9a5-115">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="fd9a5-116"><xref:System.TimeSpan> positif qui spécifie la période maximale d'inactivité des canaux du pool avant leur déconnexion.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-116">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="fd9a5-117">La valeur par défaut est 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-117">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="fd9a5-118"><xref:System.TimeSpan> qui spécifie l'intervalle de temps après lequel un canal, lorsqu'il est retourné au pool, est fermé.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-118">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="fd9a5-119">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-119">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="fd9a5-120">Entier positif qui spécifie le nombre maximal de canaux qui peuvent être stockés dans le pool pour chaque point de terminaison distant.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-120">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="fd9a5-121">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-121">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd9a5-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fd9a5-122">Child Elements</span></span>  
 <span data-ttu-id="fd9a5-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd9a5-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fd9a5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fd9a5-125">Élément</span><span class="sxs-lookup"><span data-stu-id="fd9a5-125">Element</span></span>|<span data-ttu-id="fd9a5-126">Description</span><span class="sxs-lookup"><span data-stu-id="fd9a5-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd9a5-127">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="fd9a5-127">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="fd9a5-128">Active le routage de paquets pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-128">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd9a5-129">Notes</span><span class="sxs-lookup"><span data-stu-id="fd9a5-129">Remarks</span></span>  
 <span data-ttu-id="fd9a5-130">Les quotas sont utilisés comme un mécanisme de stratégie pour empêcher une consommation excessive de ressources.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-130">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="fd9a5-131">Ils empêchent les attaques par déni de service (DOS) qui sont malveillantes ou involontaires.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-131">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="fd9a5-132">Utilisez cet élément lors de la définition de quotas de canal sur un canal personnalisé.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-132">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="fd9a5-133">`ChannelPoolSettings` spécifie trois quotas :</span><span class="sxs-lookup"><span data-stu-id="fd9a5-133">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
-   <span data-ttu-id="fd9a5-134">Le quota `idleTimeout` est utilisé pour atténuer des attaques par déni de service (DOS) sur le serveur qui monopolise des ressources sur une longue période.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-134">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="fd9a5-135">Sur le client, la définition de la valeur correcte peut augmenter la fiabilité de la connexion avec le service.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-135">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="fd9a5-136">La valeur par défaut est basée sur une allocation habituellement modeste de ressources.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-136">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="fd9a5-137">Cette valeur convient pour un environnement de développement et pour de petits scénarios d'installation.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-137">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="fd9a5-138">Les administrateurs de service doivent examiner la valeur si une installation manque de ressources ou si les connexions sont limitées malgré la présence de ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-138">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="fd9a5-139">Le quota `leaseTimeout` est utilisé pour l'intégration avec les programmes d'équilibrage de charge et pour l'amélioration de la fiabilité.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-139">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="fd9a5-140">La valeur par défaut est basée sur une allocation classique de ressources.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-140">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="fd9a5-141">Cette valeur convient pour un environnement de développement et pour de petits scénarios d'installation.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-141">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="fd9a5-142">Les administrateurs de service doivent examiner la valeur si une installation manque de ressources ou si les connexions sont limitées malgré la présence de ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-142">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="fd9a5-143">Le quota `maxOutboundChannelsPerEndpoint` définit des limites de cache sur le serveur et le client et est utilisé pour améliorer la fiabilité.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-143">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="fd9a5-144">La valeur par défaut est basée $$sur une allocation habituellement modeste des ressources qui sont appropriées pour un environnement de développement et de petits scénarios d'installation.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-144">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="fd9a5-145">Les administrateurs de service doivent examiner la valeur si une installation manque de ressources ou si les connexions sont limitées malgré la présence de ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="fd9a5-145">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd9a5-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd9a5-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>  
 <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="fd9a5-147">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="fd9a5-147">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)  
 [<span data-ttu-id="fd9a5-148">Liaisons</span><span class="sxs-lookup"><span data-stu-id="fd9a5-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="fd9a5-149">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="fd9a5-149">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="fd9a5-150">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="fd9a5-150">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="fd9a5-151">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="fd9a5-151">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
