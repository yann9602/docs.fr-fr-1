---
title: '&lt;filters&gt; de &lt;routing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c9dd9faf63ade725bb8bea12b40390fd30c91973
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="6b30e-102">&lt;filters&gt; de &lt;routing&gt;</span><span class="sxs-lookup"><span data-stu-id="6b30e-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="6b30e-103">Représente une section de configuration qui définit un jeu des filtres de routage, déterminant le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l'évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="6b30e-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="6b30e-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="6b30e-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="6b30e-105">&nbsp;&nbsp;[**\<routage >**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="6b30e-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="6b30e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filtres >**</span><span class="sxs-lookup"><span data-stu-id="6b30e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6b30e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b30e-107">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String" 
              filterData="String" 
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6b30e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6b30e-108">Attributes and elements</span></span>

<span data-ttu-id="6b30e-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6b30e-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6b30e-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="6b30e-110">Attributes</span></span>

<span data-ttu-id="6b30e-111">Aucune</span><span class="sxs-lookup"><span data-stu-id="6b30e-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="6b30e-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6b30e-112">Child elements</span></span>

|     | <span data-ttu-id="6b30e-113">Description</span><span class="sxs-lookup"><span data-stu-id="6b30e-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6b30e-114">**\<Filtre >**</span><span class="sxs-lookup"><span data-stu-id="6b30e-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="6b30e-115">Contient un filtre de routage qui détermine le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l'évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="6b30e-115">Contains a routing filter that determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="6b30e-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6b30e-116">Parent elements</span></span>

|     | <span data-ttu-id="6b30e-117">Description</span><span class="sxs-lookup"><span data-stu-id="6b30e-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6b30e-118">**\<routage >**</span><span class="sxs-lookup"><span data-stu-id="6b30e-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="6b30e-119">Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l'évaluation des messages entrants, ainsi que des tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu'un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="6b30e-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="6b30e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b30e-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
