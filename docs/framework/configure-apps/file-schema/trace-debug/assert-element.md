---
title: "&lt;assert&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#assert"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<assert> (élément)"
  - "assert (élément)"
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;assert&gt;, &#233;l&#233;ment
Spécifie s'il convient d'afficher une boîte de message lorsque vous appelez la méthode <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>; spécifie également le nom du fichier dans lequel écrire les messages.  
  
## Syntaxe  
  
```  
  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`assertuienabled`|Attribut facultatif.<br /><br /> Spécifie s'il convient d'afficher une boîte de message lorsque la méthode **Debug.Assert** prend la valeur **false**.|  
|`logfilename`|Attribut facultatif.<br /><br /> Spécifie le nom du fichier dans lequel écrire le message si **Debug.Assert** prend la valeur **false**.|  
  
## assertuienabled, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|`true`|Affiche la boîte de message.  Il s'agit de la valeur par défaut.|  
|`false`|N'affiche pas la boîte de message.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de traçage qui collectent, stockent et routent des messages, ainsi que le niveau auquel un commutateur de traçage est défini.|  
  
## Notes  
 Les attributs de l'élément **\<assert\>** sont tous deux facultatifs.  Vous pouvez désactiver les boîtes de message en ne spécifiant pas de fichier dans lequel les écrire, ou bien vous pouvez spécifier un fichier dans lequel écrire les messages tout en laissant les boîtes de message activées.  
  
## Exemple  
 L'exemple suivant montre comment désactiver l'affichage des boîtes de message lorsque vous appelez **Debug.Assert** et écrire les messages dans `c:\log.txt`.  
  
```  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Diagnostics.Debug>   
 [Schéma des paramètres de traçage et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)