---
title: "&lt;remove&gt;, &#233;l&#233;ment de &lt;listeners&gt; pour &lt;source&gt; | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<remove> (élément de <listeners> pour <source>)"
  - "remove (élément de <listeners> pour <source>)"
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# &lt;remove&gt;, &#233;l&#233;ment de &lt;listeners&gt; pour &lt;source&gt;
Supprime un écouteur de la collection `Listeners` pour une source de trace.  
  
## Syntaxe  
  
```  
<remove name="listenerName" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`name`|Attribut requis.<br /><br /> Nom de l'écouteur à supprimer de la collection `Listeners`.|  
  
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
 L'élément `<remove>` supprime un écouteur spécifié de la collection `Listeners` pour une source de trace.  
  
 Vous pouvez supprimer par programme un élément de la collection `Listeners` pour une source de trace en appelant la méthode <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> sur la propriété <xref:System.Diagnostics.TraceSource.Listeners%2A> de l'instance de <xref:System.Diagnostics.TraceSource>.  
  
 Cet élément peut être utilisé dans le fichier de configuration machine \(Machine.config\) et dans le fichier de configuration de l'application.  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'élément `<remove>` avant d'utiliser l'élément `<add>` pour ajouter l'écouteur `console` à la collection `Listeners` pour la source de trace `TraceSourceApp`.  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## Voir aussi  
 <xref:System.Diagnostics.TraceSource.Listeners%2A>   
 <xref:System.Diagnostics.TraceSource>   
 [Schéma des paramètres de traçage et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [\<clear\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)