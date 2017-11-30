---
title: "&lt;écouteurs&gt; , élément pour &lt;source&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 71b11cbc34bdbb5d414aa250ea2c2fce85cfac0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlistenersgt-element-for-ltsourcegt"></a>&lt;écouteurs&gt; , élément pour &lt;source&gt;
Ajoute ou supprime des écouteurs dans la <xref:System.Diagnostics.TraceSource.Listeners%2A> collection pour un <xref:System.Diagnostics.TraceSource>. Un écouteur dirige la sortie de traçage vers une cible appropriée, par exemple un journal, une fenêtre ou un fichier texte.  
  
 \<configuration>  
\<System.Diagnostics >  
\<sources >  
\<source >  
\<écouteurs > élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|Ajoute un écouteur à la collection `Listeners`.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|Supprime un écouteur de la `Listeners` collection.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|Efface la collection `Listeners` pour une source de trace.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`sources`|Contient les sources de trace qui lancent des messages de traçage.|  
|`source`|Spécifie une source de trace qui lance des messages de traçage.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (Machine.config) et le fichier de configuration d’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `<listeners>` élément à ajouter un écouteur de suivi de console à la `mySource` source et de supprimer l’écouteur de trace par défaut.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Diagnostics.TraceListener>  
 [Schéma des paramètres de trace et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [Écouteurs de suivi](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
