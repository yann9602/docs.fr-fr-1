---
title: "&lt;add&gt;, &#233;l&#233;ment de &lt;listeners&gt; pour &lt;source&gt; | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<add> (élément de <listeners> pour <source>)"
  - "<add> (élément de <listeners> pour <source>)"
  - "initializeData (attribut)"
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# &lt;add&gt;, &#233;l&#233;ment de &lt;listeners&gt; pour &lt;source&gt;
Ajoute un écouteur à la collection `Listeners` pour une source de trace.  
  
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
|`type`|Attribut requis.<br /><br /> Spécifie le type de l'écouteur.  Vous devez utiliser une chaîne qui répond aux conditions énoncées dans [Spécification des noms de types qualifiés complets](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Attribut facultatif.<br /><br /> Chaîne passée au constructeur pour la classe spécifiée.  Une exception <xref:System.Configuration.ConfigurationException> est levée si la classe ne possède pas de constructeur qui prend une chaîne.|  
|`name`|Attribut facultatif.<br /><br /> Spécifie le nom de l'écouteur.|  
|`traceOutputOptions`|Attribut facultatif.<br /><br /> Spécifie la valeur de la propriété <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> pour l'écouteur de la trace.|  
|\[attributs personnalisés\]|Attributs facultatifs.<br /><br /> Spécifie la valeur des attributs spécifiques à l'écouteur identifiés par la méthode <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> pour cet écouteur.  <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> est un exemple d'attribut supplémentaire unique à la classe <xref:System.Diagnostics.DelimitedListTraceListener>.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|Ajoute un filtre à un écouteur dans la collection `Listeners` pour une source de trace.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de traçage qui collectent, stockent et routent des messages, ainsi que le niveau auquel un commutateur de traçage est défini.|  
|`sources`|Contient des sources de trace qui initient des messages de traçage.|  
|`source`|Spécifie une source de trace qui initie le traçage des messages.|  
|`listeners`|Spécifie des écouteurs qui collectent, stockent et routent des messages.|  
  
## Notes  
 Les classes d'écouteur livrées avec le .NET Framework dérivent de la classe <xref:System.Diagnostics.TraceListener>.  
  
 Si vous ne spécifiez pas l'attribut `name` de l'écouteur de la trace, la propriété <xref:System.Diagnostics.TraceListener.Name%2A> de l'écouteur de la trace prend comme valeur par défaut une chaîne vide \(""\).  Si votre application n'a qu'un seul écouteur, vous pouvez l'ajouter sans spécifier de nom et le supprimer en spécifiant une chaîne vide en tant que nom.  Toutefois, si votre application possède plusieurs écouteurs, vous devez spécifier un nom unique pour chaque écouteur de la trace, ce qui permet d'identifier et de gérer des écouteurs de trace individuels dans la collection <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=fullName>.  
  
> [!NOTE]
>  Si vous ajoutez plusieurs écouteurs de la trace possédant le même type et le même nom, un seul écouteur de la trace de ce type et de ce nom est ajouté à la collection `Listeners`.  Toutefois, vous pouvez ajouter par programme plusieurs écouteurs identiques à la collection `Listeners`.  
  
 La valeur de l'attribut `initializeData` dépend du type d'écouteur que vous créez.  Il n'est pas nécessaire de spécifier `initializeData` pour tous les écouteurs de la trace.  
  
> [!NOTE]
>  Lorsque vous utilisez l'attribut `initializeData`, le message d'avertissement du compilateur suivant peut s'afficher : « L'attribut 'initializeData' n'est pas déclaré. ». Cet avertissement s'affiche, car les paramètres de configuration sont validés par rapport à la classe de base abstraite <xref:System.Diagnostics.TraceListener>, qui ne reconnaît pas l'attribut `initializeData`.  En général, vous pouvez ignorer cet avertissement pour les implémentations de l'écouteur de la trace disposant d'un constructeur qui accepte un paramètre.  
  
 Le tableau suivant présente les écouteurs de la trace inclus avec le .NET Framework et décrit la valeur de leur attribut `initializeData`.  
  
|Classe d'écouteurs de traces|initializeData, valeur d'attribut|  
|----------------------------------|---------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=fullName>|Valeur `useErrorStream` pour le constructeur <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>.  Affectez la valeur `true` à l'attribut `initializeData` pour écrire la sortie de la trace et du débogage dans le flux d'erreurs standard ; affectez\-lui la valeur `false` pour l'écrire dans le flux de sortie standard.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=fullName>|Nom du fichier vers lequel <xref:System.Diagnostics.DelimitedListTraceListener> écrit.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName>|Nom d'une source existante de journal des événements.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=fullName>|Nom du fichier dans lequel <xref:System.Diagnostics.EventSchemaTraceListener> écrit.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=fullName>|Nom du fichier dans lequel <xref:System.Diagnostics.TextWriterTraceListener> écrit.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=fullName>|Nom du fichier dans lequel <xref:System.Diagnostics.XmlWriterTraceListener> écrit.|  
  
## Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration machine \(Machine.config\) et dans le fichier de configuration de l'application.  
  
## Exemple  
 L'exemple suivant montre comment utiliser des éléments `<add>` pour ajouter les écouteurs `console` et `textListener` à la collection `Listeners` pour la source de trace `TraceSourceApp`.  L'écouteur `textListener` écrit la sortie de la trace dans le fichier myListener.log.  
  
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