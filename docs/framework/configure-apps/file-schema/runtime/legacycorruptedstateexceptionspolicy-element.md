---
title: "&lt;legacyCorruptedStateExceptionsPolicy&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "<legacyCorruptedStateExceptionsPolicy> (élément)"
  - "legacyCorruptedStateExceptionsPolicy (élément)"
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;legacyCorruptedStateExceptionsPolicy&gt;, &#233;l&#233;ment
Spécifie si le Common Language Runtime permet au code managé d'intercepter les violations d'accès et d'autres exceptions d'état endommagé.  
  
## Syntaxe  
  
```  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie que l'application interceptera les échecs liés aux exceptions d'état endommagé tels que les violations d'accès.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|L'application n'interceptera pas les échecs liés aux exceptions d'état endommagé tels que les violations d'accès.  Il s'agit de la valeur par défaut.|  
|`true`|L'application interceptera les échecs liés aux exceptions d'état endommagé tels que les violations d'accès.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Dans le .NET Framework version 3.5 et antérieure, le Common Language Runtime autorise le code managé à intercepter les exceptions levées par des états de processus endommagés.  Une violation d'accès est un exemple de ce type d'exception.  
  
 Depuis le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], le code managé n'intercepte plus ces types d'exceptions dans les blocs `catch`.  Toutefois, vous pouvez substituer cette modification et maintenir la gestion des exceptions d'état endommagé de deux façons :  
  
-   Dans l'élément `<legacyCorruptedStateExceptionsPolicy>`, affectez à l'attribut `enabled` la valeur `true`.  Ce paramètre de configuration est appliqué au niveau du processus et affecte toutes les méthodes.  
  
 ou  
  
-   Appliquez l'attribut <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName> à la méthode qui contient le bloc `catch` d'exceptions.  
  
 Cet élément de configuration est disponible uniquement dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] et versions ultérieures.  
  
## Exemple  
 L'exemple suivant indique comment spécifier que l'application doit rétablir le comportement avant le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] et intercepter tous les échecs liés aux exceptions d'état endommagé.  
  
```  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>   
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)