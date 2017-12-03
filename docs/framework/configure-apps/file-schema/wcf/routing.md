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
ms.openlocfilehash: 7cbe682ef9f7bca25ab4f5089a295ada9a00a8bc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltroutinggt"></a><span data-ttu-id="56173-102">&lt;routage&gt;</span><span class="sxs-lookup"><span data-stu-id="56173-102">&lt;routing&gt;</span></span>

<span data-ttu-id="56173-103">Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l'évaluation des messages entrants, ainsi que des tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu'un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="56173-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="56173-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="56173-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="56173-105">&nbsp;&nbsp;**\<routage >**</span><span class="sxs-lookup"><span data-stu-id="56173-105">&nbsp;&nbsp;**\<routing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="56173-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56173-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="56173-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="56173-107">Attributes and elements</span></span>

<span data-ttu-id="56173-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="56173-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="56173-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="56173-109">Attributes</span></span>

<span data-ttu-id="56173-110">Aucune</span><span class="sxs-lookup"><span data-stu-id="56173-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="56173-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="56173-111">Child elements</span></span>

|     | <span data-ttu-id="56173-112">Description</span><span class="sxs-lookup"><span data-stu-id="56173-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="56173-113">**\<filtres >**</span><span class="sxs-lookup"><span data-stu-id="56173-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="56173-114">Contient un jeu des filtres de routage permettant de déterminer le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter à utiliser lors de l'évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="56173-114">Contains a set of routing filters that determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="56173-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="56173-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="56173-116">Contient les mappages entre les filtres de routage et les points de terminaison cibles permettant de spécifier le point de terminaison à utiliser lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="56173-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="56173-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="56173-117">Parent elements</span></span>

|     | <span data-ttu-id="56173-118">Description</span><span class="sxs-lookup"><span data-stu-id="56173-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="56173-119">**\<système. ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="56173-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="56173-120">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="56173-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="56173-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56173-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
