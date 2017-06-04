---
title: "&lt;assemblyBinding&gt;, &#233;l&#233;ment de &lt;configuration&gt; | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<assemblyBinding> (élément)"
  - "assemblyBinding (élément)"
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# &lt;assemblyBinding&gt;, &#233;l&#233;ment de &lt;configuration&gt;
Spécifie la stratégie de liaison de l'assembly au niveau de la configuration.  
  
## Syntaxe  
  
```  
<assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1">  
</assemblyBinding>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`xmlns`|Attribut requis.<br /><br /> Spécifie l'espace de noms XML requis pour les liaisons d'assembly.  Utilisez la chaîne "urn:schemas\-microsoft\-com:asm.v1" comme valeur.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<linkedConfiguration\> \(élément\)](../../../../docs/framework/configure-apps/file-schema/linkedconfiguration-element.md)|Spécifie un fichier de configuration à inclure.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration\>, élément](../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## Notes  
 [\<linkedConfiguration\> \(élément\)](../../../../docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) simplifie la gestion des assemblys de composant en permettant aux fichiers de configuration de l'application d'inclure des fichiers de configuration d'assembly dans des emplacements connus, plutôt qu'en dupliquant des paramètres de configuration d'assembly.  
  
> [!NOTE]
>  L'élément `<linkedConfiguration>` n'est pas pris en charge pour les applications avec des manifestes côte à côte Windows.  
  
## Exemple  
 L'exemple de code suivant indique comment inclure un fichier de configuration sur le disque dur local.  
  
```  
<configuration>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
      <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>  
   </assemblyBinding>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des fichiers de configuration](../../../../docs/framework/configure-apps/file-schema/index.md)