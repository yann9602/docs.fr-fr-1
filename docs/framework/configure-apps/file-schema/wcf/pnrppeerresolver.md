---
title: '&lt;pnrpPeerResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 223a66dd21305a4cbb6bb434f553e821037e7cb0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="e5194-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="e5194-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="e5194-103">Spécifie que le programme de résolution PNRP (Peer Name Resolution Protocol) doit être utilisé comme un programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="e5194-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="e5194-104">Cet élément est facultatif parce que PNRP est le programme de résolution par défaut.</span><span class="sxs-lookup"><span data-stu-id="e5194-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="e5194-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e5194-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e5194-106">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="e5194-106">\<bindings></span></span>  
<span data-ttu-id="e5194-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e5194-107">\<customBinding></span></span>  
<span data-ttu-id="e5194-108">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="e5194-108">\<binding></span></span>  
<span data-ttu-id="e5194-109">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="e5194-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5194-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5194-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5194-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e5194-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e5194-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e5194-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5194-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="e5194-113">Attributes</span></span>  
  
|<span data-ttu-id="e5194-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="e5194-114">Attribute</span></span>|<span data-ttu-id="e5194-115">Description</span><span class="sxs-lookup"><span data-stu-id="e5194-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5194-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="e5194-116">resolverType</span></span>|<span data-ttu-id="e5194-117">Chaîne qui spécifie le programme de résolution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e5194-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="e5194-118">Cet attribut est facultatif.</span><span class="sxs-lookup"><span data-stu-id="e5194-118">This attribute is optional.</span></span> <span data-ttu-id="e5194-119">S'il n'est pas défini ou s'il a pour valeur une chaîne vide, PNRP est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e5194-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5194-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e5194-120">Child Elements</span></span>  
 <span data-ttu-id="e5194-121">None</span><span class="sxs-lookup"><span data-stu-id="e5194-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5194-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e5194-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e5194-123">Élément</span><span class="sxs-lookup"><span data-stu-id="e5194-123">Element</span></span>|<span data-ttu-id="e5194-124">Description</span><span class="sxs-lookup"><span data-stu-id="e5194-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5194-125">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="e5194-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="e5194-126">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="e5194-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e5194-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="e5194-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5194-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5194-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>  
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="e5194-129">Liaisons</span><span class="sxs-lookup"><span data-stu-id="e5194-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e5194-130">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="e5194-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="e5194-131">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="e5194-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="e5194-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e5194-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="e5194-133">Programmes de résolution d’homologue</span><span class="sxs-lookup"><span data-stu-id="e5194-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
