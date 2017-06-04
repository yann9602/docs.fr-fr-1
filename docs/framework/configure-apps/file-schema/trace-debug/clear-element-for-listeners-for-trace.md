---
title: "&lt;clear&gt;, &#233;l&#233;ment de &lt;listeners&gt; pour &lt;trace&gt; | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<clear> (élément de <listeners> pour <trace>)"
  - "<clear> (élément de <listeners> pour <trace>)"
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;clear&gt;, &#233;l&#233;ment de &lt;listeners&gt; pour &lt;trace&gt;
Efface le contenu de la collection `Listeners` de l'élément trace.  
  
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
|`trace`|Contient des écouteurs qui collectent, stockent et routent des messages de traçage.|  
|`listeners`|Contient des écouteurs qui collectent, stockent et routent des messages.  Les écouteurs dirigent la sortie de traçage vers une cible appropriée.|  
  
## Notes  
 L'élément `<clear>` supprime tous les écouteurs de la collection `Listeners` de l'élément trace.  Vous pouvez utiliser l'élément `<clear>` avant d'utiliser l'élément `<add>` pour garantir l'absence de tout autre écouteur actif dans la collection.  
  
 Vous pouvez effacer par programme le contenu de la collection `Listeners` en appelant la méthode <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> sur la propriété <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=fullName> \(`System.Diagnostics.Trace.Listeners.Clear()`\).  
  
 Cet élément peut être utilisé dans le fichier de configuration machine \(Machine.config\) et dans le fichier de configuration de l'application.  
  
> [!NOTE]
>  L'élément `<clear>` supprime le <xref:System.Diagnostics.DefaultTraceListener> de la collection `Listeners`, modifiant ainsi le comportement des méthodes <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> et <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>.  L'appel d'une méthode `Assert` ou `Fail` provoque normalement l'affichage d'une boîte de message.  Toutefois, la boîte de message ne s'affiche pas si <xref:System.Diagnostics.DefaultTraceListener> n'est pas dans la collection `Listeners`.  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'élément `<clear>` avant d'utiliser l'élément `<add>` pour ajouter l'écouteur `console` à la collection `Listeners` de l'élément trace.  
  
```  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## Voir aussi  
 <xref:System.Diagnostics.Trace.Listeners%2A>   
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.Debug>   
 <xref:System.Diagnostics.TraceSource>   
 [Schéma des paramètres de traçage et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [\<remove\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)