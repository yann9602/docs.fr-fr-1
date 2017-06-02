---
title: "&lt;switches&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#switches"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<switches> (élément)"
  - "switches (élément)"
  - "commutateurs de traçage, <switches> (élément)"
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;switches&gt;, &#233;l&#233;ment
Contient des commutateurs de traçage et le niveau auquel les commutateurs de traçage sont définis.  
  
## Syntaxe  
  
```  
  
      <switches>   
</switches>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun.  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<ajouter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|Spécifie le niveau auquel un commutateur de traçage est défini.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`System.diagnostics`|Spécifie les écouteurs de traçage qui collectent, stockent et routent des messages, ainsi que le niveau auquel un commutateur de traçage est défini.|  
  
## Notes  
 Vous pouvez changer le niveau d'un commutateur de traçage en le plaçant dans un fichier de configuration.  Si le commutateur est du type <xref:System.Diagnostics.BooleanSwitch>, vous pouvez l'activer et le désactiver.  Si le commutateur est du type <xref:System.Diagnostics.TraceSwitch>, vous pouvez lui assigner différents niveaux pour spécifier les types de messages de traçage ou de débogage que l'application enverra.  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'élément **\<switch\>** pour définir le commutateur de traçage `General` à [TraceLevel.Error](frlrfSystemDiagnosticsTraceLevelClassTopic) et comment activer le commutateur de traçage au niveau `Data` de type booléen.  
  
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