---
title: "&lt;probing&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#probing"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<probing> (élément)"
  - "balises conteneurs, <probing> (élément)"
  - "probing (élément)"
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# &lt;probing&gt;, &#233;l&#233;ment
Spécifie les sous\-répertoires de base de l'application dans lesquels le Common Language Runtime effectue sa recherche lorsqu'il charge les assemblys.  
  
## Syntaxe  
  
```  
<probing privatePath="paths"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`privatePath`|Attribut requis.<br /><br /> Spécifie les sous\-répertoires du répertoire de base de l'application susceptible de contenir des assemblys.  Séparez les différents sous\-répertoires par des points\-virgules.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`assemblyBinding`|Contient des informations sur la redirection des versions des assemblys et sur l'emplacement de ces derniers.|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Exemple  
 L'exemple suivant montre comment spécifier les sous\-répertoires de base de l'application dans lesquels le runtime devra rechercher les assemblys.  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Spécification de l'emplacement d'un assembly](../../../../../docs/framework/configure-apps/specify-assembly-location.md)   
 [Méthode de localisation des assemblys par le runtime](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)