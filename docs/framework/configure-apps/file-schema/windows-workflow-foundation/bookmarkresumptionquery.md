---
title: '&lt;bookmarkResumptionQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bafb044d052692385e0be0f4dbb1271eca847b1a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbookmarkresumptionquerygt"></a><span data-ttu-id="2ca3d-102">&lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="2ca3d-102">&lt;bookmarkResumptionQuery&gt;</span></span>
<span data-ttu-id="2ca3d-103">Représente une requête qui permet d'effectuer le suivi de la reprise d'un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="2ca3d-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="2ca3d-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="2ca3d-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="2ca3d-105">Pour plus d’informations sur les requêtes de modèle de suivi, consultez [modèles de suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2ca3d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="2ca3d-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2ca3d-106">\<system.serviceModel></span></span>  
<span data-ttu-id="2ca3d-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="2ca3d-107">\<tracking></span></span>  
<span data-ttu-id="2ca3d-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="2ca3d-108">\<trackingProfile></span></span>  
<span data-ttu-id="2ca3d-109">\<flux de travail ></span><span class="sxs-lookup"><span data-stu-id="2ca3d-109">\<workflow></span></span>  
<span data-ttu-id="2ca3d-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="2ca3d-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="2ca3d-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="2ca3d-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ca3d-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ca3d-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ca3d-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2ca3d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2ca3d-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2ca3d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ca3d-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="2ca3d-115">Attributes</span></span>  
  
|<span data-ttu-id="2ca3d-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="2ca3d-116">Attribute</span></span>|<span data-ttu-id="2ca3d-117">Description</span><span class="sxs-lookup"><span data-stu-id="2ca3d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ca3d-118">name</span><span class="sxs-lookup"><span data-stu-id="2ca3d-118">name</span></span>|<span data-ttu-id="2ca3d-119">Chaîne qui spécifie le nom de l'enregistrement de signet auquel s'abonner.</span><span class="sxs-lookup"><span data-stu-id="2ca3d-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ca3d-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2ca3d-120">Child Elements</span></span>  
 <span data-ttu-id="2ca3d-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2ca3d-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ca3d-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2ca3d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2ca3d-123">Élément</span><span class="sxs-lookup"><span data-stu-id="2ca3d-123">Element</span></span>|<span data-ttu-id="2ca3d-124">Description</span><span class="sxs-lookup"><span data-stu-id="2ca3d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ca3d-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="2ca3d-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="2ca3d-126">Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="2ca3d-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ca3d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ca3d-127">See Also</span></span>  
 <span data-ttu-id="2ca3d-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2ca3d-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="2ca3d-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2ca3d-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="2ca3d-130">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="2ca3d-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="2ca3d-131">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="2ca3d-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
