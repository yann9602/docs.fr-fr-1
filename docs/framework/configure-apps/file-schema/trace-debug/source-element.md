---
title: "&lt;source&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#source"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<source> (élément)"
  - "source (élément)"
ms.assetid: ecf86505-735d-4844-aaba-266fdd134218
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;source&gt;, &#233;l&#233;ment
Spécifie une source de trace qui initie le traçage des messages.  
  
## Syntaxe  
  
```  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`name`|Attribut facultatif.<br /><br /> Spécifie le nom de la source de trace.|  
|`switchName`|Attribut facultatif.<br /><br /> Spécifie le nom d'une instance de commutateur de trace dans l'application.  Si le commutateur n'est pas identifié dans un élément `<switches>`, la valeur spécifie le niveau du commutateur.|  
|`switchType`|Attribut facultatif.<br /><br /> Spécifie le type du commutateur de trace.  S'il est précisé, le type doit représenter un nom de classe valide et ne peut pas être une chaîne vide.|  
|`extraAttribute`|Attribut facultatif.<br /><br /> Spécifie la valeur d'un attribut de source\-détail de trace identifié par la méthode d' <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> pour cette source de trace.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<listeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|Contient des écouteurs qui collectent, stockent et routent des messages.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de traçage qui collectent, stockent et routent des messages, ainsi que le niveau auquel un commutateur de traçage est défini.|  
|`sources`|Contient des sources de trace qui initient des messages de traçage.|  
  
## Notes  
 Cet élément peut être utilisé dans le fichier de configuration machine \(Machine.config\) et dans le fichier de configuration de l'application.  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'élément `<source>`  pour ajouter la source de trace `mySource` et définir le niveau du commutateur source nommé `sourceSwitch`.  Un écouteur de la trace console qui écrit les informations de traçage dans la console est ajouté.  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>    
  </system.diagnostics>   
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres de traçage et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [Trace Switches](../../../../../docs/framework/debug-trace-profile/trace-switches.md)