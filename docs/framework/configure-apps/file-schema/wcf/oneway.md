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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be70abe745879b5d6f6e8cdde802a6403f90174b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltonewaygt"></a><span data-ttu-id="32a09-102">&lt;oneWay&gt;</span><span class="sxs-lookup"><span data-stu-id="32a09-102">&lt;oneWay&gt;</span></span>
<span data-ttu-id="32a09-103">Active le routage de paquets et l’utilisation de méthodes unidirectionnelles pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="32a09-103">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="32a09-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="32a09-104">\<system.serviceModel></span></span>  
<span data-ttu-id="32a09-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="32a09-105">\<bindings></span></span>  
<span data-ttu-id="32a09-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="32a09-106">\<customBinding></span></span>  
<span data-ttu-id="32a09-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="32a09-107">\<binding></span></span>  
<span data-ttu-id="32a09-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="32a09-108">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32a09-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32a09-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32a09-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="32a09-110">Attributes and Elements</span></span>  
 <span data-ttu-id="32a09-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="32a09-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32a09-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="32a09-112">Attributes</span></span>  
  
|<span data-ttu-id="32a09-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="32a09-113">Attribute</span></span>|<span data-ttu-id="32a09-114">Description</span><span class="sxs-lookup"><span data-stu-id="32a09-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="32a09-115">Valeur booléenne qui spécifie si le routage de paquets est activé.</span><span class="sxs-lookup"><span data-stu-id="32a09-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="32a09-116">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="32a09-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="32a09-117">Entier qui spécifie le nombre maximal de canaux qui peuvent être acceptés.</span><span class="sxs-lookup"><span data-stu-id="32a09-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32a09-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="32a09-118">Child Elements</span></span>  
  
|<span data-ttu-id="32a09-119">Élément</span><span class="sxs-lookup"><span data-stu-id="32a09-119">Element</span></span>|<span data-ttu-id="32a09-120">Description</span><span class="sxs-lookup"><span data-stu-id="32a09-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32a09-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="32a09-121">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="32a09-122">Objet <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> qui contient des propriétés du pool de canaux pour le canal actuel.</span><span class="sxs-lookup"><span data-stu-id="32a09-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32a09-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="32a09-123">Parent Elements</span></span>  
  
|<span data-ttu-id="32a09-124">Élément</span><span class="sxs-lookup"><span data-stu-id="32a09-124">Element</span></span>|<span data-ttu-id="32a09-125">Description</span><span class="sxs-lookup"><span data-stu-id="32a09-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32a09-126">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="32a09-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="32a09-127">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="32a09-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32a09-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="32a09-128">Remarks</span></span>  
 <span data-ttu-id="32a09-129">Pour activer le routage de paquets, une couche de conversion unidirectionnelle est nécessaire (fournie par cet élément).</span><span class="sxs-lookup"><span data-stu-id="32a09-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="32a09-130">Un utilisateur peut créer une liaison personnalisée qui crée une couche pour cette liaison via un transport prenant en charge la session ou de type demande/réponse pour qu'elle puisse router les paquets.</span><span class="sxs-lookup"><span data-stu-id="32a09-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="32a09-131">Cet élément s'avère également utile lorsque vous souhaitez exposer des méthodes unidirectionnelles de façon plus native.</span><span class="sxs-lookup"><span data-stu-id="32a09-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="32a09-132">D'autres transformations peuvent être appliquées sur cette couche, comme le duplex composite et la messagerie fiable.</span><span class="sxs-lookup"><span data-stu-id="32a09-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a09-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32a09-133">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>  
 <xref:System.ServiceModel.Configuration.OneWayElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="32a09-134">Liaisons</span><span class="sxs-lookup"><span data-stu-id="32a09-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="32a09-135">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="32a09-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="32a09-136">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="32a09-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="32a09-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="32a09-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
