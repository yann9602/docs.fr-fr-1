---
title: '&lt;compositeDuplex&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80c8f3954cccbce8e93ab9d8c516fdfd6c7bff10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcompositeduplexgt"></a><span data-ttu-id="bd9ac-102">&lt;compositeDuplex&gt;</span><span class="sxs-lookup"><span data-stu-id="bd9ac-102">&lt;compositeDuplex&gt;</span></span>
<span data-ttu-id="bd9ac-103">Définit l’élément de liaison utilisé lorsque le client doit exposer un point de terminaison pour permettre au service de renvoyer des messages au client.</span><span class="sxs-lookup"><span data-stu-id="bd9ac-103">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="bd9ac-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="bd9ac-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bd9ac-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="bd9ac-105">\<bindings></span></span>  
<span data-ttu-id="bd9ac-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bd9ac-106">\<customBinding></span></span>  
<span data-ttu-id="bd9ac-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="bd9ac-107">\<binding></span></span>  
<span data-ttu-id="bd9ac-108">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="bd9ac-108">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd9ac-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd9ac-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd9ac-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bd9ac-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bd9ac-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bd9ac-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd9ac-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="bd9ac-112">Attributes</span></span>  
  
|<span data-ttu-id="bd9ac-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="bd9ac-113">Attribute</span></span>|<span data-ttu-id="bd9ac-114">Description</span><span class="sxs-lookup"><span data-stu-id="bd9ac-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd9ac-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="bd9ac-115">clientBaseAddress</span></span>|<span data-ttu-id="bd9ac-116">URI qui définit l'adresse du canal arrière en mode duplex.</span><span class="sxs-lookup"><span data-stu-id="bd9ac-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="bd9ac-117">Le service utilise cette adresse pour entrer en contact et établir une connexion avec le client.</span><span class="sxs-lookup"><span data-stu-id="bd9ac-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="bd9ac-118">Si cet attribut n’est pas défini, une adresse par défaut «`full qualified name+default port\TemporaryIndigoAddress\guid`» est générée.</span><span class="sxs-lookup"><span data-stu-id="bd9ac-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="bd9ac-119">La valeur par défaut est `null`.</span><span class="sxs-lookup"><span data-stu-id="bd9ac-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd9ac-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bd9ac-120">Child Elements</span></span>  
 <span data-ttu-id="bd9ac-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bd9ac-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd9ac-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bd9ac-122">Parent Elements</span></span>  
  
|<span data-ttu-id="bd9ac-123">Élément</span><span class="sxs-lookup"><span data-stu-id="bd9ac-123">Element</span></span>|<span data-ttu-id="bd9ac-124">Description</span><span class="sxs-lookup"><span data-stu-id="bd9ac-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd9ac-125">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="bd9ac-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="bd9ac-126">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="bd9ac-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd9ac-127">Notes</span><span class="sxs-lookup"><span data-stu-id="bd9ac-127">Remarks</span></span>  
 <span data-ttu-id="bd9ac-128">Cet élément de configuration est utilisé avec les transports qui n'autorisent pas de communications duplex en mode natif, par exemple, HTTP.</span><span class="sxs-lookup"><span data-stu-id="bd9ac-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="bd9ac-129">En revanche, TCP autorise nativement les communications duplex et ne requiert pas l'utilisation de cet élément de liaison pour permettre au service de renvoyer des messages à un client.</span><span class="sxs-lookup"><span data-stu-id="bd9ac-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="bd9ac-130">Le client doit exposer une adresse pour que le service puisse entrer en contact avec lui et établir une connexion.</span><span class="sxs-lookup"><span data-stu-id="bd9ac-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="bd9ac-131">Cette adresse cliente est fournie par l'attribut `clientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="bd9ac-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="bd9ac-132">Notez que Windows Communication Foundation (WCF) génère automatiquement un attribut ClientBaseAddress si aucun n'est explicitement défini par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bd9ac-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd9ac-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="bd9ac-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd9ac-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd9ac-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="bd9ac-135">Liaisons</span><span class="sxs-lookup"><span data-stu-id="bd9ac-135">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bd9ac-136">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="bd9ac-136">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="bd9ac-137">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="bd9ac-137">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="bd9ac-138">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bd9ac-138">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
