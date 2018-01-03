---
title: '&lt;privacyNoticeAt&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30b3f0bdd1aa02473470c354a730bcfa450f0264
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="a74d5-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="a74d5-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="a74d5-103">Représente un élément de configuration qui spécifie un avis de confidentialité utilisé dans la liaison `wsFederationHttp`.</span><span class="sxs-lookup"><span data-stu-id="a74d5-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="a74d5-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a74d5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a74d5-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="a74d5-105">\<bindings></span></span>  
<span data-ttu-id="a74d5-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a74d5-106">\<customBinding></span></span>  
<span data-ttu-id="a74d5-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="a74d5-107">\<binding></span></span>  
<span data-ttu-id="a74d5-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="a74d5-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a74d5-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a74d5-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"  
        version="Integer" />  
```  
  
## <a name="type"></a><span data-ttu-id="a74d5-110">Type</span><span class="sxs-lookup"><span data-stu-id="a74d5-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a74d5-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a74d5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a74d5-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a74d5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a74d5-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="a74d5-113">Attributes</span></span>  
  
|<span data-ttu-id="a74d5-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="a74d5-114">Attribute</span></span>|<span data-ttu-id="a74d5-115">Description</span><span class="sxs-lookup"><span data-stu-id="a74d5-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="a74d5-116">Chaîne qui spécifie l'URI dans lequel l'information préalable de confidentialité est située.</span><span class="sxs-lookup"><span data-stu-id="a74d5-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="a74d5-117">Entier qui spécifie la version de cet avis de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="a74d5-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a74d5-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a74d5-118">Child Elements</span></span>  
 <span data-ttu-id="a74d5-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a74d5-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a74d5-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a74d5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a74d5-121">Élément</span><span class="sxs-lookup"><span data-stu-id="a74d5-121">Element</span></span>|<span data-ttu-id="a74d5-122">Description</span><span class="sxs-lookup"><span data-stu-id="a74d5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a74d5-123">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="a74d5-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a74d5-124">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a74d5-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a74d5-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a74d5-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="a74d5-126">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a74d5-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a74d5-127">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="a74d5-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a74d5-128">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="a74d5-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a74d5-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a74d5-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
