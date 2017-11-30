---
title: '&lt;webSocketSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2714b27916a47ae8e002ea857c93377736c4eff5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="89f3b-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="89f3b-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="89f3b-103">Élément de configuration utilisé pour spécifier des paramètres WebSocket.</span><span class="sxs-lookup"><span data-stu-id="89f3b-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="89f3b-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="89f3b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="89f3b-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="89f3b-105">\<bindings></span></span>  
<span data-ttu-id="89f3b-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="89f3b-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89f3b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89f3b-107">Syntax</span></span>  
  
```xml  
<netHttpBinding>  
  <binding>   
    <webSocketSettings createNotificationOnConnection="boolean" 
                       disablePayloadMasking="boolean" 
                       keepAliveInterval="TimeSpan" 
                       maxPendingConnections="Integer" 
                       receiveBufferSize="Integer" 
                       sendBufferSize="Integer" 
                       subProtocol="String" 
                       transportUsage="WhenDuplex/Always/Never"/>
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89f3b-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="89f3b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="89f3b-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="89f3b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89f3b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="89f3b-110">Attributes</span></span>  
  
|<span data-ttu-id="89f3b-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="89f3b-111">Attribute</span></span>|<span data-ttu-id="89f3b-112">Description</span><span class="sxs-lookup"><span data-stu-id="89f3b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89f3b-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="89f3b-113">createNotificationOnConnection</span></span>|<span data-ttu-id="89f3b-114">Spécifie si une notification est envoyée lors de la connexion.</span><span class="sxs-lookup"><span data-stu-id="89f3b-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="89f3b-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="89f3b-115">disablePayloadMasking</span></span>|<span data-ttu-id="89f3b-116">Spécifie si le masquage WebSocket est désactivé.</span><span class="sxs-lookup"><span data-stu-id="89f3b-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="89f3b-117">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="89f3b-117">keepAliveInterval</span></span>|<span data-ttu-id="89f3b-118">Spécifie l'intervalle de maintien de l'activité.</span><span class="sxs-lookup"><span data-stu-id="89f3b-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="89f3b-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="89f3b-119">maxPendingConnections</span></span>|<span data-ttu-id="89f3b-120">Spécifie le nombre maximal de connexions entrantes en attente de distribution sur le service.</span><span class="sxs-lookup"><span data-stu-id="89f3b-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="89f3b-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="89f3b-121">receiveBufferSize</span></span>|<span data-ttu-id="89f3b-122">Spécifie la taille de la mémoire tampon de réception.</span><span class="sxs-lookup"><span data-stu-id="89f3b-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="89f3b-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="89f3b-123">sendBufferSize</span></span>|<span data-ttu-id="89f3b-124">Spécifie la taille de la mémoire tampon d'envoi.</span><span class="sxs-lookup"><span data-stu-id="89f3b-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="89f3b-125">subProtocol</span><span class="sxs-lookup"><span data-stu-id="89f3b-125">subProtocol</span></span>|<span data-ttu-id="89f3b-126">Spécifie le sous-protocole WebSocket.</span><span class="sxs-lookup"><span data-stu-id="89f3b-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="89f3b-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="89f3b-127">transportUsage</span></span>|<span data-ttu-id="89f3b-128">Spécifie quand utiliser WebSocket.</span><span class="sxs-lookup"><span data-stu-id="89f3b-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="89f3b-129">Attribut transportUsage</span><span class="sxs-lookup"><span data-stu-id="89f3b-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="89f3b-130">Valeur</span><span class="sxs-lookup"><span data-stu-id="89f3b-130">Value</span></span>|<span data-ttu-id="89f3b-131">Description</span><span class="sxs-lookup"><span data-stu-id="89f3b-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89f3b-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="89f3b-132">WhenDuplex</span></span>|<span data-ttu-id="89f3b-133">Utilisez le protocole WebSocket lorsque le contrat est en duplex.</span><span class="sxs-lookup"><span data-stu-id="89f3b-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="89f3b-134">Always</span><span class="sxs-lookup"><span data-stu-id="89f3b-134">Always</span></span>|<span data-ttu-id="89f3b-135">Utilisez toujours le protocole WebSocket indépendamment du contrat.</span><span class="sxs-lookup"><span data-stu-id="89f3b-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="89f3b-136">Never</span><span class="sxs-lookup"><span data-stu-id="89f3b-136">Never</span></span>|<span data-ttu-id="89f3b-137">N'utilisez jamais le protocole WebSocket.</span><span class="sxs-lookup"><span data-stu-id="89f3b-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89f3b-138">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="89f3b-138">Child Elements</span></span>  
 <span data-ttu-id="89f3b-139">None</span><span class="sxs-lookup"><span data-stu-id="89f3b-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89f3b-140">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="89f3b-140">Parent Elements</span></span>  
  
|<span data-ttu-id="89f3b-141">Élément</span><span class="sxs-lookup"><span data-stu-id="89f3b-141">Element</span></span>|<span data-ttu-id="89f3b-142">Description</span><span class="sxs-lookup"><span data-stu-id="89f3b-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89f3b-143">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="89f3b-143">\<netHttpBinding></span></span>|<span data-ttu-id="89f3b-144">Spécifie le NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="89f3b-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="89f3b-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="89f3b-145">Example</span></span>  
 <span data-ttu-id="89f3b-146">L’exemple suivant montre comment utiliser le \<webSocketSettings > élément.</span><span class="sxs-lookup"><span data-stu-id="89f3b-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>  
        <binding>  
          <webSocketSettings createNotificationOnConnection="true"  
                              disablePayloadMasking="false  
                              keepAliveInterval="00:10:00"  
                              maxPendingConnections="100"  
                              receiveBufferSize="1000"  
                              sendBufferSize="1000"  
                              subProtocol="Soap"  
                              transportUsage="WhenDuplex/Always/Never"/>  
  
        </binding>  
      </netHttpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="89f3b-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89f3b-147">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="89f3b-148">Liaisons</span><span class="sxs-lookup"><span data-stu-id="89f3b-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="89f3b-149">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="89f3b-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="89f3b-150">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="89f3b-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="89f3b-151">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="89f3b-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
