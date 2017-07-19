---
title: "&lt;add&gt;, &#233;l&#233;ment de &lt;sharedListeners&gt; | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<add> (élément de <sharedListeners>)"
  - "add (élément de <sharedListeners>)"
  - "initializeData (attribut)"
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;add&gt;, &#233;l&#233;ment de &lt;sharedListeners&gt;
Ajoute un écouteur à la collection `sharedListeners`.  `sharedListeners` est une collection d'écouteurs que tout [\<source\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) ou [\<trace\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) peut référencer.  Par défaut, les écouteurs de la collection `sharedListeners` ne sont pas placés dans une collection `Listeners`.  Leur nom doit être ajouté à [\<source\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) ou à [\<trace\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).  Il n'est pas possible d'obtenir les écouteurs de la collection `sharedListeners` dans le code au moment de l'exécution.  
  
## Syntaxe  
  
```  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`name`|Attribut requis.<br /><br /> Spécifie le nom de l'écouteur utilisé pour ajouter l'écouteur partagé à une collection `Listeners`.|  
|`type`|Attribut requis.<br /><br /> Spécifie le type de l'écouteur.  Vous devez utiliser une chaîne qui répond aux conditions énoncées dans [Spécification des noms de types qualifiés complets](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Attribut facultatif.<br /><br /> Chaîne passée au constructeur pour la classe spécifiée.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|Ajoute un filtre à un écouteur de la collection `sharedListeners`.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de traçage qui collectent, stockent et routent des messages, ainsi que le niveau auquel un commutateur de traçage est défini.|  
|`sharedListeners`|Collection d'écouteurs qui peut être référencée par tout élément source ou de trace.|  
  
## Notes  
 Les classes d'écouteur livrées avec le .NET Framework dérivent de la classe <xref:System.Diagnostics.TraceListener>.  La valeur de l'attribut `name` est utilisée pour ajouter l'écouteur partagé à une collection `Listeners` pour une trace ou une source de trace.  La valeur de l'attribut `initializeData` dépend du type d'écouteur que vous créez.  Il n'est pas nécessaire de spécifier `initializeData` pour tous les écouteurs de la trace.  
  
> [!NOTE]
>  Lorsque vous utilisez l'attribut `initializeData`, le message d'avertissement du compilateur suivant peut s'afficher : « L'attribut 'initializeData' n'est pas déclaré. ». Cet avertissement s'affiche, car les paramètres de configuration sont validés par rapport à la classe de base abstraite <xref:System.Diagnostics.TraceListener>, qui ne reconnaît pas l'attribut `initializeData`.  En général, vous pouvez ignorer cet avertissement pour les implémentations de l'écouteur de la trace disposant d'un constructeur qui accepte un paramètre.  
  
 Le tableau suivant présente les écouteurs de la trace inclus avec le .NET Framework et décrit la valeur de leur attribut `initializeData`.  
  
|Classe d'écouteurs de traces|initializeData, valeur d'attribut|  
|----------------------------------|---------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|Valeur `useErrorStream` pour le constructeur <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>.  Affectez la valeur `true` à l'attribut `initializeData` pour écrire la sortie de la trace et du débogage dans le flux d'erreurs standard ; affectez\-lui la valeur `false` pour l'écrire dans le flux de sortie standard.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|Nom du fichier vers lequel <xref:System.Diagnostics.DelimitedListTraceListener> écrit.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName>|Nom d'une source existante de journal des événements.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=fullName>|Nom du fichier dans lequel <xref:System.Diagnostics.EventSchemaTraceListener> écrit.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=fullName>|Nom du fichier dans lequel <xref:System.Diagnostics.TextWriterTraceListener> écrit.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|Nom du fichier dans lequel <xref:System.Diagnostics.XmlWriterTraceListener> écrit.|  
  
## Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration machine \(Machine.config\) et dans le fichier de configuration de l'application.  
  
## Exemple  
 L'exemple suivant montre comment utiliser des éléments `<add>` pour ajouter <xref:System.Diagnostics.TextWriterTraceListener> `textListener` à la collection `sharedListeners` .   `textListener` est ajouté par nom à la collection `Listeners` de la source de suivi `TraceSourceApp`.  L'écouteur `textListener` écrit la sortie de la trace dans le fichier myListener.log.  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## Voir aussi  
 <xref:System.Diagnostics.TraceSource>   
 <xref:System.Diagnostics.TraceListener>   
 [Schéma des paramètres de traçage et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)