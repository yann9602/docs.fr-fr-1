---
title: '&lt;enableWebScript&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6dc2654b8c51dad53c05a37f5febe15d6d69fd1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltenablewebscriptgt"></a><span data-ttu-id="50678-102">&lt;enableWebScript&gt;</span><span class="sxs-lookup"><span data-stu-id="50678-102">&lt;enableWebScript&gt;</span></span>
<span data-ttu-id="50678-103">Cet élément active le comportement de point de terminaison qui permet de consommer le service à partir de pages web ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="50678-103">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="50678-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="50678-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="50678-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="50678-105">\<behaviors></span></span>  
<span data-ttu-id="50678-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="50678-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="50678-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="50678-107">\<behavior></span></span>  
<span data-ttu-id="50678-108">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="50678-108">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50678-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50678-109">Syntax</span></span>  
  
```xml  
<enableWebScript />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50678-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="50678-110">Attributes and Elements</span></span>  
 <span data-ttu-id="50678-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="50678-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50678-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="50678-112">Attributes</span></span>  
 <span data-ttu-id="50678-113">Aucun</span><span class="sxs-lookup"><span data-stu-id="50678-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="50678-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="50678-114">Child Elements</span></span>  
 <span data-ttu-id="50678-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="50678-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50678-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="50678-116">Parent Elements</span></span>  
  
|<span data-ttu-id="50678-117">Élément</span><span class="sxs-lookup"><span data-stu-id="50678-117">Element</span></span>|<span data-ttu-id="50678-118">Description</span><span class="sxs-lookup"><span data-stu-id="50678-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50678-119">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="50678-119">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="50678-120">Spécifie le jeu de comportements du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="50678-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50678-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="50678-121">Remarks</span></span>  
 <span data-ttu-id="50678-122">Ce comportement doit uniquement être utilisé conjointement avec l’option le [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) liaison standard, ou le [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="50678-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="50678-123">Pour plus d'informations sur ce comportement, consultez <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="50678-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50678-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50678-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>  
 [<span data-ttu-id="50678-125">Intégration d’AJAX et prise en charge JSON</span><span class="sxs-lookup"><span data-stu-id="50678-125">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="50678-126">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="50678-126">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
