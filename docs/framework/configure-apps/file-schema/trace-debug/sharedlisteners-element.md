---
title: "&lt;sharedListeners&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<sharedListeners> (élément)"
  - "écouteurs"
  - "écouteurs partagés"
  - "sharedListeners (élément)"
  - "écouteurs de traçage, <sharedListeners> (élément)"
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# &lt;sharedListeners&gt;, &#233;l&#233;ment
Contient des écouteurs qui peuvent être référencés par n'importe quel élément trace ou source.  Ces écouteurs ne reçoivent pas de traces par défaut et il n'est pas possible de les récupérer au moment de l'exécution.  Les écouteurs identifiés comme des écouteurs partagés peuvent être ajoutés aux sources ou aux traces par nom.  
  
## Syntaxe  
  
```  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun.  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Ajoute un écouteur à la collection `sharedListeners`.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`Configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
  
## Notes  
 L'ajout d'un écouteur à la collection sharedListeners ne l'active pas pour autant.  Il doit encore être ajouté à une source de trace ou à une trace en l'ajoutant à la collection `Listeners` de cet élément trace.  Les classes d'écouteur du .NET Framework dérivent de la classe <xref:System.Diagnostics.TraceListener>.  
  
 Cet élément peut être utilisé dans le fichier de configuration machine \(Machine.config\) et dans le fichier de configuration de l'application.  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'élément `<sharedListeners>` pour ajouter l'écouteur `console` à la collection `Listeners` pour les classes <xref:System.Diagnostics.TraceSource> et <xref:System.Diagnostics.Trace>.  L'écouteur de la trace console écrit des informations de traçage dans la console par des appels à <xref:System.Diagnostics.TraceSource> ou à <xref:System.Diagnostics.Trace>.  
  
```  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration></system.diagnostics>   
```  
  
## Voir aussi  
 <xref:System.Diagnostics.TraceListener>   
 [Schéma des paramètres de traçage et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)