---
title: "&#201;l&#233;ment &lt;Thread_UseAllCpuGroups&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# &#201;l&#233;ment &lt;Thread_UseAllCpuGroups&gt;
Spécifie si le runtime distribue des threads managés dans tous les groupes d'UC.  
  
## Syntaxe  
  
```vb  
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime distribue des threads managés dans tous les groupes d'UC.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|Le runtime ne distribue pas les threads managés entre plusieurs groupes d'UC.  Valeur par défaut.|  
|`true`|Le runtime distribue les threads managés entre les différents groupes d'UC, si l'ordinateur a différents groupes d'UC et que l'élément [\<GCCpuGroup\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) est activé.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Lorsqu'un ordinateur a plusieurs groupes d'UC, l'activation de cet élément conduit le runtime à distribuer les threads managés à travers plusieurs groupes d'UC.  Pour utiliser cette fonctionnalité, vous devez également activer l'élément [\<GCCpuGroup\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md), qui étend le garbage collection à tous les groupes d'UC et prend en considération tous les cœurs lors de la création et de l'équilibrage de charge des tas.  Activation de l'élément [\<GCCpuGroup\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) requiert l'activation de l'élément [\<gcServer\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md).  Si ces éléments ne sont pas activées, l'activation de l'élément `<Thread_UseAllCpuGroups>` n'a aucun effet.  
  
## Exemple  
 L'exemple suivant montre comment activer la prise en charge de plusieurs groupes d'UC.  
  
```  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<GCCpuGroup\>, élément](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)