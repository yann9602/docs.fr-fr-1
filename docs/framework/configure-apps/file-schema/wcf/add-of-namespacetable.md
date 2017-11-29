---
title: '&lt;add&gt; de &lt;namespaceTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f08f4b46c6e6290602fc78a2f06954b9cf0b07d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a>&lt;add&gt; de &lt;namespaceTable&gt;
Représente un élément de configuration qui contient un mappage espace de noms-préfixe à utiliser dans des filtres XPath pour le routage.  
  
 \<system.serviceModel >  
\<routage >  
\<namespaceTable >  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|namespace|Chaîne qui contient l'espace de noms.|  
|prefix|Chaîne qui contient le préfixe de cet espace de noms.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<namespaceTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|Représente une section de configuration qui permet de définir un ensemble d’éléments contenant des mappages espace de noms-préfixe qui peuvent ensuite être utilisés dans des filtres XPath pour le routage.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
