---
title: "&lt;system.diagnostics&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<system.diagnostics> (élément)"
  - "system.diagnostics (élément)"
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# &lt;system.diagnostics&gt;, &#233;l&#233;ment
Spécifie les écouteurs de traçage qui collectent, stockent et routent des messages, ainsi que le niveau auquel un commutateur de traçage est défini.  
  
## Syntaxe  
  
```  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun.  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<assert\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|Spécifie s'il convient d'afficher une boîte de message lorsque vous appelez la méthode <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>; spécifie également le nom du fichier dans lequel écrire les messages.|  
|[\<performanceCounters\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|Spécifie la taille de la mémoire globale partagée par les compteurs de performance.|  
|[\<sharedListeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|Contient des écouteurs qui peuvent être référencés par n'importe quel élément trace ou source.  Les écouteurs identifiés comme des écouteurs partagés peuvent être ajoutés aux sources ou aux traces par nom.|  
|[\<sources\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|Spécifie les sources de trace qui initient des messages de traçage.|  
|[\<commutateurs\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|Contient des commutateurs de traçage et les niveaux auxquels les commutateurs de traçage sont définis.|  
|[\<trace\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|Contient des écouteurs qui collectent, stockent et routent des messages de traçage.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## Exemple  
 L'exemple suivant montre comment incorporer un commutateur de traçage et un écouteur de traçage dans l'élément **\<system.diagnostics\>**.  Le commutateur de traçage `General` est défini au niveau [TraceLevel.Error](frlrfSystemDiagnosticsTraceLevelClassTopic).  L'écouteur de traçage `myListener` crée un fichier `MyListener.log` et écrit la sortie dans ce fichier.  
  
> [!NOTE]
>  Dans le .NET Framework version 2.0, vous pouvez utiliser le texte pour spécifier la valeur d'un commutateur.  Par exemple, vous pouvez spécifier `true` pour un <xref:System.Diagnostics.BooleanSwitch> ou utiliser le texte représentant une valeur d'énumération telle que `Error` pour un <xref:System.Diagnostics.TraceSwitch>.  La ligne `<add name="myTraceSwitch" value="Error" />` équivaut à `<add name="myTraceSwitch" value="1" />`.  
  
```  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.Debug>   
 [Schéma des paramètres de traçage et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)