---
title: "&lt;developmentMode&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<developmentMode> (élément)"
  - "balises conteneurs, <developmentMode> (élément)"
  - "developmentMode (élément)"
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# &lt;developmentMode&gt;, &#233;l&#233;ment
Spécifie si le runtime recherche les assemblys dans les répertoires spécifiés par la variable d'environnement DEVPATH.  
  
## Syntaxe  
  
```  
<developmentMode developerInstallation="true | false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**developerInstallation**|Spécifie si le runtime recherche les assemblys dans les répertoires spécifiés par la variable d'environnement DEVPATH.|  
  
## developerInstallation, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|**true**|Recherche les assemblys dans les répertoires spécifiés par la variable d'environnement DEVPATH.|  
|**false**|Ne recherche pas les assemblys dans les répertoires spécifiés par la variable d'environnement DEVPATH.  Il s'agit de la valeur par défaut.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Utilisez ce paramètre au moment du développement uniquement.  Le runtime ne vérifie pas les versions des assemblys avec nom fort qui se trouvent dans DEVPATH.  Il utilise simplement le premier assembly qu'il trouve.  
  
## Exemple  
 L'exemple suivant montre comment faire en sorte que le runtime recherche les assemblys dans les répertoires spécifiés par la variable d'environnement DEVPATH.  
  
```  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Comment : localiser des assemblys à l'aide de DEVPATH](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)