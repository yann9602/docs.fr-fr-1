---
title: "&lt;filter&gt;, &#233;l&#233;ment de &lt;add&gt; pour &lt;sharedListeners&gt; | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<filter> (élément de <add> pour <sharedListeners>)"
  - "<filter> (élément de <add> pour <sharedListeners>)"
  - "filtres, écouteurs de traçage"
  - "initializeData (attribut)"
  - "écouteurs de traçage, filtres"
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# &lt;filter&gt;, &#233;l&#233;ment de &lt;add&gt; pour &lt;sharedListeners&gt;
Ajoute un filtre à un écouteur de la collection `sharedListeners`.  
  
## Syntaxe  
  
```  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**type**|Attribut requis.<br /><br /> Spécifie le type du filtre.  Vous pouvez utiliser uniquement le nom complet du type \(au format de la propriété <xref:System.Type.FullName%2A?displayProperty=fullName>\) ou utiliser le nom de type qualifié complet comprenant les informations d'assembly \(au format de la propriété <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName>\).  Pour plus d'informations sur la création d'un nom de type qualifié complet, consultez [Spécification des noms de types qualifiés complets](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|Attribut facultatif.<br /><br /> Chaîne passée au constructeur pour la classe spécifiée.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de traçage qui collectent, stockent et routent des messages, ainsi que le niveau auquel un commutateur de traçage est défini.|  
|`sharedListeners`|Collection d'écouteurs qui peut être référencée par tout élément source ou de trace.|  
|`add`|Ajoute un écouteur à la collection **sharedListeners**.|  
  
## Notes  
 Si un écouteur est défini dans un élément `<add>` de l'élément `<sharedListeners>`, le filtre de cet écouteur doit être défini dans un élément `<filter>`, qui est un enfant de l'élément `<add>`.  
  
 Cet élément peut être utilisé dans le fichier de configuration machine \(Machine.config\) et dans le fichier de configuration de l'application.  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'élément `<filter>` pour ajouter un filtre à l'écouteur de la trace `console` de la collection `sharedListeners`.  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Diagnostics.TraceFilter>   
 <xref:System.Diagnostics.TraceListener>   
 <xref:System.Diagnostics.TraceSource>   
 [Schéma des paramètres de traçage et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)