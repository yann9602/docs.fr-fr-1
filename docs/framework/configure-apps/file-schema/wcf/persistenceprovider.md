---
title: '&lt;persistenceProvider&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d93a9ea8614f98c968d499c2f95dcd3962f0020
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="e6520-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="e6520-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="e6520-103">Indique le type d'implémentation de fournisseur de persistance à utiliser, ainsi que le délai d'expiration à utiliser pour les opérations de persistance.</span><span class="sxs-lookup"><span data-stu-id="e6520-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="e6520-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e6520-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e6520-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="e6520-105">\<behaviors></span></span>  
<span data-ttu-id="e6520-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e6520-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e6520-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="e6520-107">\<behavior></span></span>  
<span data-ttu-id="e6520-108">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="e6520-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6520-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6520-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6520-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e6520-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e6520-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e6520-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6520-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="e6520-112">Attributes</span></span>  
  
|<span data-ttu-id="e6520-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="e6520-113">Attribute</span></span>|<span data-ttu-id="e6520-114">Description</span><span class="sxs-lookup"><span data-stu-id="e6520-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6520-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="e6520-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="e6520-116">Valeur <xref:System.TimeSpan> indiquant le délai d'expiration utilisé pour les opérations de persistance.</span><span class="sxs-lookup"><span data-stu-id="e6520-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="e6520-117">La valeur par défaut est « 00 : 00:30 ».</span><span class="sxs-lookup"><span data-stu-id="e6520-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="e6520-118">type</span><span class="sxs-lookup"><span data-stu-id="e6520-118">type</span></span>|<span data-ttu-id="e6520-119">Chaîne indiquant le type à utiliser pour la fabrique de fournisseurs de persistance.</span><span class="sxs-lookup"><span data-stu-id="e6520-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6520-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e6520-120">Child Elements</span></span>  
 <span data-ttu-id="e6520-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e6520-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6520-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e6520-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e6520-123">Élément</span><span class="sxs-lookup"><span data-stu-id="e6520-123">Element</span></span>|<span data-ttu-id="e6520-124">Description</span><span class="sxs-lookup"><span data-stu-id="e6520-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6520-125">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="e6520-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e6520-126">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="e6520-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6520-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="e6520-127">Remarks</span></span>  
 <span data-ttu-id="e6520-128">Cet élément spécifie le fournisseur de persistance à utiliser pour sérialiser l'état d'un service WCF.</span><span class="sxs-lookup"><span data-stu-id="e6520-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="e6520-129">Il doit être utilisé avec le `wsHttpContextBinding` qui transmet les informations d'état dans les en-têtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="e6520-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6520-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6520-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
