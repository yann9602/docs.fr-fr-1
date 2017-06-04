---
title: "&lt;clear&gt;, &#233;l&#233;ment de &lt;listeners&gt; pour &lt;source&gt; | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<clear> (élément de <listeners> pour <source>)"
  - "<clear> (élément de <listeners> pour <source>)"
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# &lt;clear&gt;, &#233;l&#233;ment de &lt;listeners&gt; pour &lt;source&gt;
Efface le contenu de la collection `Listeners` pour une source de trace.  
  
## Syntaxe  
  
```  
<clear/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de traçage qui collectent, stockent et routent des messages, ainsi que le niveau auquel un commutateur de traçage est défini.|  
|`sources`|Contient des sources de trace qui initient des messages de traçage.|  
|`source`|Spécifie une source de trace qui initie le traçage des messages.|  
|`listeners`|Spécifie des écouteurs qui collectent, stockent et routent des messages.|  
  
## Notes  
 L'élément `<clear>` supprime tous les écouteurs de la collection `Listeners` pour une source de trace, y compris <xref:System.Diagnostics.DefaultTraceListener>.  Vous pouvez utiliser l'élément `<clear>` avant d'utiliser l'élément `<add>` pour garantir l'absence de tout autre écouteur actif dans la collection.  
  
## Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration machine \(Machine.config\) et dans le fichier de configuration de l'application.  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'élément `<clear>` avant d'utiliser l'élément `<add>` pour ajouter les écouteurs `console` et `textListener` à la collection `Listeners` pour la source de trace `TraceSourceApp`.  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## Voir aussi  
 <xref:System.Diagnostics.TraceSource>   
 <xref:System.Diagnostics.TraceListener>   
 [Schéma des paramètres de traçage et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)