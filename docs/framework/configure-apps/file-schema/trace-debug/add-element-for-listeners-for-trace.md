---
title: "&lt;add&gt;, &#233;l&#233;ment de &lt;listeners&gt; pour &lt;trace&gt; | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<add> (élément de <listeners>)"
  - "add (élément de <listeners>)"
  - "initializeData (attribut)"
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
caps.latest.revision: 24
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 22
---
# &lt;add&gt;, &#233;l&#233;ment de &lt;listeners&gt; pour &lt;trace&gt;
Ajoute un écouteur à la collection **Listeners**.  
  
## Syntaxe  
  
```  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**type**|Attribut requis.<br /><br /> Spécifie le type de l'écouteur.  Vous devez utiliser une chaîne conforme aux exigences spécifiées dans [Spécification des noms de types qualifiés complets](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|Attribut facultatif.<br /><br /> Chaîne passée au constructeur pour la classe spécifiée.|  
|**nom**|Attribut facultatif.<br /><br /> Spécifie le nom de l'écouteur.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|Ajoute un filtre à un écouteur de la collection `Listeners` d'une trace.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`listeners`|Spécifie un écouteur qui collecte, stocke et route des messages.  Les écouteurs dirigent la sortie de traçage vers une cible appropriée.|  
|`system.diagnostics`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
|`trace`|Contient des écouteurs qui collectent, stockent et routent des messages de traçage.|  
  
## Notes  
 Les classes <xref:System.Diagnostics.Debug> et <xref:System.Diagnostics.Trace> partagent la même collection **Listeners**.  Si vous ajoutez un objet Listener à la collection dans l'une de ces classes, l'autre classe utilise le même écouteur.  Les classes d'écouteur dérivent de la [classe TraceListener](frlrfSystemDiagnosticsTraceListenerClassTopic).  
  
 Si vous ne spécifiez pas l'attribut `nam`e de l'écouteur de la trace, le <xref:System.Diagnostics.TraceListener.Name%2A> de l'écouteur de la trace prend comme valeur par défaut une chaîne vide \(""\).  Si votre application n'a qu'un écouteur, vous pouvez l'ajouter sans spécifier de nom et le supprimer en spécifiant une chaîne vide en tant que nom.  Toutefois, si votre application a plusieurs écouteurs, vous devez spécifier des noms uniques pour chaque écouteur de la trace, ce qui permet d'identifier et de gérer des écouteurs de trace individuels dans les collections <xref:System.Diagnostics.Debug.Listeners%2A> et <xref:System.Diagnostics.Trace.Listeners%2A>.  
  
> [!NOTE]
>  Si vous ajoutez plusieurs écouteurs de la trace possédant le même type et le même nom, un seul écouteur de la trace de ce type et de ce nom est ajouté à la collection `Listeners`.  Toutefois, vous pouvez ajouter par programme plusieurs écouteurs identiques à la collection `Listeners`.  
  
 La valeur de l'attribut **initializeData** dépend du type d'écouteur que vous créez.  Il n'est pas nécessaire de spécifier **initializeData** pour tous les écouteurs de la trace.  
  
> [!NOTE]
>  Lorsque vous utilisez l'attribut `initializeData`, le message d'avertissement du compilateur suivant peut s'afficher : « L'attribut 'initializeData' n'est pas déclaré. ». Cet avertissement s'affiche, car les paramètres de configuration sont validés par rapport à la classe de base abstraite <xref:System.Diagnostics.TraceListener>, qui ne reconnaît pas l'attribut `initializeData`.  En général, vous pouvez ignorer cet avertissement pour les implémentations de l'écouteur de la trace disposant d'un constructeur qui accepte un paramètre.  
  
 Le tableau suivant présente les écouteurs de la trace inclus avec le .NET Framework et décrit la valeur de leur attribut **initializeData**.  
  
|Classe d'écouteurs de traces|initializeData, valeur d'attribut|  
|----------------------------------|---------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=fullName>|Valeur `useErrorStream` pour le constructeur <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>.  Affectez la valeur "`true`" à l'attribut `initializeData` pour écrire la sortie de la trace et de débogage à <xref:System.Console.Error%2A?displayProperty=fullName> ; "`false`" pour écrire à <xref:System.Console.Out%2A?displayProperty=fullName>.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=fullName>|Nom du fichier vers lequel <xref:System.Diagnostics.DelimitedListTraceListener> écrit.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName>|Nom d'une source existante de journal des événements.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=fullName>|Nom du fichier dans lequel <xref:System.Diagnostics.EventSchemaTraceListener> écrit.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=fullName>|Nom du fichier dans lequel <xref:System.Diagnostics.TextWriterTraceListener> écrit.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=fullName>|Nom du fichier dans lequel <xref:System.Diagnostics.XmlWriterTraceListener> écrit.|  
  
## Exemple  
 L'exemple suivant indique comment utiliser les éléments **\<add\>** pour ajouter les écouteurs `MyListener` et `MyEventListener` à la collection **Listeners**.  `MyListener` crée un fichier appelé `MyListener.log` et écrit la sortie dans le fichier.  `MyEventListener` crée une entrée dans le journal des événements.  
  
```  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.Debug>   
 <xref:System.Diagnostics.EventLogTraceListener>   
 <xref:System.Diagnostics.ConsoleTraceListener>   
 <xref:System.Diagnostics.TextWriterTraceListener>   
 [Schéma des paramètres de traçage et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)