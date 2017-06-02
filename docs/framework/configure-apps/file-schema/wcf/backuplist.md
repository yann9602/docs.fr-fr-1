---
title: "&lt;backupList&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;backupList&gt;
Représente une section de configuration pour définir une liste de sauvegarde qui énumère un ensemble de points de terminaison à utiliser par le service de routage en cas d'inaccessibilité du point de terminaison principal. Si le premier point de terminaison de la liste est inactif, le service de routage bascule automatiquement sur le suivant dans la liste. Vous disposez ainsi d'une méthode rapide pour renforcer la fiabilité de votre application sans avoir à apprendre à votre application cliente à gérer des modèles complexes ou à rechercher l'emplacement de tous vos services déployés.  
  
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
|name|Chaîne qui spécifie le nom permettant d'identifier la liste de points de terminaison.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filtre\>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<router\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Liste de points de terminaison de sauvegarde.|  
  
## Notes  
 Cette section contient une collection ordonnée de points de terminaison auxquels un message sera transmis si une exception de communication se produit lors de l'envoi au point de terminaison primaire.  
  
 En cas d'échec d'un envoi au point de terminaison primaire répertorié dans l'attribut `endpointName` de [\<ajouter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) avec une exception de communication, le service de routage tente d'envoyer le message au premier point de terminaison dans cette section de configuration.  Si l'opération échoue également avec une exception de communication, le service de routage essaie d'envoyer le message au point de terminaison suivant contenu dans cette section jusqu'à ce que la tentative d'envoi aboutisse, retourne une erreur autre qu'une exception de communication, ou que tous les points de terminaison de la collection retournent une erreur.  
  
 Dans l'exemple suivant, si un envoi au point de terminaison primaire appelé « Destination » retourne une exception de communication, le service essaiera d'envoyer le message à « alternateServiceQueue ».  Si cette tentative retourne également une exception de communication, le service de routage essaiera d'envoyer le message au point de terminaison suivant dans la collection.  
  
```  
  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
## Voir aussi  
 [System.ServiceModel.Routing.Configuration.BackupEndpointCollection](assetId:///System.ServiceModel.Routing.Configuration.BackupEndpointCollection?qualifyHint=False&amp;autoUpgrade=True)