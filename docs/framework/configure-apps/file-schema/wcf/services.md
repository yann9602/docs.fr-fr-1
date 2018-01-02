---
title: '&lt;services&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46a2e0d810068db6409bc7b0fd1443a41c3d3ec3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicesgt"></a><span data-ttu-id="354fc-102">&lt;services&gt;</span><span class="sxs-lookup"><span data-stu-id="354fc-102">&lt;services&gt;</span></span>
<span data-ttu-id="354fc-103">Les services sont définis dans la section `services` du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="354fc-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="354fc-104">Chacun dispose de sa propre section de configuration de `service`.</span><span class="sxs-lookup"><span data-stu-id="354fc-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="354fc-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="354fc-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="354fc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="354fc-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="354fc-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="354fc-107">Attributes and Elements</span></span>  
 <span data-ttu-id="354fc-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="354fc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="354fc-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="354fc-109">Attributes</span></span>  
 <span data-ttu-id="354fc-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="354fc-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="354fc-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="354fc-111">Child Elements</span></span>  
  
|<span data-ttu-id="354fc-112">Élément</span><span class="sxs-lookup"><span data-stu-id="354fc-112">Element</span></span>|<span data-ttu-id="354fc-113">Description</span><span class="sxs-lookup"><span data-stu-id="354fc-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="354fc-114">\<service ></span><span class="sxs-lookup"><span data-stu-id="354fc-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="354fc-115">Définissez le contrat de service, le comportement et les points de terminaison du service particulier.</span><span class="sxs-lookup"><span data-stu-id="354fc-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="354fc-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="354fc-116">Parent Elements</span></span>  
  
|<span data-ttu-id="354fc-117">Élément</span><span class="sxs-lookup"><span data-stu-id="354fc-117">Element</span></span>|<span data-ttu-id="354fc-118">Description</span><span class="sxs-lookup"><span data-stu-id="354fc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="354fc-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="354fc-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="354fc-120">Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="354fc-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="354fc-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="354fc-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
