---
title: '&lt;serviceAuthenticationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2385b96460e0a3d53efb62054fb7da334ddd2d49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="c1ff0-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="c1ff0-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="c1ff0-103">Fournit un élément de configuration de flux de travail qui établit au niveau du service la validité d'une transmission, d'un message ou d'un expéditeur.</span><span class="sxs-lookup"><span data-stu-id="c1ff0-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="c1ff0-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c1ff0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c1ff0-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="c1ff0-105">\<behaviors></span></span>  
<span data-ttu-id="c1ff0-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c1ff0-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c1ff0-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="c1ff0-107">\<behavior></span></span>  
<span data-ttu-id="c1ff0-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="c1ff0-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1ff0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1ff0-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1ff0-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c1ff0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c1ff0-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c1ff0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1ff0-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="c1ff0-112">Attributes</span></span>  
  
|<span data-ttu-id="c1ff0-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="c1ff0-113">Attribute</span></span>|<span data-ttu-id="c1ff0-114">Description</span><span class="sxs-lookup"><span data-stu-id="c1ff0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c1ff0-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="c1ff0-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="c1ff0-116">Chaîne qui spécifie le type de la stratégie d'authentification pour le comportement actuel.</span><span class="sxs-lookup"><span data-stu-id="c1ff0-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1ff0-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c1ff0-117">Child Elements</span></span>  
 <span data-ttu-id="c1ff0-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c1ff0-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c1ff0-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c1ff0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c1ff0-120">Élément</span><span class="sxs-lookup"><span data-stu-id="c1ff0-120">Element</span></span>|<span data-ttu-id="c1ff0-121">Description</span><span class="sxs-lookup"><span data-stu-id="c1ff0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1ff0-122">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="c1ff0-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="c1ff0-123">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="c1ff0-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1ff0-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1ff0-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
