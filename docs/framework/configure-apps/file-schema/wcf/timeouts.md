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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41ebd88f64b001b577342562c9c3010b307aaccc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="e13a3-102">&lt;délais d’attente&gt;</span><span class="sxs-lookup"><span data-stu-id="e13a3-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="e13a3-103">Représente un élément de configuration qui spécifie l'intervalle de temps pendant lequel l'ouverture ou la fermeture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="e13a3-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="e13a3-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e13a3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e13a3-105">\<client ></span><span class="sxs-lookup"><span data-stu-id="e13a3-105">\<client></span></span>  
<span data-ttu-id="e13a3-106">\<point de terminaison ></span><span class="sxs-lookup"><span data-stu-id="e13a3-106">\<endpoint></span></span>  
<span data-ttu-id="e13a3-107">\<hôte ></span><span class="sxs-lookup"><span data-stu-id="e13a3-107">\<host></span></span>  
<span data-ttu-id="e13a3-108">\<délais d’attente ></span><span class="sxs-lookup"><span data-stu-id="e13a3-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e13a3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e13a3-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e13a3-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e13a3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e13a3-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e13a3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e13a3-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="e13a3-112">Attributes</span></span>  
  
|<span data-ttu-id="e13a3-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="e13a3-113">Attribute</span></span>|<span data-ttu-id="e13a3-114">Description</span><span class="sxs-lookup"><span data-stu-id="e13a3-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="e13a3-115">Valeur de type <xref:System.TimeSpan> qui spécifie l'intervalle de temps pendant lequel la fermeture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="e13a3-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="e13a3-116">Valeur de type <xref:System.TimeSpan> qui spécifie l'intervalle de temps pendant lequel l'ouverture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="e13a3-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e13a3-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e13a3-117">Child Elements</span></span>  
 <span data-ttu-id="e13a3-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e13a3-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e13a3-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e13a3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e13a3-120">Élément</span><span class="sxs-lookup"><span data-stu-id="e13a3-120">Element</span></span>|<span data-ttu-id="e13a3-121">Description</span><span class="sxs-lookup"><span data-stu-id="e13a3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e13a3-122">\<hôte ></span><span class="sxs-lookup"><span data-stu-id="e13a3-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="e13a3-123">Élément de configuration qui spécifie des paramètres pour un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="e13a3-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e13a3-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e13a3-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="e13a3-125">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="e13a3-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
