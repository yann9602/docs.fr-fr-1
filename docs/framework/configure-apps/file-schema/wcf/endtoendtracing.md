---
title: "&lt;endToEndTracing&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;endToEndTracing&gt;
Élément de configuration qui vous permet d'activer et désactiver différents aspects du suivi de bout en bout pendant l'exécution d'une application de service.  
  
## Syntaxe  
  
```  
  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`activityTracing`|Valeur booléenne qui spécifie si le suivi d'activité est activé.|  
|`messageFlowTracing`|Valeur booléenne qui spécifie si le suivi de flux de messages est activé.|  
|`propagateActivity`|Valeur booléenne qui spécifie si l'attribut de propagation a la valeur True.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<diagnostics\>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Définit des paramètres WCF pour l'inspection et le contrôle au moment de l'exécution pour l'administrateur.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>   
 <xref:System.ServiceModel.Diagnostics>   
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>   
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>   
 [Suivi de bout en bout](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)