---
title: "&lt;add&gt; de &lt;entries&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;add&gt; de &lt;entries&gt;
Représente une entrée de routage qui mappe un filtre à un point de terminaison client défini précédemment.  Les messages correspondant à ce filtre sont envoyés à cette destination.  
  
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
  
|Attribut|Description|  
|--------------|-----------------|  
|backupList|Chaîne qui spécifie une référence à une liste de sauvegarde de points de terminaison.|  
|Point de terminaison \(endpoint\)|Chaîne qui spécifie une référence à un point de terminaison client qui reçoit les messages correspondant au filtre indiqué par l'attribut `filterName`.|  
|filterName|Chaîne qui spécifie une référence à un élément de filtre.|  
|priority|Entier qui spécifie la priorité de cette entrée.<br /><br /> Les entrées dans la table de routage sont évaluées selon leur priorité, 0 correspondant à la priorité la plus basse.  Toutes les entrées d'une priorité donnée sont évaluées simultanément, si aucune entrée correspondante n'est trouvée pour la priorité actuelle, le niveau de priorité suivant est évalué.<br /><br /> Cette valeur est facultative.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<router\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Section de configuration qui contient les entrées de mappage de routage.|  
  
## Voir aussi  
 [System.ServiceModel.Routing.Configuration.RoutingSection](assetId:///System.ServiceModel.Routing.Configuration.RoutingSection?qualifyHint=False&amp;autoUpgrade=True)   
 [System.ServiceModel.Routing.Configuration.FilterTableEntryElement](assetId:///System.ServiceModel.Routing.Configuration.FilterTableEntryElement?qualifyHint=False&amp;autoUpgrade=True)