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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 24ae6dbf0fb67b5755aca848ea7fce6abda14b0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="4e1d3-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="4e1d3-102">&lt;dispatcherSynchronization&gt;</span></span>

<span data-ttu-id="4e1d3-103">Spécifie un comportement de point de terminaison qui permet à un service d'envoyer des réponses de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="4e1d3-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>

<span data-ttu-id="4e1d3-104">\<system.serviceModel > \<comportements > \<endpointBehaviors > \<comportement ></span><span class="sxs-lookup"><span data-stu-id="4e1d3-104">\<system.serviceModel> \<behaviors> \<endpointBehaviors> \<behavior></span></span>

## <a name="syntax"></a><span data-ttu-id="4e1d3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e1d3-105">Syntax</span></span>

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a><span data-ttu-id="4e1d3-106">Type</span><span class="sxs-lookup"><span data-stu-id="4e1d3-106">Type</span></span>

`Type`

## <a name="attributes-and-elements"></a><span data-ttu-id="4e1d3-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4e1d3-107">Attributes and elements</span></span>

<span data-ttu-id="4e1d3-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4e1d3-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e1d3-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="4e1d3-109">Attributes</span></span>

| <span data-ttu-id="4e1d3-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="4e1d3-110">Attribute</span></span>               | <span data-ttu-id="4e1d3-111">Description</span><span class="sxs-lookup"><span data-stu-id="4e1d3-111">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="4e1d3-112">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="4e1d3-112">asynchronousSendEnabled</span></span> | <span data-ttu-id="4e1d3-113">Valeur booléenne qui indique si un comportement d'envoi asynchrone est activé.</span><span class="sxs-lookup"><span data-stu-id="4e1d3-113">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="4e1d3-114">Entier qui spécifie le nombre de réceptions simultanées qui peuvent être émises sur le canal.</span><span class="sxs-lookup"><span data-stu-id="4e1d3-114">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="4e1d3-115">Cette valeur doit être configurée uniquement après avoir correctement configuré le comportement de limitation de service.</span><span class="sxs-lookup"><span data-stu-id="4e1d3-115">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="4e1d3-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4e1d3-116">Child elements</span></span>

<span data-ttu-id="4e1d3-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4e1d3-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4e1d3-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4e1d3-118">Parent elements</span></span>

| <span data-ttu-id="4e1d3-119">Élément</span><span class="sxs-lookup"><span data-stu-id="4e1d3-119">Element</span></span> | <span data-ttu-id="4e1d3-120">Description</span><span class="sxs-lookup"><span data-stu-id="4e1d3-120">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="4e1d3-121">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="4e1d3-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4e1d3-122">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4e1d3-122">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="4e1d3-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e1d3-123">See also</span></span>

 <span data-ttu-id="4e1d3-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="4e1d3-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
