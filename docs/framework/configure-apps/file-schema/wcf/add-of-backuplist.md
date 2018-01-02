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
ms.workload: dotnet
ms.openlocfilehash: 786620b0daf1cd22a95f9d0c94b7fc3d17c1a2c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="78495-102">&lt;add&gt; de &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="78495-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="78495-103">Représente un élément de configuration qui définit un élément de point de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="78495-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="78495-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="78495-104">\<system.serviceModel></span></span>  
<span data-ttu-id="78495-105">\<routage ></span><span class="sxs-lookup"><span data-stu-id="78495-105">\<routing></span></span>  
<span data-ttu-id="78495-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="78495-106">\<backupLists></span></span>  
<span data-ttu-id="78495-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="78495-107">\<backupList></span></span>  
<span data-ttu-id="78495-108">\<add></span><span class="sxs-lookup"><span data-stu-id="78495-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78495-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78495-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78495-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="78495-110">Attributes and Elements</span></span>  
 <span data-ttu-id="78495-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="78495-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78495-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="78495-112">Attributes</span></span>  
  
|<span data-ttu-id="78495-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="78495-113">Attribute</span></span>|<span data-ttu-id="78495-114">Description</span><span class="sxs-lookup"><span data-stu-id="78495-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="78495-115">name</span><span class="sxs-lookup"><span data-stu-id="78495-115">name</span></span>|<span data-ttu-id="78495-116">Chaîne qui spécifie le nom du point de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="78495-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78495-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="78495-117">Child Elements</span></span>  
 <span data-ttu-id="78495-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="78495-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78495-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="78495-119">Parent Elements</span></span>  
  
|<span data-ttu-id="78495-120">Élément</span><span class="sxs-lookup"><span data-stu-id="78495-120">Element</span></span>|<span data-ttu-id="78495-121">Description</span><span class="sxs-lookup"><span data-stu-id="78495-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78495-122">\<routage ></span><span class="sxs-lookup"><span data-stu-id="78495-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="78495-123">Contient une liste de points de terminaison que vous souhaitez que le Service de routage à utiliser au cas où le point de terminaison principal ne peut pas être atteint.</span><span class="sxs-lookup"><span data-stu-id="78495-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78495-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78495-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
