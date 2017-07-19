---
title: "&lt;listeners&gt;, &#233;l&#233;ment de &lt;source&gt; | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<listeners> (élément de <source>)"
  - "<listeners> (élément de <source>)"
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# &lt;listeners&gt;, &#233;l&#233;ment de &lt;source&gt;
Ajoute ou supprime des écouteurs dans la collection <xref:System.Diagnostics.TraceSource.Listeners%2A> pour <xref:System.Diagnostics.TraceSource>.  Un écouteur dirige la sortie de traçage vers une cible appropriée, telle qu'un journal, une fenêtre ou un fichier texte.  
  
## Syntaxe  
  
```  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|Ajoute un écouteur à la collection `Listeners`.|  
|[\<remove\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|Supprime un écouteur de la collection `Listeners`.|  
|[\<clear\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|Efface le contenu de la collection `Listeners` pour une source de trace.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de traçage qui collectent, stockent et routent des messages, ainsi que le niveau auquel un commutateur de traçage est défini.|  
|`sources`|Contient des sources de trace qui initient des messages de traçage.|  
|`source`|Spécifie une source de trace qui initie le traçage des messages.|  
  
## Notes  
  
## Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration machine \(Machine.config\) et dans le fichier de configuration de l'application.  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'élément `<listeners>`  pour ajouter un écouteur de la trace console à la source `mySource` et pour supprimer l'écouteur de la trace par défaut.  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Diagnostics.TraceListener>   
 [Schéma des paramètres de traçage et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)