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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed2dd4e68584d6e79e18fc9b61fcc8f078615dac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltroutinggt"></a><span data-ttu-id="b14a5-102">&lt;routage&gt;</span><span class="sxs-lookup"><span data-stu-id="b14a5-102">&lt;routing&gt;</span></span>

<span data-ttu-id="b14a5-103">Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l'évaluation des messages entrants, ainsi que des tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu'un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="b14a5-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="b14a5-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="b14a5-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="b14a5-105">&nbsp;&nbsp;**\<routage >**</span><span class="sxs-lookup"><span data-stu-id="b14a5-105">&nbsp;&nbsp;**\<routing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b14a5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b14a5-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b14a5-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b14a5-107">Attributes and elements</span></span>

<span data-ttu-id="b14a5-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b14a5-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b14a5-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="b14a5-109">Attributes</span></span>

<span data-ttu-id="b14a5-110">Aucune</span><span class="sxs-lookup"><span data-stu-id="b14a5-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="b14a5-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b14a5-111">Child elements</span></span>

|     | <span data-ttu-id="b14a5-112">Description</span><span class="sxs-lookup"><span data-stu-id="b14a5-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b14a5-113">**\<filtres >**</span><span class="sxs-lookup"><span data-stu-id="b14a5-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="b14a5-114">Contient un jeu des filtres de routage permettant de déterminer le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter à utiliser lors de l'évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="b14a5-114">Contains a set of routing filters that determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="b14a5-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="b14a5-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="b14a5-116">Contient les mappages entre les filtres de routage et les points de terminaison cibles permettant de spécifier le point de terminaison à utiliser lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="b14a5-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="b14a5-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b14a5-117">Parent elements</span></span>

|     | <span data-ttu-id="b14a5-118">Description</span><span class="sxs-lookup"><span data-stu-id="b14a5-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="b14a5-119">**\<système. ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="b14a5-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="b14a5-120">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="b14a5-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="b14a5-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b14a5-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
