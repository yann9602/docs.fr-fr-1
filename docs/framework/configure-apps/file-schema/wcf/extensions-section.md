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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a564b85609ca289f382789844d4e78252bb66482
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltextensionsgt-section"></a><span data-ttu-id="eb0b5-102">&lt;extensions&gt;, section</span><span class="sxs-lookup"><span data-stu-id="eb0b5-102">&lt;extensions&gt; section</span></span>
<span data-ttu-id="eb0b5-103">Cette section de configuration contient une collection d'extensions, qui permettent à l'utilisateur de créer des liaisons, des comportements et d'autres aspects d'extensions définis par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="eb0b5-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="eb0b5-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="eb0b5-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb0b5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb0b5-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb0b5-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="eb0b5-106">Attributes and Elements</span></span>  
 <span data-ttu-id="eb0b5-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="eb0b5-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb0b5-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="eb0b5-108">Attributes</span></span>  
 <span data-ttu-id="eb0b5-109">Aucun</span><span class="sxs-lookup"><span data-stu-id="eb0b5-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eb0b5-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="eb0b5-110">Child Elements</span></span>  
  
|<span data-ttu-id="eb0b5-111">Élément</span><span class="sxs-lookup"><span data-stu-id="eb0b5-111">Element</span></span>|<span data-ttu-id="eb0b5-112">Description</span><span class="sxs-lookup"><span data-stu-id="eb0b5-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb0b5-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="eb0b5-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="eb0b5-114">Cette section contient des éléments enfants qui spécifient des extensions de comportement permettant à l’utilisateur de personnaliser les comportements de service ou de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="eb0b5-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="eb0b5-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="eb0b5-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="eb0b5-116">Cette section active l’utilisation d’un élément de liaison personnalisé à partir d’un ordinateur ou d’un fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="eb0b5-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="eb0b5-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="eb0b5-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="eb0b5-118">Cette section contient des éléments enfants qui spécifient des extensions de liaison permettant à l’utilisateur de personnaliser des liaisons.</span><span class="sxs-lookup"><span data-stu-id="eb0b5-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="eb0b5-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="eb0b5-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="eb0b5-120">Cette section contient des éléments enfants qui inscrivent des points de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="eb0b5-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb0b5-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="eb0b5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="eb0b5-122">Élément</span><span class="sxs-lookup"><span data-stu-id="eb0b5-122">Element</span></span>|<span data-ttu-id="eb0b5-123">Description</span><span class="sxs-lookup"><span data-stu-id="eb0b5-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb0b5-124">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="eb0b5-124">system.ServiceModel</span></span>|<span data-ttu-id="eb0b5-125">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="eb0b5-125">The root element of all WCF configuration elements.</span></span>|
