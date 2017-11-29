---
title: "&lt;ordinateur hôte&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bded8d718259bf4fc84bfe790db069a77fc2a703
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lthostgt"></a><span data-ttu-id="a648a-102">&lt;ordinateur hôte&gt;</span><span class="sxs-lookup"><span data-stu-id="a648a-102">&lt;host&gt;</span></span>
<span data-ttu-id="a648a-103">Spécifie les paramètres d'un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="a648a-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="a648a-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a648a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a648a-105">\<Services ></span><span class="sxs-lookup"><span data-stu-id="a648a-105">\<services></span></span>  
<span data-ttu-id="a648a-106">\<service ></span><span class="sxs-lookup"><span data-stu-id="a648a-106">\<service></span></span>  
<span data-ttu-id="a648a-107">\<hôte ></span><span class="sxs-lookup"><span data-stu-id="a648a-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a648a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a648a-108">Syntax</span></span>  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a><span data-ttu-id="a648a-109">Type</span><span class="sxs-lookup"><span data-stu-id="a648a-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a648a-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a648a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a648a-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a648a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a648a-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="a648a-112">Attributes</span></span>  
 <span data-ttu-id="a648a-113">Aucun</span><span class="sxs-lookup"><span data-stu-id="a648a-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a648a-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a648a-114">Child Elements</span></span>  
  
|<span data-ttu-id="a648a-115">Élément</span><span class="sxs-lookup"><span data-stu-id="a648a-115">Element</span></span>|<span data-ttu-id="a648a-116">Description</span><span class="sxs-lookup"><span data-stu-id="a648a-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a648a-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="a648a-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="a648a-118">Collection d'éléments `baseAddress` qui spécifie les adresses de base utilisées par l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="a648a-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="a648a-119">\<délais d’attente ></span><span class="sxs-lookup"><span data-stu-id="a648a-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="a648a-120">Élément de configuration qui spécifie la durée d'ouverture ou de fermeture autorisée de l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="a648a-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a648a-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a648a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a648a-122">Élément</span><span class="sxs-lookup"><span data-stu-id="a648a-122">Element</span></span>|<span data-ttu-id="a648a-123">Description</span><span class="sxs-lookup"><span data-stu-id="a648a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a648a-124">\<service ></span><span class="sxs-lookup"><span data-stu-id="a648a-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="a648a-125">Spécifie les paramètres d'un service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a648a-125">Specifies the settings for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a648a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a648a-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="a648a-127">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="a648a-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
