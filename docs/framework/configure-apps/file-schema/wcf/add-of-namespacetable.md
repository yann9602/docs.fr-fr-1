---
title: '&lt;add&gt; de &lt;namespaceTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f08f4b46c6e6290602fc78a2f06954b9cf0b07d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="7bdaf-102">&lt;add&gt; de &lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="7bdaf-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="7bdaf-103">Représente un élément de configuration qui contient un mappage espace de noms-préfixe à utiliser dans des filtres XPath pour le routage.</span><span class="sxs-lookup"><span data-stu-id="7bdaf-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="7bdaf-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="7bdaf-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7bdaf-105">\<routage ></span><span class="sxs-lookup"><span data-stu-id="7bdaf-105">\<routing></span></span>  
<span data-ttu-id="7bdaf-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="7bdaf-106">\<namespaceTable></span></span>  
<span data-ttu-id="7bdaf-107">\<add></span><span class="sxs-lookup"><span data-stu-id="7bdaf-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bdaf-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bdaf-108">Syntax</span></span>  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bdaf-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7bdaf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7bdaf-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7bdaf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bdaf-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="7bdaf-111">Attributes</span></span>  
  
|<span data-ttu-id="7bdaf-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="7bdaf-112">Attribute</span></span>|<span data-ttu-id="7bdaf-113">Description</span><span class="sxs-lookup"><span data-stu-id="7bdaf-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7bdaf-114">namespace</span><span class="sxs-lookup"><span data-stu-id="7bdaf-114">namespace</span></span>|<span data-ttu-id="7bdaf-115">Chaîne qui contient l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7bdaf-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="7bdaf-116">prefix</span><span class="sxs-lookup"><span data-stu-id="7bdaf-116">prefix</span></span>|<span data-ttu-id="7bdaf-117">Chaîne qui contient le préfixe de cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7bdaf-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bdaf-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7bdaf-118">Child Elements</span></span>  
 <span data-ttu-id="7bdaf-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7bdaf-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bdaf-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7bdaf-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7bdaf-121">Élément</span><span class="sxs-lookup"><span data-stu-id="7bdaf-121">Element</span></span>|<span data-ttu-id="7bdaf-122">Description</span><span class="sxs-lookup"><span data-stu-id="7bdaf-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bdaf-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="7bdaf-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="7bdaf-124">Représente une section de configuration qui permet de définir un ensemble d’éléments contenant des mappages espace de noms-préfixe qui peuvent ensuite être utilisés dans des filtres XPath pour le routage.</span><span class="sxs-lookup"><span data-stu-id="7bdaf-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7bdaf-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bdaf-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
