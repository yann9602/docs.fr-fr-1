---
title: "&lt;workflowIdle&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;workflowIdle&gt;
Comportement de service qui contrôle à quel moment les instances de workflow inactives sont déchargées et rendues persistantes.  
  
## Syntaxe  
  
```  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name=String">  
      <workflowIdle timeToPersist=”TimeSpan”  
          timeToUnload=”TimeSpan” />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|timeToPersist|Valeur Timespan qui spécifie la durée entre le moment où le flux de travail devient inactif et celui où il est rendu persistant.  La valeur par défaut est TimeSpan.MaxValue.<br /><br /> La durée commence à s'écouler lorsque l'instance de flux de travail devient inactive.  Cet attribut s'avère utile si vous souhaitez rendre une instance de flux de travail persistante de manière plus agressive tout en conservant quand même l'instance dans la mémoire aussi longtemps que possible.  Cet attribut est valide uniquement si sa valeur est inférieure à celle de l'attribut **timeToUnload**.  Si elle est supérieure, elle est ignorée.  Si cet attribut s'écoule avant la valeur spécifiée par l'attribut **timeToUnload**, la persistance doit s'effectuer avant que le flux de travail ne soit déchargé.  Cela implique un éventuel retard de l'opération de déchargement tant que le flux de travail n'a pas été rendu persistant.  La couche de persistance est responsable de la gestion de toutes les tentatives pour les erreurs temporaires et lève uniquement des exceptions sur les erreurs non récupérables.  Par conséquent, toutes les exceptions levées pendant la persistance sont traitées comme fatales et l'instance de flux de travail est abandonnée.|  
|timeToUnload|Valeur Timespan qui spécifie la durée entre l'inactivation et le déchargement du flux de travail.  La valeur par défaut est égale à 1 minute.<br /><br /> Le déchargement d'un flux de travail implique qu'il soit également rendu persistant.  Si cet attribut a la valeur zéro, l'instance de flux de travail est rendue persistante et immédiatement déchargée une fois que le flux de travail devient inactif.  Affecter à cet attribut la valeur TimeSpan.MaxValue désactive l'opération de déchargement.  Les instances de flux de travail inactives ne sont jamais déchargées.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior\> de \<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Spécifie un élément de comportement.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>   
 <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>