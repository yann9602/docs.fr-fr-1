---
title: "&lt;trace&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#trace"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<trace> (élément)"
  - "écouteurs"
  - "trace (élément)"
  - "écouteur de la trace, <trace> (élément)"
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;trace&gt;, &#233;l&#233;ment
Contient des écouteurs qui collectent, stockent et routent des messages de traçage.  
  
## Syntaxe  
  
```  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`autoflush`|Attribut facultatif.<br /><br /> Spécifie si les écouteurs de traçage vident automatiquement la mémoire tampon de sortie après chaque opération d'écriture.|  
|`indentsize`|Attribut facultatif.<br /><br /> Spécifie le nombre d'espaces pour la mise en retrait.|  
|`useGlobalLock`|Attribut facultatif.<br /><br /> Indique si le verrouillage global doit être utilisé.|  
  
## autoflush, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|Ne vide pas automatiquement la mémoire tampon de sortie.  Il s'agit de la valeur par défaut.|  
|`true`|Vide automatiquement la mémoire tampon de sortie.|  
  
## useGlobalLock, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|N'utilise le verrouillage global que si l'écouteur est thread\-safe.|  
|`true`|Utilise le verrouillage global que l'écouteur soit thread\-safe ou non.  Il s'agit de la valeur par défaut.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<listeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|Spécifie un écouteur qui collecte, stocke et route des messages.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de traçage qui collectent, stockent et routent des messages, ainsi que le niveau auquel un commutateur de traçage est défini.|  
  
## Exemple  
 L'exemple suivant indique comment utiliser l'élément `<trace>` pour ajouter l'écouteur `MyListener` à la collection `Listeners`.  `MyListener` crée un fichier nommé `MyListener.log` et écrit la sortie dans le fichier.  Lorsque l'attribut `useGlobalLock` a la valeur `false`, le verrouillage global n'est pas utilisé si l'écouteur de la trace est thread\-safe.  Lorsque l'attribut `autoflush` a la valeur `true`, l'écouteur de la trace écrit dans le fichier, que la méthode <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=fullName> soit appelée ou non.  Lorsque l'attribut `indentsize` a la valeur 0 \(zéro\), l'écouteur met en retrait des espaces nuls lorsque la méthode <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=fullName> est appelée.  
  
```  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
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