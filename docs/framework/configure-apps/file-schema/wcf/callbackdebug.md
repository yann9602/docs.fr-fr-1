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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 93b89787795cb58644b79ae4795e7a036741e138
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcallbackdebuggt"></a><span data-ttu-id="e0611-102">&lt;callbackDebug&gt;</span><span class="sxs-lookup"><span data-stu-id="e0611-102">&lt;callbackDebug&gt;</span></span>
<span data-ttu-id="e0611-103">Spécifie le débogage de service pour un objet de rappel [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e0611-103">Specifies service debugging for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] callback object.</span></span>  
  
 <span data-ttu-id="e0611-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e0611-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e0611-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="e0611-105">\<behaviors></span></span>  
<span data-ttu-id="e0611-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e0611-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="e0611-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="e0611-107">\<behavior></span></span>  
<span data-ttu-id="e0611-108">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="e0611-108">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0611-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0611-109">Syntax</span></span>  
  
```xml  
<callbackDebug  includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="type"></a><span data-ttu-id="e0611-110">Type</span><span class="sxs-lookup"><span data-stu-id="e0611-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0611-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e0611-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e0611-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e0611-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0611-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="e0611-113">Attributes</span></span>  
  
|<span data-ttu-id="e0611-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="e0611-114">Attribute</span></span>|<span data-ttu-id="e0611-115">Description</span><span class="sxs-lookup"><span data-stu-id="e0611-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="e0611-116">Valeur qui spécifie si les objets de rappel client retournent au service des informations sur les exceptions managées dans les erreurs SOAP.</span><span class="sxs-lookup"><span data-stu-id="e0611-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="e0611-117">Si vous définissez cet attribut par programme à `true`, vous pouvez activer le retour du flux d'informations sur les exceptions managées dans un objet de rappel client, à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="e0611-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="e0611-118">**Attention :** retournant des informations d’exception gérées aux clients peuvent constituer un risque de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e0611-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="e0611-119">En effet, les détails de l'exception exposent des informations relatives à l'implémentation d'un service interne qui peuvent être utilisées par des clients non autorisés.</span><span class="sxs-lookup"><span data-stu-id="e0611-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0611-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e0611-120">Child Elements</span></span>  
 <span data-ttu-id="e0611-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e0611-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0611-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e0611-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e0611-123">Élément</span><span class="sxs-lookup"><span data-stu-id="e0611-123">Element</span></span>|<span data-ttu-id="e0611-124">Description</span><span class="sxs-lookup"><span data-stu-id="e0611-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0611-125">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="e0611-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e0611-126">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="e0611-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0611-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0611-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>
