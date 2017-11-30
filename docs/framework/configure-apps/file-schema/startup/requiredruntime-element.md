---
title: "&lt;requiredRuntime&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 633769573253d7516bc50f0210c30376e6aa230a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltrequiredruntimegt-element"></a>&lt;requiredRuntime&gt; élément
Spécifie que l’application prend en charge uniquement la version 1.0 du common language runtime. Cet élément est déconseillé et ne doit plus être utilisé. Le [ `supportedRuntime` ](supportedruntime-element.md) élément doit être utilisé à la place.
  
 \<configuration>  
\<démarrage >  
\<requiredRuntime >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`version`|Attribut facultatif.<br /><br /> Valeur de chaîne qui spécifie la version du .NET Framework qui prend en charge de cette application. La valeur de chaîne doit correspondre le nom de répertoire se trouve sous la racine d’installation de .NET Framework. Le contenu de la valeur de chaîne n’est pas analysé.|  
|`safemode`|Attribut facultatif.<br /><br /> Spécifie si le code de démarrage runtime recherche dans le Registre pour déterminer la version du runtime.|  
  
## <a name="safemode-attribute"></a>SafeMode attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|Le code de démarrage runtime recherche dans le Registre. Valeur par défaut.|  
|`true`|Le code de démarrage runtime ne recherche pas dans le Registre.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`startup`|Contient le `<requiredRuntime>` élément.|  
  
## <a name="remarks"></a>Remarques  
 Les applications générées pour prendre en charge uniquement la version 1.0 du runtime doivent utiliser le `<requiredRuntime>` élément. Les applications générées à l’aide de la version 1.1 ou ultérieure du runtime doivent utiliser le `<supportedRuntime>` élément.  
  
> [!NOTE]
>  Si vous utilisez la [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) de fonction pour spécifier le fichier de configuration, vous devez utiliser le `<requiredRuntime>` élément pour toutes les versions du runtime. Le `<supportedRuntime>` élément est ignoré lorsque vous utilisez [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
 Le `version` chaîne d’attribut doit correspondre au nom de dossier d’installation de la version spécifiée du .NET Framework. Cette chaîne n’est pas interprétée. Si le code de démarrage runtime ne trouve pas le dossier correspondant, le runtime n’est pas chargé ; le code de démarrage affiche un message d’erreur et se ferme.  
  
> [!NOTE]
>  Le code de démarrage d’une application qui est hébergé dans Microsoft Internet Explorer ignore le `<requiredRuntime>` élément.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier la version du runtime dans un fichier de configuration.  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres de démarrage](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver> Spécification de la version du runtime à utiliser](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)
