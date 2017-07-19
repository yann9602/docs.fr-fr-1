---
title: "&lt;filterTables&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;filterTables&gt;
Représente une section de configuration permettant de définir des tables de routage qui contiennent des mappages entre les filtres de routage et les points de terminaison cibles auxquels envoyer des messages lorsque le filtre correspond.  
  
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
|[\<filtres\>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|Table de routage qui contient des mappages entre les filtres de routage et les points de terminaison cibles vers lesquels envoyer des messages lorsque le filtre correspond.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<router\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Section de configuration qui contient des filtres de routage et des tables de routage.|  
  
## Voir aussi  
 [System.ServiceModel.Routing.Configuration.RoutingSection](assetId:///System.ServiceModel.Routing.Configuration.RoutingSection?qualifyHint=False&amp;autoUpgrade=True)   
 [System.ServiceModel.Routing.Configuration.FilterTableCollection](assetId:///System.ServiceModel.Routing.Configuration.FilterTableCollection?qualifyHint=False&amp;autoUpgrade=True)