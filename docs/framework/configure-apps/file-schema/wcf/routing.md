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
# <a name="ltroutinggt"></a>&lt;routage&gt;

Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l'évaluation des messages entrants, ainsi que des tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu'un filtre correspond.

[**\<system.serviceModel >**](system-servicemodel.md)   
&nbsp;&nbsp;**\<routage >**

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

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

Aucune

### <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [**\<filtres >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | Contient un jeu des filtres de routage permettant de déterminer le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter à utiliser lors de l'évaluation des messages entrants. |
| [**\<filterTables >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | Contient les mappages entre les filtres de routage et les points de terminaison cibles permettant de spécifier le point de terminaison à utiliser lorsque le filtre correspond. |

### <a name="parent-elements"></a>Éléments parents

|     | Description |
| --- | ----------- |
| **\<système. ServiceModel >** | Élément racine de tous les éléments de configuration WCF. |

## <a name="see-also"></a>Voir aussi

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
