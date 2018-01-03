---
title: '&lt;extensions&gt;, section'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04905ae0f40a1f9ca88b4a04d4e49b0ce895ca56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltextensionsgt-section"></a><span data-ttu-id="fb6cc-102">&lt;extensions&gt;, section</span><span class="sxs-lookup"><span data-stu-id="fb6cc-102">&lt;extensions&gt; section</span></span>
<span data-ttu-id="fb6cc-103">Cette section de configuration contient une collection d’extensions, qui permettent à l’utilisateur de créer des liaisons, des comportements et d’autres aspects d’extensions définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fb6cc-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="fb6cc-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fb6cc-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb6cc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb6cc-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <extensions>  
    <bindingExtensions>  
    </bindingExtensions>  
    <behaviorExtensions>  
    </behaviorExtensions>  
    <bindingElementExtensions>  
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb6cc-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fb6cc-106">Attributes and Elements</span></span>  
 <span data-ttu-id="fb6cc-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fb6cc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb6cc-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="fb6cc-108">Attributes</span></span>  
 <span data-ttu-id="fb6cc-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fb6cc-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fb6cc-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fb6cc-110">Child Elements</span></span>  
  
|<span data-ttu-id="fb6cc-111">Élément</span><span class="sxs-lookup"><span data-stu-id="fb6cc-111">Element</span></span>|<span data-ttu-id="fb6cc-112">Description</span><span class="sxs-lookup"><span data-stu-id="fb6cc-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb6cc-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="fb6cc-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="fb6cc-114">Cette section contient des éléments enfants qui spécifient des extensions de comportement permettant à l’utilisateur de personnaliser les comportements de service ou de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="fb6cc-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="fb6cc-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="fb6cc-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="fb6cc-116">Cette section active l’utilisation d’un élément de liaison personnalisé à partir d’un ordinateur ou d’un fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="fb6cc-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="fb6cc-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="fb6cc-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="fb6cc-118">Cette section contient des éléments enfants qui spécifient des extensions de liaison permettant à l’utilisateur de personnaliser des liaisons.</span><span class="sxs-lookup"><span data-stu-id="fb6cc-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="fb6cc-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="fb6cc-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="fb6cc-120">Cette section contient des éléments enfants qui inscrivent des points de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="fb6cc-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb6cc-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fb6cc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="fb6cc-122">Élément</span><span class="sxs-lookup"><span data-stu-id="fb6cc-122">Element</span></span>|<span data-ttu-id="fb6cc-123">Description</span><span class="sxs-lookup"><span data-stu-id="fb6cc-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb6cc-124">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fb6cc-124">system.ServiceModel</span></span>|<span data-ttu-id="fb6cc-125">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="fb6cc-125">The root element of all WCF configuration elements.</span></span>|
