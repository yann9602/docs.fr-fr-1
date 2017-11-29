---
title: '&lt;serviceThrottling&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6ba0f3a442e3598322f223be63b64a811c8f785a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicethrottlinggt"></a>&lt;serviceThrottling&gt;
Spécifie le mécanisme de limitation de requêtes d'un service Windows Communication Foundation (WCF).  
  
 \<système. ServiceModel >  
\<comportements >  
\<serviceBehaviors >  
\<comportement >  
\<serviceThrottling >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"  
    maxConcurrentInstances="Integer"  
    maxConcurrentSessions="Integer" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|maxConcurrentCalls|Entier positif qui limite le nombre de messages actuellement traités dans <xref:System.ServiceModel.ServiceHost>. Une fois cette limite atteinte, les appels sont mis en file d'attente. Affecter 0 à cette valeur équivaut à lui affecter la valeur Int32.MaxValue. La valeur par défaut est 16 * nombre de processeurs.|  
|maxConcurrentInstances|Entier positif qui limite le nombre d'objets <xref:System.ServiceModel.InstanceContext> exécutés à un moment donné sur <xref:System.ServiceModel.ServiceHost>. Les demandes de création d'instances supplémentaires sont mises en file d'attente et traitées lorsqu'un emplacement se libère. La valeur par défaut est la somme de maxConcurrentSessions et MaxConcurrentCalls.|  
|maxConcurrentSessions|Entier positif qui limite le nombre de sessions qu'un objet <xref:System.ServiceModel.ServiceHost> peut accepter.<br /><br /> Le service acceptera des connexions une fois la limite atteinte, mais seuls les canaux ne dépassant pas la limite seront actifs (les messages seront lus à partir du canal). Affecter 0 à cette valeur équivaut à lui affecter la valeur Int32.MaxValue. La valeur par défaut est 100 * nombre de processeurs.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
  
## <a name="remarks"></a>Remarques  
 Les contrôles de limitation de requêtes limitent le nombre d'appels, d'instances ou de sessions simultanés pour empêcher une surconsommation des ressources.  
  
 Un suivi est écrit à chaque fois que la valeur des attributs est atteinte. Le premier suivi est écrit en tant qu'avertissement.  
  
## <a name="example"></a>Exemple  
 L'exemple de configuration suivant spécifie que le service restreint le nombre maximal d'appels simultanés à 2 et le nombre maximal d'instances simultanées à 10. Pour obtenir un exemple détaillé de l’exécution de cet exemple, consultez [limitation](../../../../../docs/framework/wcf/samples/throttling.md).  
  
```xml  
<behaviors>   
  <serviceBehaviors>   
    <behavior name="CalculatorServiceBehavior">   
      <serviceDebug includeExceptionDetailInFaults="False" />   
      <serviceMetadata httpGetEnabled="True"/>   
      <!-- Specify throttling behavior -->  
      <serviceThrottling maxConcurrentCalls="2"   
           maxConcurrentInstances="10"/>   
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>  
 [Utilisation de ServiceThrottlingBehavior pour contrôler les performances de Service WCF](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
