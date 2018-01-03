---
title: '&lt;NET.TCP&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a3d22b6feef80dbff8c7f20b130ce2b0f9702c9e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnettcpgt"></a><span data-ttu-id="7c8e3-102">&lt;NET.TCP&gt;</span><span class="sxs-lookup"><span data-stu-id="7c8e3-102">&lt;net.tcp&gt;</span></span>
<span data-ttu-id="7c8e3-103">Spécifie les paramètres de configuration du service de partage de port NET.TCP, qui permet à plusieurs processus de partager le même port TCP.</span><span class="sxs-lookup"><span data-stu-id="7c8e3-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
 <span data-ttu-id="7c8e3-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="7c8e3-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="7c8e3-105">\<NET.TCP ></span><span class="sxs-lookup"><span data-stu-id="7c8e3-105">\<net.tcp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c8e3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c8e3-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="Integer"  
          maxPendingAccepts="Integer"  
          maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan"  
          teredoEnabled="Boolean">  
          <allowAccounts>  
             <!-- LocalSystem account -->   
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->   
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->   
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->   
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only)-->   
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="7c8e3-107">Type</span><span class="sxs-lookup"><span data-stu-id="7c8e3-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c8e3-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7c8e3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7c8e3-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7c8e3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c8e3-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="7c8e3-110">Attributes</span></span>  
  
|<span data-ttu-id="7c8e3-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="7c8e3-111">Attribute</span></span>|<span data-ttu-id="7c8e3-112">Description</span><span class="sxs-lookup"><span data-stu-id="7c8e3-112">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="7c8e3-113">Entier qui spécifie le nombre maximal de connexions en attente qui sont acceptées à partir de la connexion partagée, mais qui ne sont pas encore distribuées aux services [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7c8e3-113">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span> <span data-ttu-id="7c8e3-114">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="7c8e3-114">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="7c8e3-115">Entier qui spécifie le nombre maximal de threads d'acceptation simultanés en attente sur le point de terminaison d'écoute du service de partage.</span><span class="sxs-lookup"><span data-stu-id="7c8e3-115">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="7c8e3-116">La valeur par défaut est 2.</span><span class="sxs-lookup"><span data-stu-id="7c8e3-116">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="7c8e3-117">Nombre maximal de connexions que l'écouteur peut mettre en attente d'acceptation par l'application.</span><span class="sxs-lookup"><span data-stu-id="7c8e3-117">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="7c8e3-118">Lorsque cette valeur de quota est dépassée, les nouvelles connexions entrantes sont supprimées plutôt que mises en attente d'acceptation.</span><span class="sxs-lookup"><span data-stu-id="7c8e3-118">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="7c8e3-119">Les fonctionnalités de connexion telles que la sécurité des messages peuvent entraîner qu'un client ouvre plusieurs connexions.</span><span class="sxs-lookup"><span data-stu-id="7c8e3-119">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="7c8e3-120">Les administrateurs de service doivent prendre en compte ces connexions supplémentaires lors de la définition de cette valeur de quota.</span><span class="sxs-lookup"><span data-stu-id="7c8e3-120">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="7c8e3-121">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="7c8e3-121">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="7c8e3-122">`TimeSpan` qui spécifie le délai d'attente pour lire les données d'encadrement et effectuer la distribution de la connexion à partir des connexions sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="7c8e3-122">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="7c8e3-123">La valeur par défaut est « 00:00:10 ».</span><span class="sxs-lookup"><span data-stu-id="7c8e3-123">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="7c8e3-124">Valeur booléenne qui indique si le service de partage de port utilise le service Microsoft Teredo pour écouter les ports TCP pour le compte des services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7c8e3-124">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="7c8e3-125">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="7c8e3-125">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c8e3-126">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7c8e3-126">Child Elements</span></span>  
  
|<span data-ttu-id="7c8e3-127">Élément</span><span class="sxs-lookup"><span data-stu-id="7c8e3-127">Element</span></span>|<span data-ttu-id="7c8e3-128">Description</span><span class="sxs-lookup"><span data-stu-id="7c8e3-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c8e3-129">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="7c8e3-129">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="7c8e3-130">Collection d'éléments de configuration qui contiennent un attribut `securityIdentifier` permettant de spécifier les comptes d'utilisateurs correspondant aux processus qui hébergent des services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] et qui disposent d'un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="7c8e3-130">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7c8e3-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7c8e3-131">Parent Elements</span></span>  
  
|<span data-ttu-id="7c8e3-132">Élément</span><span class="sxs-lookup"><span data-stu-id="7c8e3-132">Element</span></span>|<span data-ttu-id="7c8e3-133">Description</span><span class="sxs-lookup"><span data-stu-id="7c8e3-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c8e3-134">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="7c8e3-134">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="7c8e3-135">Contient les paramètres de configuration du processus de l'écouteur SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="7c8e3-135">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c8e3-136">Notes</span><span class="sxs-lookup"><span data-stu-id="7c8e3-136">Remarks</span></span>  
 <span data-ttu-id="7c8e3-137">Pour plus d’informations sur le partage de ports, consultez [le partage de ports Net.TCP](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded).</span><span class="sxs-lookup"><span data-stu-id="7c8e3-137">For more information on port sharing, see [Net.TCP Port Sharing](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded).</span></span> <span data-ttu-id="7c8e3-138">Pour comprendre comment configurer le service de partage de ports, consultez [configurer le Service de partage de ports Net.TCP](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).</span><span class="sxs-lookup"><span data-stu-id="7c8e3-138">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c8e3-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c8e3-139">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>  
 [<span data-ttu-id="7c8e3-140">Partage de ports Net.TCP</span><span class="sxs-lookup"><span data-stu-id="7c8e3-140">Net.TCP Port Sharing</span></span>](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded)  
 [<span data-ttu-id="7c8e3-141">Configuration du service de partage de ports Net.TCP</span><span class="sxs-lookup"><span data-stu-id="7c8e3-141">Configuring the Net.TCP Port Sharing Service</span></span>](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)
