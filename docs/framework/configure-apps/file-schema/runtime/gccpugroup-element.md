---
title: "&lt;GCCpuGroup&gt;, &#233;l&#233;ment | Microsoft Docs"
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
helpviewer_keywords: 
  - "<GCCpuGroup> (élément)"
  - "GCCpuGroup (élément)"
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# &lt;GCCpuGroup&gt;, &#233;l&#233;ment
Spécifie si le garbage collection prend en charge des groupes d'UC multiples.  
  
## Syntaxe  
  
```  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le garbage collection prend en charge des groupes d'UC multiples.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|Le garbage collection ne prend pas en charge les groupes d'UC multiples.  Il s'agit de la valeur par défaut.|  
|`true`|Le garbage collection prend en charge des groupes d'UC multiples, si le garbage collection du serveur est activé.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Lorsqu'un ordinateur a des groupes d'UC multiples et que le garbage collection du serveur est activé \(consultez l'élément de [\<gcServer\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) \), autoriser cet élément étend le garbage collection à tous les groupes d'UC et prend en considération tous les cœurs lors de la génération et de l'équilibrage du tas.  
  
> [!NOTE]
>  Cet élément s'applique uniquement aux threads de garbage collection.  Pour permettre au runtime de distribuer des threads d'utilisateur dans tous les groupes d'UC, vous devez également activer l'élément [\<Thread\_UseAllCpuGroups\>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md).  
  
## Exemple  
 L'exemple suivant montre comment activer le garbage collection pour plusieurs groupes d'UC.  
  
```  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [How to: Disable Concurrent Garbage Collection](http://msdn.microsoft.com/fr-fr/ba2c6c67-5778-497c-9fac-5f793b5500c7)   
 [Garbage collection de station de travail et de serveur](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)