---
title: '&lt;callbackDebug&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccb48efcdd1924ade27220a685e146a7f5eeef76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcallbackdebuggt"></a><span data-ttu-id="95193-102">&lt;callbackDebug&gt;</span><span class="sxs-lookup"><span data-stu-id="95193-102">&lt;callbackDebug&gt;</span></span>
<span data-ttu-id="95193-103">Spécifie le débogage de service pour un objet de rappel [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="95193-103">Specifies service debugging for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] callback object.</span></span>  
  
 <span data-ttu-id="95193-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="95193-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="95193-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="95193-105">\<behaviors></span></span>  
<span data-ttu-id="95193-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="95193-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="95193-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="95193-107">\<behavior></span></span>  
<span data-ttu-id="95193-108">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="95193-108">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95193-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95193-109">Syntax</span></span>  
  
```xml  
<callbackDebug  includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="type"></a><span data-ttu-id="95193-110">Type</span><span class="sxs-lookup"><span data-stu-id="95193-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95193-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="95193-111">Attributes and Elements</span></span>  
 <span data-ttu-id="95193-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="95193-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95193-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="95193-113">Attributes</span></span>  
  
|<span data-ttu-id="95193-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="95193-114">Attribute</span></span>|<span data-ttu-id="95193-115">Description</span><span class="sxs-lookup"><span data-stu-id="95193-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="95193-116">Valeur qui spécifie si les objets de rappel client retournent au service des informations sur les exceptions managées dans les erreurs SOAP.</span><span class="sxs-lookup"><span data-stu-id="95193-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="95193-117">Si vous définissez cet attribut par programme à `true`, vous pouvez activer le retour du flux d'informations sur les exceptions managées dans un objet de rappel client, à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="95193-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="95193-118">**Attention :** retournant des informations d’exception gérées aux clients peuvent constituer un risque de sécurité.</span><span class="sxs-lookup"><span data-stu-id="95193-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="95193-119">En effet, les détails de l'exception exposent des informations relatives à l'implémentation d'un service interne qui peuvent être utilisées par des clients non autorisés.</span><span class="sxs-lookup"><span data-stu-id="95193-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95193-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="95193-120">Child Elements</span></span>  
 <span data-ttu-id="95193-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="95193-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95193-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="95193-122">Parent Elements</span></span>  
  
|<span data-ttu-id="95193-123">Élément</span><span class="sxs-lookup"><span data-stu-id="95193-123">Element</span></span>|<span data-ttu-id="95193-124">Description</span><span class="sxs-lookup"><span data-stu-id="95193-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95193-125">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="95193-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="95193-126">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="95193-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95193-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95193-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>
