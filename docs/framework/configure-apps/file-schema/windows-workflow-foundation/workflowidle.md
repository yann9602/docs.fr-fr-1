---
title: '&lt;workflowIdle&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5f9b4989de57204d9ec97d69475121c30ae82644
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowidlegt"></a>&lt;workflowIdle&gt;
Comportement de service qui contrôle à quel moment les instances de workflow inactives sont déchargées et rendues persistantes.  
  
\<système. ServiceModel >  
\<comportements >  
\<serviceBehaviors >  
\<comportement >  
\<workflowIdle >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan" 
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|timeToPersist|Une valeur Timespan qui spécifie la durée entre le moment où le flux de travail devienne inactif et est rendue persistante. La valeur par défaut a la valeur TimeSpan.MaxValue.<br /><br /> La durée commence à s'écouler lorsque l'instance de flux de travail devient inactive. Cet attribut est utile si vous souhaitez conserver une instance de flux de travail plus efficacement tout en conservant l’instance en mémoire aussi longtemps que possible. Cet attribut est valide uniquement si sa valeur est inférieure à la **timeToUnload** attribut. Si elle est supérieure, elle est ignorée. Si cet attribut est écoulé avant que la valeur spécifiée par la **timeToUnload** attribut, persistance doit s’effectuer avant que le workflow est déchargé. Cela implique un éventuel retard de l'opération de déchargement tant que le flux de travail n'a pas été rendu persistant. La couche de persistance est responsable de la gestion de toutes les tentatives pour les erreurs temporaires et lève uniquement des exceptions sur les erreurs non récupérables. Par conséquent, toutes les exceptions levées pendant la persistance sont traitées comme fatales et l'instance de flux de travail est abandonnée.|  
|timeToUnload|Valeur Timespan qui spécifie la durée entre l'inactivation et le déchargement du flux de travail. La valeur par défaut est égale à 1 minute.<br /><br /> Le déchargement d'un flux de travail implique qu'il soit également rendu persistant. Si cet attribut est défini à zéro l’instance de workflow est persistant et déchargée immédiatement après le workflow devient inactif. Cet attribut TimeSpan.MaxValue efficacement désactive l’opération de déchargement. Les instances de flux de travail inactives ne sont jamais déchargées.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement > de \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Spécifie un élément de comportement.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
