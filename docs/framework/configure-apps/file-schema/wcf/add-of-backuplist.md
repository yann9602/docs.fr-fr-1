---
title: '&lt;add&gt; de &lt;backupList&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b93b442d21d34eea5031cea565bdcf62139abc81
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="dc011-102">&lt;add&gt; de &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="dc011-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="dc011-103">Représente un élément de configuration qui définit un élément de point de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="dc011-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="dc011-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="dc011-104">\<system.serviceModel></span></span>  
<span data-ttu-id="dc011-105">\<routage ></span><span class="sxs-lookup"><span data-stu-id="dc011-105">\<routing></span></span>  
<span data-ttu-id="dc011-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="dc011-106">\<backupLists></span></span>  
<span data-ttu-id="dc011-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="dc011-107">\<backupList></span></span>  
<span data-ttu-id="dc011-108">\<add></span><span class="sxs-lookup"><span data-stu-id="dc011-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc011-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc011-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc011-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dc011-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dc011-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="dc011-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc011-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="dc011-112">Attributes</span></span>  
  
|<span data-ttu-id="dc011-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="dc011-113">Attribute</span></span>|<span data-ttu-id="dc011-114">Description</span><span class="sxs-lookup"><span data-stu-id="dc011-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc011-115">name</span><span class="sxs-lookup"><span data-stu-id="dc011-115">name</span></span>|<span data-ttu-id="dc011-116">Chaîne qui spécifie le nom du point de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="dc011-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc011-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dc011-117">Child Elements</span></span>  
 <span data-ttu-id="dc011-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dc011-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc011-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dc011-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dc011-120">Élément</span><span class="sxs-lookup"><span data-stu-id="dc011-120">Element</span></span>|<span data-ttu-id="dc011-121">Description</span><span class="sxs-lookup"><span data-stu-id="dc011-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc011-122">\<routage ></span><span class="sxs-lookup"><span data-stu-id="dc011-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="dc011-123">Contient une liste de points de terminaison que vous souhaitez que le Service de routage à utiliser au cas où le point de terminaison principal ne peut pas être atteint.</span><span class="sxs-lookup"><span data-stu-id="dc011-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc011-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc011-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
