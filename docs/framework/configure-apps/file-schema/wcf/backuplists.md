---
title: "&lt;backupLists&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;backupLists&gt;
Représente une section de configuration pour la définition d'un ensemble de services de sauvegarde utilisés dans la gestion des erreurs.  Chaque élément enfant est une liste de sauvegarde qui énumère un ensemble de points de terminaison à utiliser par le service de routage s'il est impossible d'atteindre le point de terminaison primaire. Si le premier point de terminaison de la liste est inactif, le service de routage bascule automatiquement sur le suivant dans la liste. Vous disposez ainsi d'une méthode rapide pour renforcer la fiabilité de votre application sans avoir à apprendre à votre application cliente à gérer des modèles complexes ou à rechercher l'emplacement de tous vos services déployés.  
  
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
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filtre\>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|Contient une liste de points de terminaison à utiliser par le service de routage en cas d'inaccessibilité du point de terminaison principal.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<router\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de <xref:System.ServiceModel.Dispatcher.MessageFilter> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] à utiliser lors de l'évaluation des messages entrants, ainsi que des tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu'un filtre correspond.|  
  
## Voir aussi  
 [System.ServiceModel.Routing.Configuration.BackupListCollection](assetId:///System.ServiceModel.Routing.Configuration.BackupListCollection?qualifyHint=False&amp;autoUpgrade=True)