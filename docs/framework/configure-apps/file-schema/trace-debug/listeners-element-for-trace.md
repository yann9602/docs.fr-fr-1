---
title: "&lt;écouteurs&gt; , élément pour &lt;trace&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 97d6673fddb20e99454bf97c87254049b82f0000
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlistenersgt-element-for-lttracegt"></a>&lt;écouteurs&gt; , élément pour &lt;trace&gt;
Spécifie un écouteur qui collecte, stocke et achemine les messages. Les écouteurs dirigent la sortie de traçage vers une cible appropriée.  
  
 \<configuration > élément  
\<System.Diagnostics > élément  
\<trace > élément  
\<écouteurs >, élément pour \<trace >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Ajoute un écouteur à la collection `Listeners`.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|Efface la collection `Listeners` de la trace.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|Supprime un écouteur de la `Listeners` collection.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
|`trace`|Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.|  
  
## <a name="remarks"></a>Remarques  
 Le <xref:System.Diagnostics.Debug> et <xref:System.Diagnostics.Trace> classes partagent le même **écouteurs** collection. Si vous ajoutez un objet écouteur à la collection dans un de ces classes, l’autre classe utilise le même écouteur. Les classes d’écouteur livrées avec le .NET Framework dérivent la <xref:System.Diagnostics.TraceListener> classe.  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (Machine.config) et le fichier de configuration d’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le  **\<écouteurs >** élément pour ajouter les écouteurs `MyListener` et `MyEventListener` à la **écouteurs** collection. `MyListener`Crée un fichier appelé `MyListener.log` et écrit la sortie dans le fichier. `MyEventListener`Crée une entrée dans le journal des événements.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"   
          type="System.Diagnostics.TextWriterTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"   
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Diagnostics.TraceListener>  
 [Schéma des paramètres de trace et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
