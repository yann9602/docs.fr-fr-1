---
title: "&lt;requiredRuntime&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<requiredRuntime> (élément)"
  - "balises conteneurs, <requiredRuntime> (élément)"
  - "requiredRuntime (élément)"
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;requiredRuntime&gt;, &#233;l&#233;ment
Spécifie que l'application ne prend en charge que la version 1.0 du Common Language Runtime.  
  
## Syntaxe  
  
```  
  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`version`|Attribut facultatif.<br /><br /> Valeur de chaîne qui spécifie la version du .NET Framework que cette application prend en charge.  La valeur de chaîne doit correspondre au nom du répertoire se trouvant sous la racine d'installation du .NET Framework.  Le contenu de la valeur de chaîne n'est pas analysé.|  
|`safemode`|Attribut facultatif.<br /><br /> Spécifie si le code de démarrage runtime recherche la version du Common Language Runtime dans le Registre.|  
  
## safemode, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|Le code de démarrage d'exécution recherche dans le Registre.  Valeur par défaut.|  
|`true`|Le code de démarrage d'exécution ne recherche pas dans le Registre.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`startup`|Contient l'élément `<requiredRuntime>`.|  
  
## Notes  
 Les applications générées pour prendre en charge uniquement la version 1.0 du runtime doivent utiliser l'élément `<requiredRuntime>`.  Les applications créées à l'aide de la version 1.1 ou ultérieure de l'exécution doit utiliser l'élément `<supportedRuntime>`.  
  
> [!NOTE]
>  Si vous utilisez la fonction [CorBindToRuntimeByCfg](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) pour spécifier le fichier de configuration, vous devez employer l'élément `<requiredRuntime>` pour toutes les versions du runtime.  L'élément `<supportedRuntime>` est ignoré lorsque vous utilisez [CorBindToRuntimeByCfg](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
 La chaîne de l'attribut `version` doit correspondre au nom du dossier d'installation de la version spécifiée du .NET Framework.  Cette chaîne n'est pas interprétée.  Si le code de démarrage runtime ne trouve pas de dossier correspondant, le runtime n'est pas chargé ; le code de démarrage affiche un message d'erreur et s'interrompt.  
  
> [!NOTE]
>  Le code de démarrage d'une application hébergée dans Microsoft Internet Explorer ignore l'élément `<requiredRuntime>`.  
  
## Exemple  
 L'exemple suivant montre comment spécifier la version du Common Language Runtime dans un fichier de configuration.  
  
```  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres de démarrage](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<PaveOver\> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/fr-fr/c376208d-980d-42b4-865b-fbe0d9cc97c2)