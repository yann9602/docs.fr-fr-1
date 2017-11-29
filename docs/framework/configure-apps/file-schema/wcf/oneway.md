---
title: '&lt;oneWay&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 79dd5dd0ca383cebc5f08f3e12c6c6261d11a02a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltonewaygt"></a><span data-ttu-id="ecad5-102">&lt;oneWay&gt;</span><span class="sxs-lookup"><span data-stu-id="ecad5-102">&lt;oneWay&gt;</span></span>
<span data-ttu-id="ecad5-103">Active le routage de paquets et l’utilisation de méthodes unidirectionnelles pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="ecad5-103">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="ecad5-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ecad5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ecad5-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="ecad5-105">\<bindings></span></span>  
<span data-ttu-id="ecad5-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ecad5-106">\<customBinding></span></span>  
<span data-ttu-id="ecad5-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="ecad5-107">\<binding></span></span>  
<span data-ttu-id="ecad5-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="ecad5-108">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecad5-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecad5-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">  
        <channelPoolSettings  
           idleTimeout"TimeSpan"  
          leaseTimeout"TimeSpan"  
          maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
```xml  
</oneWay>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecad5-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ecad5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ecad5-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ecad5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecad5-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="ecad5-112">Attributes</span></span>  
  
|<span data-ttu-id="ecad5-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="ecad5-113">Attribute</span></span>|<span data-ttu-id="ecad5-114">Description</span><span class="sxs-lookup"><span data-stu-id="ecad5-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="ecad5-115">Valeur booléenne qui spécifie si le routage de paquets est activé.</span><span class="sxs-lookup"><span data-stu-id="ecad5-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="ecad5-116">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="ecad5-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="ecad5-117">Entier qui spécifie le nombre maximal de canaux qui peuvent être acceptés.</span><span class="sxs-lookup"><span data-stu-id="ecad5-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecad5-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ecad5-118">Child Elements</span></span>  
  
|<span data-ttu-id="ecad5-119">Élément</span><span class="sxs-lookup"><span data-stu-id="ecad5-119">Element</span></span>|<span data-ttu-id="ecad5-120">Description</span><span class="sxs-lookup"><span data-stu-id="ecad5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecad5-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="ecad5-121">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="ecad5-122">Objet <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> qui contient des propriétés du pool de canaux pour le canal actuel.</span><span class="sxs-lookup"><span data-stu-id="ecad5-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ecad5-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ecad5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ecad5-124">Élément</span><span class="sxs-lookup"><span data-stu-id="ecad5-124">Element</span></span>|<span data-ttu-id="ecad5-125">Description</span><span class="sxs-lookup"><span data-stu-id="ecad5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecad5-126">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="ecad5-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="ecad5-127">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="ecad5-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecad5-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="ecad5-128">Remarks</span></span>  
 <span data-ttu-id="ecad5-129">Pour activer le routage de paquets, une couche de conversion unidirectionnelle est nécessaire (fournie par cet élément).</span><span class="sxs-lookup"><span data-stu-id="ecad5-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="ecad5-130">Un utilisateur peut créer une liaison personnalisée qui crée une couche pour cette liaison via un transport prenant en charge la session ou de type demande/réponse pour qu'elle puisse router les paquets.</span><span class="sxs-lookup"><span data-stu-id="ecad5-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="ecad5-131">Cet élément s'avère également utile lorsque vous souhaitez exposer des méthodes unidirectionnelles de façon plus native.</span><span class="sxs-lookup"><span data-stu-id="ecad5-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="ecad5-132">D'autres transformations peuvent être appliquées sur cette couche, comme le duplex composite et la messagerie fiable.</span><span class="sxs-lookup"><span data-stu-id="ecad5-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecad5-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecad5-133">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>  
 <xref:System.ServiceModel.Configuration.OneWayElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="ecad5-134">Liaisons</span><span class="sxs-lookup"><span data-stu-id="ecad5-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ecad5-135">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="ecad5-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="ecad5-136">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="ecad5-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="ecad5-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ecad5-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
