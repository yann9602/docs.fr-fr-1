---
title: "&lt;add&gt; de &lt;backupList&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;add&gt; de &lt;backupList&gt;
Représente un élément de configuration qui définit un élément de point de terminaison de sauvegarde.  
  
## Syntaxe  
  
```vb  
  
<routing>  
  <backupLists>  
    <backupList name="String">  
      <add endpointName="String" />  
    </backupList>    
  </backupLists>  
</routing>  
  
```  
  
```csharp  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|name|Chaîne qui spécifie le nom du point de terminaison de sauvegarde.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<router\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Contient une liste de points de terminaison à utiliser par le service de routage en cas d'inaccessibilité du point de terminaison principal.|  
  
## Voir aussi  
 [System.ServiceModel.Routing.Configuration.BackupEndpointElement](assetId:///System.ServiceModel.Routing.Configuration.BackupEndpointElement?qualifyHint=False&amp;autoUpgrade=True)