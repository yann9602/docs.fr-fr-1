---
title: "&lt;UseSmallInternalThreadStacks&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "<UseSmallInternalThreadStacks> (élément)"
  - "UseSmallInternalThreadStacks (élément)"
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;UseSmallInternalThreadStacks&gt;, &#233;l&#233;ment
Demande que le Common Language Runtime \(CLR\) réduise l'utilisation de la mémoire en spécifiant des tailles de pile explicites lorsqu'il crée certains threads qu'il emploie en interne, au lieu d'utiliser la taille de pile par défaut pour ces threads.  
  
## Syntaxe  
  
```  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|activé|Attribut requis.<br /><br /> Spécifie s'il convient de demander que le CLR utilise des tailles de pile explicites au lieu de la taille de pile par défaut lorsqu'il crée certains threads qu'il emploie en interne.  Les tailles de pile explicites sont inférieures à la taille de pile par défaut de 1 Mo.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|true|Demandez des tailles de pile explicites.|  
|false|Utilisez la taille de pile par défaut.  Valeur par défaut pour [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Cet élément de configuration est utilisé pour demander l'utilisation réduite de la mémoire virtuelle dans un processus, parce que les tailles de threads explicites utilisées par le CLR pour ses threads internes sont plus petites que la taille par défaut \(si la demande est honorée\).  
  
> [!IMPORTANT]
>  Cet élément de configuration est une demande au CLR plutôt qu'une spécification absolue.  Dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], la demande est honorée uniquement pour l'architecture x86.  Cet élément peut complètement être ignoré dans les versions ultérieures du CLR ou remplacé par des tailles de piles explicites qui sont toujours utilisées pour les threads internes sélectionnés.  
  
 La spécification de cet élément de configuration privilégie une moindre utilisation de la mémoire virtuelle au détriment de la fiabilité si le CLR répond à la requête car la réduction des tailles de pile peut augmenter les risques de dépassement de capacité.  
  
## Exemple  
 L'exemple suivant montre comment demander que le CLR emploie des tailles de pile explicites pour certains threads qu'il utilise en interne.  
  
```  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)