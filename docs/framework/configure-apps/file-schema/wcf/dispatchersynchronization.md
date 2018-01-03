---
title: '&lt;dispatcherSynchronization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57477ea60337e5032b80bd9ae8da850099dd08f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="70171-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="70171-102">&lt;dispatcherSynchronization&gt;</span></span>

<span data-ttu-id="70171-103">Spécifie un comportement de point de terminaison qui permet à un service d'envoyer des réponses de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="70171-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>

<span data-ttu-id="70171-104">\<system.serviceModel > \<comportements > \<endpointBehaviors > \<comportement ></span><span class="sxs-lookup"><span data-stu-id="70171-104">\<system.serviceModel> \<behaviors> \<endpointBehaviors> \<behavior></span></span>

## <a name="syntax"></a><span data-ttu-id="70171-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70171-105">Syntax</span></span>

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a><span data-ttu-id="70171-106">Type</span><span class="sxs-lookup"><span data-stu-id="70171-106">Type</span></span>

`Type`

## <a name="attributes-and-elements"></a><span data-ttu-id="70171-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="70171-107">Attributes and elements</span></span>

<span data-ttu-id="70171-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="70171-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="70171-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="70171-109">Attributes</span></span>

| <span data-ttu-id="70171-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="70171-110">Attribute</span></span>               | <span data-ttu-id="70171-111">Description</span><span class="sxs-lookup"><span data-stu-id="70171-111">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="70171-112">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="70171-112">asynchronousSendEnabled</span></span> | <span data-ttu-id="70171-113">Valeur booléenne qui indique si un comportement d'envoi asynchrone est activé.</span><span class="sxs-lookup"><span data-stu-id="70171-113">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="70171-114">Entier qui spécifie le nombre de réceptions simultanées qui peuvent être émises sur le canal.</span><span class="sxs-lookup"><span data-stu-id="70171-114">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="70171-115">Cette valeur doit être configurée uniquement après avoir correctement configuré le comportement de limitation de service.</span><span class="sxs-lookup"><span data-stu-id="70171-115">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="70171-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="70171-116">Child elements</span></span>

<span data-ttu-id="70171-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="70171-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="70171-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="70171-118">Parent elements</span></span>

| <span data-ttu-id="70171-119">Élément</span><span class="sxs-lookup"><span data-stu-id="70171-119">Element</span></span> | <span data-ttu-id="70171-120">Description</span><span class="sxs-lookup"><span data-stu-id="70171-120">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="70171-121">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="70171-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="70171-122">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="70171-122">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="70171-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70171-123">See also</span></span>

 <span data-ttu-id="70171-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="70171-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
