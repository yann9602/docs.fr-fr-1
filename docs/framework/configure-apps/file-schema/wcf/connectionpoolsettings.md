---
title: '&lt;connectionPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11500830c7c5fd75a9e2880a5875bd21fb070634
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltconnectionpoolsettingsgt"></a><span data-ttu-id="87dcd-102">&lt;connectionPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="87dcd-102">&lt;connectionPoolSettings&gt;</span></span>
<span data-ttu-id="87dcd-103">Spécifie des paramètres de pool de connexions supplémentaires pour une liaison de canal nommé.</span><span class="sxs-lookup"><span data-stu-id="87dcd-103">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="87dcd-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="87dcd-104">\<system.serviceModel></span></span>  
<span data-ttu-id="87dcd-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="87dcd-105">\<bindings></span></span>  
<span data-ttu-id="87dcd-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="87dcd-106">\<customBinding></span></span>  
<span data-ttu-id="87dcd-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="87dcd-107">\<binding></span></span>  
<span data-ttu-id="87dcd-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="87dcd-108">\<namePipeTransport></span></span>  
<span data-ttu-id="87dcd-109">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="87dcd-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87dcd-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87dcd-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings  
        groupName="String"  
    idleTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87dcd-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="87dcd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="87dcd-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="87dcd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87dcd-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="87dcd-113">Attributes</span></span>  
  
|<span data-ttu-id="87dcd-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="87dcd-114">Attribute</span></span>|<span data-ttu-id="87dcd-115">Description</span><span class="sxs-lookup"><span data-stu-id="87dcd-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="87dcd-116">Chaîne qui définit le nom du pool de connexions utilisé pour les canaux sortants.</span><span class="sxs-lookup"><span data-stu-id="87dcd-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="87dcd-117">En mode de transmission continu, les connexions ne sont pas partagées, ce qui signifie que la mise en pool des connexions est désactivée.</span><span class="sxs-lookup"><span data-stu-id="87dcd-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="87dcd-118">La valeur par défaut est une chaîne par défaut.</span><span class="sxs-lookup"><span data-stu-id="87dcd-118">The default is a "default" string.</span></span> <span data-ttu-id="87dcd-119">Vous pouvez modifier cette valeur pour isoler les connexions d'un client particulier dans des groupes séparés.</span><span class="sxs-lookup"><span data-stu-id="87dcd-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="87dcd-120"><xref:System.TimeSpan> positif qui spécifie la période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.</span><span class="sxs-lookup"><span data-stu-id="87dcd-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="87dcd-121">La valeur par défaut est 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="87dcd-121">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="87dcd-122">Entier positif qui spécifie le nombre maximal de connexions à un point de terminaison distant initié par le service.</span><span class="sxs-lookup"><span data-stu-id="87dcd-122">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="87dcd-123">Toute connexion dépassant cette limite est mise en file d'attente jusqu'à ce qu'une place se libère.</span><span class="sxs-lookup"><span data-stu-id="87dcd-123">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="87dcd-124">`idleTimeout` limite la durée pendant laquelle les connexions restent dans la file d'attente avant qu'une exception soit levée.</span><span class="sxs-lookup"><span data-stu-id="87dcd-124">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="87dcd-125">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="87dcd-125">The default is 10.</span></span><br /><br /> <span data-ttu-id="87dcd-126">Cet attribut limite le nombre de connexions actives simultanées entre le client et un point de terminaison de service particulier.</span><span class="sxs-lookup"><span data-stu-id="87dcd-126">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="87dcd-127">Si cette valeur est dépassée, il est possible que le service ne semble pas répondre au client.</span><span class="sxs-lookup"><span data-stu-id="87dcd-127">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="87dcd-128">Dans ce cas, cette valeur doit être ajustée de façon à être supérieure au nombre maximal de connexions simultanées prévues à un point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="87dcd-128">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87dcd-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="87dcd-129">Child Elements</span></span>  
 <span data-ttu-id="87dcd-130">Aucun.</span><span class="sxs-lookup"><span data-stu-id="87dcd-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87dcd-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="87dcd-131">Parent Elements</span></span>  
  
|<span data-ttu-id="87dcd-132">Élément</span><span class="sxs-lookup"><span data-stu-id="87dcd-132">Element</span></span>|<span data-ttu-id="87dcd-133">Description</span><span class="sxs-lookup"><span data-stu-id="87dcd-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87dcd-134">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="87dcd-134">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="87dcd-135">Définit un transport qui entraîne un canal à transférer des messages à l'aide de canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="87dcd-135">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87dcd-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87dcd-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="87dcd-137">Transports</span><span class="sxs-lookup"><span data-stu-id="87dcd-137">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="87dcd-138">Choix d’un transport</span><span class="sxs-lookup"><span data-stu-id="87dcd-138">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="87dcd-139">Liaisons</span><span class="sxs-lookup"><span data-stu-id="87dcd-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="87dcd-140">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="87dcd-140">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="87dcd-141">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="87dcd-141">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="87dcd-142">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="87dcd-142">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
