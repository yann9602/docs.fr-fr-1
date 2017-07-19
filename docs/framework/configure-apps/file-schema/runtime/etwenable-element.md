---
title: "&lt;etwEnable&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "<etwEnable> (élément)"
  - "etwEnable (élément)"
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;etwEnable&gt;, &#233;l&#233;ment
Spécifie s'il convient d'activer le traçage d'événements pour Windows \(ETW\) pour les événements Common Language Runtime.  
  
## Syntaxe  
  
```  
<etwEnable enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|activé|Attribut requis.<br /><br /> Spécifie si ETW doit être activé.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|true|Enable ETW  C'est la valeur par défaut pour les versions de Windows qui commence avec les systèmes d'exploitation Windows Server 2008 et Windows Vista.|  
|false|Désactive ETW.  C'est la valeur par défaut pour les versions antérieures de Windows.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 À partir de Windows Vista, ETW est activé par défaut.  Utilisez cet élément pour désactiver ETW pour une application.  Dans les versions antérieures de Windows, utilisez cet élément pour activer ETW pour une application.  
  
> [!NOTE]
>  ETW peut être activé ou désactivé globalement sur un serveur en utilisant un paramètre du Registre.  Consultez [Controlling .NET Framework Logging](../../../../../docs/framework/performance/controlling-logging.md).  
  
## Exemple  
 L'exemple suivant indique comment activer le traçage ETW pour une application.  
  
```  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Controlling .NET Framework Logging](../../../../../docs/framework/performance/controlling-logging.md)