---
title: '&lt;webScriptEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 855a0fc0727bf0559b922317d439f7550f18d9ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="9f10d-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="9f10d-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="9f10d-103">Cet élément de configuration définit un point de terminaison standard avec une liste fixe [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) automatiquement une liaison qui ajoute le [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportement.</span><span class="sxs-lookup"><span data-stu-id="9f10d-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="9f10d-104">Utilisez ce point de terminaison lorsque vous écrivez un service appelé à partir d'une application ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="9f10d-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="9f10d-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9f10d-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="9f10d-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="9f10d-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f10d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f10d-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String"/>
    </webScriptEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f10d-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9f10d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9f10d-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9f10d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f10d-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="9f10d-110">Attributes</span></span>  
  
|<span data-ttu-id="9f10d-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="9f10d-111">Attribute</span></span>|<span data-ttu-id="9f10d-112">Description</span><span class="sxs-lookup"><span data-stu-id="9f10d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f10d-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="9f10d-113">webEndpointType</span></span>|<span data-ttu-id="9f10d-114">Chaîne qui spécifie le type du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="9f10d-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f10d-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9f10d-115">Child Elements</span></span>  
 <span data-ttu-id="9f10d-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9f10d-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f10d-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9f10d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9f10d-118">Élément</span><span class="sxs-lookup"><span data-stu-id="9f10d-118">Element</span></span>|<span data-ttu-id="9f10d-119">Description</span><span class="sxs-lookup"><span data-stu-id="9f10d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f10d-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="9f10d-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="9f10d-121">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="9f10d-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f10d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f10d-122">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
