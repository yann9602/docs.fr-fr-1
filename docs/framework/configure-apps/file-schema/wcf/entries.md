---
title: "&lt;entries&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;entries&gt;
Entrée de routage qui contient des mappages entre les filtres de routage et les points de terminaison cibles vers lesquels envoyer des messages lorsque le filtre correspond.  
  
## Syntaxe  
  
```vb  
  
<routing>  
      <filterTables>  
        <filterTable name="String">  
          <entries>  
            <add backupList=”String”  
                 endpointName="String"   
                 filterName="String"   
                 priority="Integer" />  
          </entries>  
        </table>  
      </routingTables>  
</routing>  
  
```  
  
```csharp  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filtres\>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|Mappe un filtre à un point de terminaison client précédemment défini.  Les messages correspondant à ce filtre sont envoyés à cette destination.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<router\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Section de configuration qui contient une table de routage.|  
  
## Voir aussi  
 [System.ServiceModel.Routing.Configuration.RoutingSection](assetId:///System.ServiceModel.Routing.Configuration.RoutingSection?qualifyHint=False&amp;autoUpgrade=True)   
 [System.ServiceModel.Routing.Configuration.FilterTableEntryElement](assetId:///System.ServiceModel.Routing.Configuration.FilterTableEntryElement?qualifyHint=False&amp;autoUpgrade=True)