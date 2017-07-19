---
title: "&lt;gcConcurrent&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<gcConcurrent> (élément)"
  - "balises conteneurs, <gcConcurrent> (élément)"
  - "gcConcurrent (élément)"
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# &lt;gcConcurrent&gt;, &#233;l&#233;ment
Spécifie si le common language runtime exécute l'opération garbage collection sur un thread distinct.  
  
## Syntaxe  
  
```  
<gcConcurrent    
   enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime exécute l'opération garbage collection simultanément.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|N'exécute pas l'opération garbage collection simultanément.|  
|`true`|Exécute l'opération garbage collection simultanément.  Il s'agit de la valeur par défaut.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Dans les versions antérieures à .NET Framework 4, le garbage collection de station de travail prenait en charge le garbage collection simultané, qui exécutait l'opération garbage collection en arrière\-plan sur un thread distinct.  Dans .NET Framework 4, le garbage collection simultané a été remplacé par le garbage collection d'arrière\-plan pour effectuer l'opération de la même manière.  Depuis .NET Framework 4.5, le garbage collection d'arrière\-plan est disponible dans le garbage collection de serveur.  L'élément `<gcConcurrent>` contrôle si le runtime exécute le garbage collection simultané ou d'arrière\-plan, s'il est disponible, ou s'il exécute le garbage collection de premier plan.  
  
> [!WARNING]
>  Depuis .NET Framework 4, le garbage collection simultané est remplacé par le garbage collection d'arrière\-plan.  Les termes *simultané* et *d'arrière\-plan* sont utilisés indifféremment dans la documentation .NET Framework.  Pour désactiver le garbage collection d'arrière\-plan, utilisez l'élément `<gcConcurrent>` comme indiqué dans cet article.  
  
 Par défaut, le runtime utilise le garbage collection simultané ou d'arrière\-plan, dont la latence est optimisée.  Si votre application implique une grande interaction avec l'utilisateur, laissez le garbage collection simultané activé pour minimiser le temps d'interruption de l'application pendant l'exécution de l'opération garbage collection.  Si vous définissez l'attribut `enabled` de l'élément `<gcConcurrent>` avec la valeur `false`, le runtime utilise le garbage collection non simultané, dont le débit est optimisé.  Le fichier de configuration suivant désactive le garbage collection d'arrière\-plan.  
  
```xml  
  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false"/>  
   </runtime>  
</configuration>  
  
```  
  
 Le paramètre `<gcConcurrentSetting>` qui figure dans le fichier de configuration de l'ordinateur définit la valeur par défaut de toutes les applications .NET Framework.  Ce paramètre se substitue au paramètre du fichier de configuration de l'application.  
  
 Pour plus d'informations sur le garbage collection simultané et d'arrière\-plan, voir la section sur le garbage collection simultané dans la rubrique [Fundamentals of Garbage Collection](../../../../../docs/standard/garbage-collection/fundamentals.md).  
  
## Exemple  
 L'exemple suivant active le garbage collection simultané.  
  
```  
  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="true"/>  
   </runtime>  
</configuration>  
  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Fundamentals of Garbage Collection](../../../../../docs/standard/garbage-collection/fundamentals.md)