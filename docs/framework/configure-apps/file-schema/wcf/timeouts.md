---
title: "&lt;délais d’attente&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da80ab797078e1fe912ccbfff07d7fb2da49664e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="2e5e6-102">&lt;délais d’attente&gt;</span><span class="sxs-lookup"><span data-stu-id="2e5e6-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="2e5e6-103">Représente un élément de configuration qui spécifie l'intervalle de temps pendant lequel l'ouverture ou la fermeture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="2e5e6-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="2e5e6-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2e5e6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2e5e6-105">\<client ></span><span class="sxs-lookup"><span data-stu-id="2e5e6-105">\<client></span></span>  
<span data-ttu-id="2e5e6-106">\<point de terminaison ></span><span class="sxs-lookup"><span data-stu-id="2e5e6-106">\<endpoint></span></span>  
<span data-ttu-id="2e5e6-107">\<hôte ></span><span class="sxs-lookup"><span data-stu-id="2e5e6-107">\<host></span></span>  
<span data-ttu-id="2e5e6-108">\<délais d’attente ></span><span class="sxs-lookup"><span data-stu-id="2e5e6-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e5e6-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e5e6-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e5e6-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2e5e6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2e5e6-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2e5e6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e5e6-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="2e5e6-112">Attributes</span></span>  
  
|<span data-ttu-id="2e5e6-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="2e5e6-113">Attribute</span></span>|<span data-ttu-id="2e5e6-114">Description</span><span class="sxs-lookup"><span data-stu-id="2e5e6-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="2e5e6-115">Valeur de type <xref:System.TimeSpan> qui spécifie l'intervalle de temps pendant lequel la fermeture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="2e5e6-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="2e5e6-116">Valeur de type <xref:System.TimeSpan> qui spécifie l'intervalle de temps pendant lequel l'ouverture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="2e5e6-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2e5e6-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2e5e6-117">Child Elements</span></span>  
 <span data-ttu-id="2e5e6-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2e5e6-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2e5e6-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2e5e6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2e5e6-120">Élément</span><span class="sxs-lookup"><span data-stu-id="2e5e6-120">Element</span></span>|<span data-ttu-id="2e5e6-121">Description</span><span class="sxs-lookup"><span data-stu-id="2e5e6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e5e6-122">\<hôte ></span><span class="sxs-lookup"><span data-stu-id="2e5e6-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="2e5e6-123">Élément de configuration qui spécifie des paramètres pour un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="2e5e6-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e5e6-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e5e6-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="2e5e6-125">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="2e5e6-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
