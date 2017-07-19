---
title: "&lt;gcServer&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<gcServer> (élément)"
  - "gcServer (élément)"
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# &lt;gcServer&gt;, &#233;l&#233;ment
Spécifie si le common language runtime exécute le garbage collection côté serveur.  
  
## Syntaxe  
  
```  
<gcServer    
   enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime exécute le garbage collection côté serveur.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|N'exécute pas le garbage collection côté serveur.  Il s'agit de la valeur par défaut.|  
|`true`|Exécute le garbage collection côté serveur.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Le common language runtime \(ou CLR\) prend en charge deux types de garbage collection : le garbage collection côté station de travail, qui est disponible sur tous les systèmes, et le garbage collection côté serveur, qui est disponible sur les systèmes multiprocesseurs.  Utilisez l'élément `<gcServer>` pour contrôler le type de garbage collection effectué par le CLR.  Utilisez la propriété <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=fullName> pour déterminer si le garbage collection côté serveur est activé.  
  
 Pour les ordinateurs monoprocesseurs, le garbage collection côté station de travail configuré par défaut représente normalement l'option la plus rapide.  L'option station de travail ou serveur peut être utilisée pour les ordinateurs biprocesseurs.  Le garbage collection côté serveur est normalement l'option la plus rapide pour les ordinateurs comptant plus de deux processeurs.  
  
 Cet élément peut être défini uniquement dans le fichier de configuration de l'application \(il est ignoré s'il est défini dans le fichier de configuration de l'ordinateur\).  
  
> [!NOTE]
>  Dans .NET Framework 4 et les versions antérieures, le garbage collection simultané n'est pas disponible si le garbage collection côté serveur est activé.  Depuis [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], le garbage collection côté serveur est simultané.  Pour utiliser le garbage collection côté serveur non simultané, définissez l'élément `<gcServer>` avec la valeur `true` et l'[élément \<gcConcurrent\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) avec la valeur `false`.  
  
## Exemple  
 L'exemple suivant active le garbage collection côté serveur.  
  
```  
  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
  
```  
  
## Voir aussi  
 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=fullName>   
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [How to: Disable Concurrent Garbage Collection](http://msdn.microsoft.com/fr-fr/ba2c6c67-5778-497c-9fac-5f793b5500c7)