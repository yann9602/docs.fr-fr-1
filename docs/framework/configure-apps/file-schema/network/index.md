---
title: "Schéma des paramètres réseau"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ca4a0000d85c8fbac9a723beeda51f9c7886ed8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="network-settings-schema"></a><span data-ttu-id="b96e2-102">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="b96e2-102">Network Settings Schema</span></span>
<span data-ttu-id="b96e2-103">Les paramètres réseau spécifient la façon dont le .NET Framework se connecte à Internet.</span><span class="sxs-lookup"><span data-stu-id="b96e2-103">Network settings specify how the .NET Framework connects to the Internet.</span></span> <span data-ttu-id="b96e2-104">Le tableau suivant décrit la fonction de chaque élément de configuration enfant sous [\<system.Net>, élément (paramètres réseau)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="b96e2-104">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="b96e2-105">Élément</span><span class="sxs-lookup"><span data-stu-id="b96e2-105">Element</span></span>|<span data-ttu-id="b96e2-106">Description</span><span class="sxs-lookup"><span data-stu-id="b96e2-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b96e2-107">\<authenticationModules, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b96e2-107">\<authenticationModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="b96e2-108">Spécifie les modules utilisés pour authentifier les requêtes Internet.</span><span class="sxs-lookup"><span data-stu-id="b96e2-108">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="b96e2-109">\<connectionManagement>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b96e2-109">\<connectionManagement> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="b96e2-110">Spécifie le nombre maximal de connexions à destination des hôtes Internet.</span><span class="sxs-lookup"><span data-stu-id="b96e2-110">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="b96e2-111">\<defaultProxy>, élément(paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b96e2-111">\<defaultProxy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="b96e2-112">Spécifie le serveur proxy utilisé pour les requêtes HTTP à destination d’Internet.</span><span class="sxs-lookup"><span data-stu-id="b96e2-112">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="b96e2-113">\<mailSettings>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b96e2-113">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="b96e2-114">Contient les paramètres des options d’envoi de courrier.</span><span class="sxs-lookup"><span data-stu-id="b96e2-114">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="b96e2-115">\<requestCaching>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b96e2-115">\<requestCaching> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="b96e2-116">Spécifie les modules utilisés pour demander des informations à partir des hôtes Internet.</span><span class="sxs-lookup"><span data-stu-id="b96e2-116">Specifies the modules used to request information from Internet hosts.</span></span>|  
|[<span data-ttu-id="b96e2-117">\<requestCaching>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b96e2-117">\<requestCaching> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="b96e2-118">Configure les options réseau de base pour l’espace de noms <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b96e2-118">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>|  
|[<span data-ttu-id="b96e2-119">\<webRequestModules>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b96e2-119">\<webRequestModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="b96e2-120">Spécifie les modules utilisés pour demander des informations à partir des hôtes Internet.</span><span class="sxs-lookup"><span data-stu-id="b96e2-120">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
 <span data-ttu-id="b96e2-121">Les paramètres d’URI spécifient la façon dont le .NET Framework gère les adresses web exprimées à l’aide d’URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="b96e2-121">Uri settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="b96e2-122">Le tableau suivant décrit la fonction de chaque élément de configuration enfant sous [\<Uri>, élément (paramètres d’Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="b96e2-122">The following table describes the function of each child configuration element under the [\<Uri> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="b96e2-123">Élément</span><span class="sxs-lookup"><span data-stu-id="b96e2-123">Element</span></span>|<span data-ttu-id="b96e2-124">Description</span><span class="sxs-lookup"><span data-stu-id="b96e2-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b96e2-125">\<idn>, élément (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="b96e2-125">\<idn> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="b96e2-126">Spécifie si l’analyse de nom de domaine international (IDN) s’applique aux noms de domaine.</span><span class="sxs-lookup"><span data-stu-id="b96e2-126">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="b96e2-127">\<iriParsing>, élément (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="b96e2-127">\<iriParsing> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="b96e2-128">Spécifie si l’analyse d’identificateur de ressource internationale (IRI) s’applique à un <xref:System.Uri> et si les règles d’analyse IRI doivent s’appliquer.</span><span class="sxs-lookup"><span data-stu-id="b96e2-128">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="b96e2-129">\<schemeSettings, élément (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="b96e2-129">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="b96e2-130">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="b96e2-130">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b96e2-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b96e2-131">See Also</span></span>  
 [<span data-ttu-id="b96e2-132">Configuration des applications Internet</span><span class="sxs-lookup"><span data-stu-id="b96e2-132">Configuring Internet Applications</span></span>](../../../../../docs/framework/network-programming/configuring-internet-applications.md)  
 [<span data-ttu-id="b96e2-133">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b96e2-133">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
