---
title: "&lt;add&gt;, &#233;l&#233;ment de &lt;switches&gt; | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<add> (élément de <switches>)"
  - "add (élément de <switches>)"
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;add&gt;, &#233;l&#233;ment de &lt;switches&gt;
Spécifie le niveau auquel un commutateur de traçage est défini.  
  
## Syntaxe  
  
```  
<add name="switch name"  
     value="value"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**nom**|Attribut requis.<br /><br /> Spécifie le nom du commutateur.  La valeur de cet attribut correspond au paramètre *displayName* passé au constructeur de commutateur.|  
|**par défaut**|Attribut requis.<br /><br /> Spécifie le niveau du commutateur.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`switches`|Contient des commutateurs de traçage et le niveau auquel les commutateurs de traçage sont définis.|  
|`system.diagnostics`|Spécifie les écouteurs de traçage qui collectent, stockent et routent des messages, ainsi que le niveau auquel un commutateur de traçage est défini.|  
  
## Notes  
 Vous pouvez changer le niveau d'un commutateur de traçage en le plaçant dans un fichier de configuration.  Si le commutateur est du type <xref:System.Diagnostics.BooleanSwitch>, vous pouvez l'activer et le désactiver.  Si le commutateur est du type <xref:System.Diagnostics.TraceSwitch>, vous pouvez lui assigner différents niveaux pour spécifier les types de messages de traçage ou de débogage que l'application enverra.  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'élément **\<add\>** pour définir le commutateur de traçage `General` au niveau [TraceLevel.Error](frlrfSystemDiagnosticsTraceLevelClassTopic) et comment activer le commutateur de traçage `Data` de type booléen.  
  
```  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Diagnostics.Switch>   
 <xref:System.Diagnostics.TraceSwitch>   
 <xref:System.Diagnostics.BooleanSwitch>   
 [Schéma des paramètres de traçage et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)