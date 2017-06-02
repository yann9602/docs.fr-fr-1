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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<remove> (élément)"
  - "remove (élément)"
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# &lt;remove&gt;, &#233;l&#233;ment de &lt;listeners&gt; pour &lt;source&gt;
Supprime un écouteur de la collection **Listeners**.  
  
## Syntaxe  
  
```  
  
<remove name="listener name" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**name**|Attribut requis.<br /><br /> Nom de l'écouteur à supprimer de la collection **Listeners**.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`listeners`|Spécifie un écouteur qui collecte, stocke et route des messages.  Les écouteurs dirigent la sortie de traçage vers une cible appropriée.|  
|`system.diagnostics`|Spécifie les écouteurs de traçage qui collectent, stockent et routent des messages, ainsi que le niveau auquel un commutateur de traçage est défini.|  
|`trace`|Configuration du service de trace ASP.NET.|  
  
## Notes  
  
> [!NOTE]
>  La suppression du <xref:System.Diagnostics.DefaultTraceListener> de la collection `Listeners` modifie le comportement des méthodes <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> et <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>.  L'appel d'une méthode `Assert` ou `Fail` provoque normalement l'affichage d'une boîte de message ; toutefois, la boîte de message ne s'affiche pas si <xref:System.Diagnostics.DefaultTraceListener> n'est pas dans la collection `Listeners`.  
  
## Exemple  
 L'exemple suivant montre comment supprimer l'écouteur de trace par défaut de la collection **Listeners** de traçage.  
  
```  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Diagnostics.TraceListener>   
 <xref:System.Diagnostics.DefaultTraceListener>   
 <xref:System.Diagnostics.TextWriterTraceListener>   
 <xref:System.Diagnostics.EventLogTraceListener>   
 [Schéma des paramètres de traçage et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)