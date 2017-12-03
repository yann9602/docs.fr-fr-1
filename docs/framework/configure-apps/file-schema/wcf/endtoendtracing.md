---
title: '&lt;endToEndTracing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb187302000291fd6b540b562ed7aebf1db7add2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltendtoendtracinggt"></a>&lt;endToEndTracing&gt;
Élément de configuration qui vous permet d'activer et désactiver différents aspects du suivi de bout en bout pendant l'exécution d'une application de service.  
  
 \<système. ServiceModel >  
\<diagnostic >  
\<endToEndTracing >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`activityTracing`|Valeur booléenne qui spécifie si le suivi d'activité est activé.|  
|`messageFlowTracing`|Valeur booléenne qui spécifie si le suivi de flux de messages est activé.|  
|`propagateActivity`|Valeur booléenne qui spécifie si l'attribut de propagation a la valeur True.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Diagnostics >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Définit des paramètres WCF pour l'inspection et le contrôle au moment de l'exécution pour l'administrateur.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [Suivi de bout en bout](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
