---
title: "&lt;linkedConfiguration&gt; (&#233;l&#233;ment) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<linkedConfiguration> (élément)"
  - "fichiers de configuration (.NET Framework), fichiers de configuration liés"
  - "inclure des fichiers de configuration"
  - "fichiers de configuration liés"
  - "linkedConfiguration (élément)"
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# &lt;linkedConfiguration&gt; (&#233;l&#233;ment)
Spécifie un fichier de configuration à inclure.  
  
## Syntaxe  
  
```  
<linkedConfiguration  
   href="URL of linked configuration file"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`href`|URL du fichier de configuration à inclure.  Le seul format pris en charge pour l'attribut `href` est « file:\/\/ ».  Les fichiers locaux et les fichiers UNC sont pris en charge.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<assemblyBinding\> \(élément\)](../../../../docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)|Spécifie la stratégie de liaison de l'assembly au niveau de la configuration.|  
  
## Notes  
 L'élément `<linkedConfiguration>` simplifie la maintenance pour les assemblys de composants.  Si une ou plusieurs applications utilisent un assembly disposant d'un fichier de configuration qui réside dans un emplacement connu, les fichiers de configuration des applications qui utilisent l'assembly peuvent utiliser l'élément `<linkedConfiguration>` pour inclure le fichier de configuration d'assembly, plutôt qu'inclure les informations de configuration directement.  Lorsque l'assembly de composant est traité, la mise à jour du fichier de configuration commun fournit des informations de configuration mises à jour à toutes les applications qui utilisent l'assembly.  
  
> [!NOTE]
>  L'élément `<linkedConfiguration>` n'est pas pris en charge pour les applications avec des manifestes côte à côte Windows.  
  
 Les règles suivantes déterminent l'utilisation de fichiers de configuration liés.  
  
-   Les paramètres des fichiers de configuration inclus affectent uniquement la stratégie de liaison du chargeur et sont utilisés uniquement par le chargeur.  Les fichiers de configuration inclus peuvent disposer de paramètres autres que les stratégies de liaison, mais ces paramètres n'ont aucun effet.  
  
-   Le seul format pris en charge pour l'attribut `href` est « file:\/\/ ».  Les fichiers locaux et les fichiers UNC sont pris en charge.  
  
-   Il n'existe aucune contrainte quant au nombre de configurations liées par fichier de configuration.  
  
-   Tous les fichiers de configuration liés sont fusionnés pour former un fichier, semblable au comportement de la directive `#include` en C\/C\+\+.  
  
-   L'élément `<linkedConfiguration>` est autorisé uniquement dans les fichiers de configuration de l'application ; il est ignoré dans Machine.config.  
  
-   Les références circulaires sont détectées et arrêtées.  Autrement dit, si les éléments `<linkedConfiguration>` d'une série de fichiers de configuration forment une boucle, la boucle est détectée et arrêtée.  
  
## Exemple  
 L'exemple de code suivant indique comment inclure un fichier de configuration à partir du disque dur local.  
  
```  
<configuration>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
      <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>  
   </assemblyBinding>  
</configuration>  
```  
  
## Voir aussi  
 [\<assemblyBinding\> \(élément\)](../../../../docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
 [Schéma des fichiers de configuration](../../../../docs/framework/configure-apps/file-schema/index.md)