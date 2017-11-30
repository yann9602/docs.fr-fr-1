---
title: '&lt;policyImporter&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 99bb7c6be02bad85792dfce9de1f6ef8ba1dcd17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="cf1c1-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="cf1c1-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="cf1c1-103">Indique un importateur de stratégie qui contrôle l’importation d’assertions de stratégie personnalisées concernant les liaisons.</span><span class="sxs-lookup"><span data-stu-id="cf1c1-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="cf1c1-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="cf1c1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cf1c1-105">\<client ></span><span class="sxs-lookup"><span data-stu-id="cf1c1-105">\<client></span></span>  
<span data-ttu-id="cf1c1-106">\<métadonnées ></span><span class="sxs-lookup"><span data-stu-id="cf1c1-106">\<metadata></span></span>  
<span data-ttu-id="cf1c1-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="cf1c1-107">\<policyImporters></span></span>  
<span data-ttu-id="cf1c1-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="cf1c1-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf1c1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf1c1-109">Syntax</span></span>  
  
```xml  
<metadata>  
   <policyImporters>  
      <policyImporter type="string" />  
   </policyImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf1c1-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cf1c1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cf1c1-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cf1c1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf1c1-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="cf1c1-112">Attributes</span></span>  
  
|<span data-ttu-id="cf1c1-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="cf1c1-113">Attribute</span></span>|<span data-ttu-id="cf1c1-114">Description</span><span class="sxs-lookup"><span data-stu-id="cf1c1-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="cf1c1-115">Type de cet élément.</span><span class="sxs-lookup"><span data-stu-id="cf1c1-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf1c1-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cf1c1-116">Child Elements</span></span>  
 <span data-ttu-id="cf1c1-117">None</span><span class="sxs-lookup"><span data-stu-id="cf1c1-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf1c1-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cf1c1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cf1c1-119">Élément</span><span class="sxs-lookup"><span data-stu-id="cf1c1-119">Element</span></span>|<span data-ttu-id="cf1c1-120">Description</span><span class="sxs-lookup"><span data-stu-id="cf1c1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf1c1-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="cf1c1-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="cf1c1-122">Indique tous les importateurs de stratégie contrôlant l’importation d’assertions de stratégie personnalisées concernant les liaisons.</span><span class="sxs-lookup"><span data-stu-id="cf1c1-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf1c1-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="cf1c1-123">Remarks</span></span>  
 <span data-ttu-id="cf1c1-124">Un importateur de stratégie permet de rechercher des assertions de stratégie personnalisées concernant les fonctionnalités de liaison et de joindre un élément de liaison personnalisé qui implémente les fonctionnalités requises par l’assertion.</span><span class="sxs-lookup"><span data-stu-id="cf1c1-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf1c1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf1c1-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="cf1c1-126">Configuration du Client WCF</span><span class="sxs-lookup"><span data-stu-id="cf1c1-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="cf1c1-127">Clients</span><span class="sxs-lookup"><span data-stu-id="cf1c1-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
