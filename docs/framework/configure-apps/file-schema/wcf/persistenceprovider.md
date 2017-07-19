---
title: "&lt;persistenceProvider&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;persistenceProvider&gt;
Indique le type d'implémentation de fournisseur de persistance à utiliser, ainsi que le délai d'expiration à utiliser pour les opérations de persistance.  
  
## Syntaxe  
  
```  
  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|persistenceOperationTimeout|Valeur <xref:System.TimeSpan> indiquant le délai d'expiration utilisé pour les opérations de persistance.  La valeur par défaut est « 00:00:30 ».|  
|type|Chaîne indiquant le type à utiliser pour la fabrique de fournisseurs de persistance.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
  
## Notes  
 Cet élément spécifie le fournisseur de persistance à utiliser pour sérialiser l'état d'un service WCF.  Il doit être utilisé avec le `wsHttpContextBinding` qui transmet les informations d'état dans les en\-têtes HTTP.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>   
 <xref:System.ServiceModel.Persistence.PersistenceProvider>