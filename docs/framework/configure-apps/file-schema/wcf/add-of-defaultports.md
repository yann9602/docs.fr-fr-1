---
title: '&lt;add&gt; de &lt;defaultPorts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2aa63c7a5e730b2fb45f614cb2fe5f88444cee4a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="e8b31-102">&lt;add&gt; de &lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="e8b31-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="e8b31-103">Point de terminaison de communication par défaut écouté par l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="e8b31-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="e8b31-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e8b31-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e8b31-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="e8b31-105">\<behaviors></span></span>  
<span data-ttu-id="e8b31-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e8b31-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e8b31-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="e8b31-107">\<behavior></span></span>  
<span data-ttu-id="e8b31-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="e8b31-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="e8b31-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="e8b31-109">\<defaultPorts></span></span>  
<span data-ttu-id="e8b31-110">\<add></span><span class="sxs-lookup"><span data-stu-id="e8b31-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8b31-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8b31-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>   <defaultPorts>      <add port="Integer" scheme="String" />   </defaultPorts></useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8b31-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e8b31-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e8b31-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e8b31-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8b31-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="e8b31-114">Attributes</span></span>  
  
|<span data-ttu-id="e8b31-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="e8b31-115">Attribute</span></span>|<span data-ttu-id="e8b31-116">Description</span><span class="sxs-lookup"><span data-stu-id="e8b31-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8b31-117">port</span><span class="sxs-lookup"><span data-stu-id="e8b31-117">port</span></span>|<span data-ttu-id="e8b31-118">Entier qui spécifie le numéro de port de communication par défaut.</span><span class="sxs-lookup"><span data-stu-id="e8b31-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="e8b31-119">scheme</span><span class="sxs-lookup"><span data-stu-id="e8b31-119">scheme</span></span>|<span data-ttu-id="e8b31-120">Chaîne qui spécifie le groupe de paramètres de protocole associé à un port de communication.</span><span class="sxs-lookup"><span data-stu-id="e8b31-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8b31-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e8b31-121">Child Elements</span></span>  
 <span data-ttu-id="e8b31-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e8b31-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8b31-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e8b31-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e8b31-124">Élément</span><span class="sxs-lookup"><span data-stu-id="e8b31-124">Element</span></span>|<span data-ttu-id="e8b31-125">Description</span><span class="sxs-lookup"><span data-stu-id="e8b31-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8b31-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="e8b31-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="e8b31-127">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="e8b31-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8b31-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8b31-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>
