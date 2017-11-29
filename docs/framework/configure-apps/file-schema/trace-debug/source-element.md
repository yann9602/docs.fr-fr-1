---
title: "&lt;source&gt; élément"
ms.date: 09/29/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 129888986a933fe875aade153f6becd8439d4704
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsourcegt-element"></a>&lt;source&gt; élément
Spécifie une source de trace qui lance des messages de traçage.  
  
 \<configuration>  
\<System.Diagnostics >  
\<sources >  
\<source >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Attribut facultatif.<br /><br /> Spécifie le nom de la source de trace.|  
|`switchName`|Attribut facultatif.<br /><br /> Spécifie le nom d’une instance de commutateur de trace dans l’application. Si le commutateur n’est pas identifié dans un `<switches>` élément, la valeur spécifie le niveau du commutateur.|  
|`switchType`|Attribut facultatif.<br /><br /> Spécifie le type du commutateur de trace. Le cas échéant, le type doit être un nom de classe valide et ne peut pas être une chaîne vide.|  
|`extraAttribute`|Attribut facultatif.<br /><br /> Spécifie la valeur d’un attribut spécifique à la source de trace identifié par le <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> méthode pour cette source de trace.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<listeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|Contient des écouteurs qui collectent, stocker et acheminer les messages.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`sources`|Contient les sources de trace qui lancent des messages de traçage.|  
  
## <a name="remarks"></a>Remarques  
 Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (Machine.config) et le fichier de configuration d’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `<source>` élément à ajouter la source de suivi `mySource` et pour définir le niveau du commutateur source nommé `sourceSwitch`. Un écouteur de suivi de console est ajouté qui écrit des informations de traçage dans la console.  
  
```xml  
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
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres de trace et de débogage](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [Commutateurs de suivi](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
