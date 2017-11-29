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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bd487238ebe327a5f89b737fdf764d94f955a411
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="17327-102">&lt;add&gt; de &lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="17327-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="17327-103">Point de terminaison de communication par défaut écouté par l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="17327-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="17327-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="17327-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="17327-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="17327-105">\<behaviors></span></span>  
<span data-ttu-id="17327-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="17327-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="17327-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="17327-107">\<behavior></span></span>  
<span data-ttu-id="17327-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="17327-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="17327-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="17327-109">\<defaultPorts></span></span>  
<span data-ttu-id="17327-110">\<add></span><span class="sxs-lookup"><span data-stu-id="17327-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17327-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17327-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>   <defaultPorts>      <add port="Integer" scheme="String" />   </defaultPorts></useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17327-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="17327-112">Attributes and Elements</span></span>  
 <span data-ttu-id="17327-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="17327-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17327-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="17327-114">Attributes</span></span>  
  
|<span data-ttu-id="17327-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="17327-115">Attribute</span></span>|<span data-ttu-id="17327-116">Description</span><span class="sxs-lookup"><span data-stu-id="17327-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17327-117">port</span><span class="sxs-lookup"><span data-stu-id="17327-117">port</span></span>|<span data-ttu-id="17327-118">Entier qui spécifie le numéro de port de communication par défaut.</span><span class="sxs-lookup"><span data-stu-id="17327-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="17327-119">scheme</span><span class="sxs-lookup"><span data-stu-id="17327-119">scheme</span></span>|<span data-ttu-id="17327-120">Chaîne qui spécifie le groupe de paramètres de protocole associé à un port de communication.</span><span class="sxs-lookup"><span data-stu-id="17327-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17327-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="17327-121">Child Elements</span></span>  
 <span data-ttu-id="17327-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="17327-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="17327-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="17327-123">Parent Elements</span></span>  
  
|<span data-ttu-id="17327-124">Élément</span><span class="sxs-lookup"><span data-stu-id="17327-124">Element</span></span>|<span data-ttu-id="17327-125">Description</span><span class="sxs-lookup"><span data-stu-id="17327-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17327-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="17327-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="17327-127">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="17327-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17327-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17327-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>
