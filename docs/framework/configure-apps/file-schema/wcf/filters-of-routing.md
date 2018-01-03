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
ms.workload: dotnet
ms.openlocfilehash: b2687101aa868ae77ce0ae818afd9df906f8525c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltersgt-of-ltroutinggt"></a>&lt;filters&gt; de &lt;routing&gt;

Représente une section de configuration qui définit un jeu des filtres de routage, déterminant le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l'évaluation des messages entrants.

[**\<system.serviceModel >**](system-servicemodel.md)   
&nbsp;&nbsp;[**\<routage >**](routing.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<filtres >**

## <a name="syntax"></a>Syntaxe

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

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [**\<Filtre >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | Contient un filtre de routage qui détermine le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> sera utilisé lors de l’évaluation des messages entrants. |

### <a name="parent-elements"></a>Éléments parents

|     | Description |
| --- | ----------- |
| [**\<routage >**](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Représente une section de configuration pour définir un ensemble de filtres de routage, qui détermine le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants, ainsi que le routage des tables qui définissent les points de terminaison cible pour envoyer des messages lorsqu’un filtre correspond. |

## <a name="see-also"></a>Voir aussi

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
