---
title: "&lt;filtre&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;filtre&gt;
Définit un filtre de routage, qui détermine le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l'évaluation des messages entrants, ainsi que toutes les données et paramètres de prise en charge requis par le filtre.  
  
## Syntaxe  
  
```vb  
  
<routing>  
      <filters>  
        <filter customType=”String”  
                filterData=”String”  
                filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"   
                name="String" />  
      </filters>  
</routing>  
  
```  
  
```csharp  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|customType|Chaîne qui contient le nom qualifié complet du type personnalisé à utiliser comme filtre. Si `filterType`a la valeur `custom`, cet attribut contient le nom de type qualifié complet de la classe à créer. `filterData` peut contenir également des valeurs à utiliser pendant l'évaluation du filtre de type personnalisé.|  
|filterData|Chaîne qui contient la données de filtre.  Pour plus d'informations sur la spécification de cet attribut, consultez <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.|  
|filterType|Chaîne qui contient le type de filtre.  Cet attribut est de type <xref:System.ServiceModel.Routing.Configuration.FilterType>.  Pour plus d'informations sur l'utilisation de cet attribut avec l'attribut `filterData`, consultez <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.|  
|name|Chaîne qui contient le nom unique de cet élément de filtre.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<router\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Section de configuration pour définir un jeu de filtres de routage, déterminant le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l'évaluation des messages entrants.|  
  
## Voir aussi  
 [System.ServiceModel.Routing.Configuration.FilterElement](assetId:///System.ServiceModel.Routing.Configuration.FilterElement?qualifyHint=False&amp;autoUpgrade=True)   
 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>   
 <xref:System.ServiceModel.Routing.Configuration.FilterType>