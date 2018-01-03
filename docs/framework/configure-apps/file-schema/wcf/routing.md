---
title: '&lt;routage&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ef71753a4b0ff20a966842119adb6e637ded1f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltroutinggt"></a><span data-ttu-id="89c61-102">&lt;routage&gt;</span><span class="sxs-lookup"><span data-stu-id="89c61-102">&lt;routing&gt;</span></span>

<span data-ttu-id="89c61-103">Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l'évaluation des messages entrants, ainsi que des tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu'un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="89c61-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="89c61-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="89c61-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="89c61-105">&nbsp;&nbsp;**\<routage >**</span><span class="sxs-lookup"><span data-stu-id="89c61-105">&nbsp;&nbsp;**\<routing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="89c61-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89c61-106">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String" 
              filterData="String" 
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String" 
               filterName="String" 
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="89c61-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="89c61-107">Attributes and elements</span></span>

<span data-ttu-id="89c61-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="89c61-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="89c61-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="89c61-109">Attributes</span></span>

<span data-ttu-id="89c61-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="89c61-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="89c61-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="89c61-111">Child elements</span></span>

|     | <span data-ttu-id="89c61-112">Description</span><span class="sxs-lookup"><span data-stu-id="89c61-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="89c61-113">**\<filtres >**</span><span class="sxs-lookup"><span data-stu-id="89c61-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="89c61-114">Contient un jeu des filtres de routage permettant de déterminer le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter à utiliser lors de l'évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="89c61-114">Contains a set of routing filters that determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="89c61-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="89c61-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="89c61-116">Contient les mappages entre les filtres de routage et les points de terminaison cibles permettant de spécifier le point de terminaison à utiliser lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="89c61-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="89c61-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="89c61-117">Parent elements</span></span>

|     | <span data-ttu-id="89c61-118">Description</span><span class="sxs-lookup"><span data-stu-id="89c61-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="89c61-119">**\<système. ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="89c61-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="89c61-120">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="89c61-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="89c61-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89c61-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
