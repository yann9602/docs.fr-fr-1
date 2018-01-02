---
title: "&lt;trace&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d7ddcbdbdbbc2924d4f725d2fd401f873a4cfb0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="lttracegt-element"></a>&lt;trace&gt; élément
Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.  
  
 \<configuration>  
\<System.Diagnostics >  
\<trace >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`autoflush`|Attribut facultatif.<br /><br /> Spécifie si les écouteurs de suivi vidage automatique de la mémoire tampon de sortie après chaque opération d’écriture.|  
|`indentsize`|Attribut facultatif.<br /><br /> Spécifie le nombre d’espaces pour mettre en retrait.|  
|`useGlobalLock`|Attribut facultatif.<br /><br /> Indique si le verrouillage global doit être utilisé.|  
  
## <a name="autoflush-attribute"></a>AutoFlush attribut  
  
|Value|Description|  
|-----------|-----------------|  
|`false`|Ne vide pas automatiquement la mémoire tampon de sortie. Il s'agit de la valeur par défaut.|  
|`true`|Vide automatiquement la mémoire tampon de sortie.|  
  
## <a name="usegloballock-attribute"></a>Attribut d’useGlobalLock  
  
|Value|Description|  
|-----------|-----------------|  
|`false`|N’utilise pas le verrouillage global si l’écouteur est thread-safe ; Sinon, utilise le verrouillage global.|  
|`true`|Utilise le verrouillage global que l’écouteur soit thread-safe. Il s'agit de la valeur par défaut.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<listeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|Spécifie un écouteur qui collecte, stocke et achemine les messages.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `<trace>` élément pour ajouter l’écouteur `MyListener` à la `Listeners` collection. `MyListener`Crée un fichier nommé `MyListener.log` et écrit la sortie dans le fichier. Le `useGlobalLock` attribut est défini sur `false`, ce qui entraîne le verrouillage global doit ne pas être utilisée si l’écouteur de trace est thread-safe. Le `autoflush` attribut a la valeur `true`, ce qui entraîne l’écouteur de trace à écrire dans le fichier indépendamment du fait que le <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> méthode est appelée. Le `indentsize` attribut est défini sur 0 (zéro), l’écouteur mettre en retrait des espaces nuls lorsque la <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> méthode est appelée.  
  
```xml  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [Schéma des paramètres de trace et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
