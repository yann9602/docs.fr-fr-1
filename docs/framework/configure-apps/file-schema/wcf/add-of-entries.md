---
title: '&lt;add&gt; de &lt;entries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b01ad9e608fca669c28124cf5a68781d86058308
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltentriesgt"></a>&lt;add&gt; de &lt;entries&gt;
Représente une entrée de routage qui mappe un filtre à un point de terminaison client défini précédemment. Les messages correspondant à ce filtre sont envoyés à cette destination.  
  
 \<system.serviceModel >  
\<routage >  
\<routingTables >  
\<table >  
\<entrées >  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|backupList|Chaîne qui spécifie une référence à une liste de sauvegarde de points de terminaison.|  
|Point de terminaison (endpoint)|Chaîne qui spécifie une référence à un point de terminaison client qui reçoit les messages correspondant au filtre indiqué par l'attribut `filterName`.|  
|filterName|Chaîne qui spécifie une référence à un élément de filtre.|  
|priority|Entier qui spécifie la priorité de cette entrée.<br /><br /> Les entrées dans la table de routage sont évaluées selon leur priorité, 0 correspondant à la priorité la plus basse. Toutes les entrées d'une priorité donnée sont évaluées simultanément, si aucune entrée correspondante n'est trouvée pour la priorité actuelle, le niveau de priorité suivant est évalué.<br /><br /> Cette valeur est facultative.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<routage >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Section de configuration qui contient les entrées de mappage de routage.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
