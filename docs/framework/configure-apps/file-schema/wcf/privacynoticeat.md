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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 46a27dcc35c01d25391c9224d4967937b0a02d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="a6fd6-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="a6fd6-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="a6fd6-103">Représente un élément de configuration qui spécifie un avis de confidentialité utilisé dans la liaison `wsFederationHttp`.</span><span class="sxs-lookup"><span data-stu-id="a6fd6-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="a6fd6-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a6fd6-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a6fd6-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="a6fd6-105">\<bindings></span></span>  
<span data-ttu-id="a6fd6-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a6fd6-106">\<customBinding></span></span>  
<span data-ttu-id="a6fd6-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="a6fd6-107">\<binding></span></span>  
<span data-ttu-id="a6fd6-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="a6fd6-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6fd6-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6fd6-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"  
        version="Integer" />  
```  
  
## <a name="type"></a><span data-ttu-id="a6fd6-110">Type</span><span class="sxs-lookup"><span data-stu-id="a6fd6-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6fd6-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a6fd6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a6fd6-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a6fd6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6fd6-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="a6fd6-113">Attributes</span></span>  
  
|<span data-ttu-id="a6fd6-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="a6fd6-114">Attribute</span></span>|<span data-ttu-id="a6fd6-115">Description</span><span class="sxs-lookup"><span data-stu-id="a6fd6-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="a6fd6-116">Chaîne qui spécifie l'URI dans lequel l'information préalable de confidentialité est située.</span><span class="sxs-lookup"><span data-stu-id="a6fd6-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="a6fd6-117">Entier qui spécifie la version de cet avis de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="a6fd6-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6fd6-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a6fd6-118">Child Elements</span></span>  
 <span data-ttu-id="a6fd6-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a6fd6-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6fd6-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a6fd6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a6fd6-121">Élément</span><span class="sxs-lookup"><span data-stu-id="a6fd6-121">Element</span></span>|<span data-ttu-id="a6fd6-122">Description</span><span class="sxs-lookup"><span data-stu-id="a6fd6-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6fd6-123">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="a6fd6-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a6fd6-124">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a6fd6-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6fd6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6fd6-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="a6fd6-126">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a6fd6-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a6fd6-127">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="a6fd6-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a6fd6-128">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="a6fd6-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a6fd6-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a6fd6-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
