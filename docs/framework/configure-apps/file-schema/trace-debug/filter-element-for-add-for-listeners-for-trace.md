---
title: "&lt;filter&gt;, &#233;l&#233;ment de &lt;add&gt; pour &lt;listeners&gt; pour &lt;trace&gt; | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<filter> (élément de <add> pour <listeners> pour <trace>)"
  - "filter (élément de <add> pour <listeners> pour <trace>)"
  - "initializeData (attribut)"
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;filter&gt;, &#233;l&#233;ment de &lt;add&gt; pour &lt;listeners&gt; pour &lt;trace&gt;
Ajoute un filtre à un écouteur de la collection `Listeners` d'une trace.  
  
## Syntaxe  
  
```  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`type`|Attribut requis.<br /><br /> Spécifie le type du filtre, qui doit hériter de la classe <xref:System.Diagnostics.TraceFilter>.  Vous pouvez utiliser le nom qualifié par un espace de noms du type, lequel correspond à la propriété <xref:System.Type.FullName%2A> du type. Vous pouvez, par ailleurs, utiliser le nom qualifié complet du type, avec les informations d'assembly, lequel correspond à la propriété <xref:System.Type.AssemblyQualifiedName%2A>.  Pour plus d'informations sur les noms qualifiés complets, consultez [Spécification des noms de types qualifiés complets](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Attribut facultatif.<br /><br /> Chaîne passée au constructeur pour la classe de filtre spécifiée.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de traçage qui collectent, stockent et routent des messages, ainsi que le niveau auquel un commutateur de traçage est défini.|  
|`trace`|Contient des écouteurs qui collectent, stockent et routent des messages de traçage.|  
|`listeners`|Contient des écouteurs qui collectent, stockent et routent des messages.  Les écouteurs dirigent la sortie de traçage vers une cible appropriée.|  
|`add`|Ajoute un écouteur à la collection `Listeners`.|  
  
## Notes  
 L'élément `<filter>` doit être contenu dans un élément `<add>` pour un écouteur de trace qui spécifie le type de l'écouteur et non uniquement le nom d'un écouteur défini dans un [\<sharedListeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).  Si l'écouteur est défini dans un [\<sharedListeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), le filtre de cet écouteur doit être défini dans cet élément.  
  
 Cet élément peut être utilisé dans le fichier de configuration machine \(Machine.config\) et dans le fichier de configuration de l'application.  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'élément `<filter>`  pour ajouter un filtre à l'écouteur `console` dans la collection `Listeners` d'une trace, en spécifiant `Error` comme niveau d'événement du filtre.  
  
```  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.TraceListener>   
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=fullName>   
 <xref:System.Diagnostics.TraceFilter>   
 [Schéma des paramètres de traçage et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)