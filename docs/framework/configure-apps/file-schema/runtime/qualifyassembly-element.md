---
title: "&lt;qualifyAssembly&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<qualifyAssembly> (élément)"
  - "balises conteneurs, <qualifyAssembly> (élément)"
  - "qualifyAssembly (élément)"
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# &lt;qualifyAssembly&gt;, &#233;l&#233;ment
Spécifie le nom complet de l'assembly qui doit être chargé dynamiquement lorsqu'un nom partiel est utilisé.  
  
## Syntaxe  
  
```  
  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`partialName`|Attribut requis.<br /><br /> Spécifie le nom partiel de l'assembly tel qu'il s'affiche dans le code.|  
|`fullName`|Attribut requis.<br /><br /> Spécifie le nom complet de l'assembly tel qu'il s'affiche dans le Global Assembly Cache.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`assemblyBinding`|Contient des informations sur la redirection des versions des assemblys et sur l'emplacement de ces derniers.|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 L'appel de la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> à l'aide des noms d'assemblys partiels force le Common Language Runtime à rechercher l'assembly uniquement dans le répertoire de base de l'application.  Utilisez l'élément **\<qualifyAssembly\>** dans le fichier de configuration de votre application pour fournir les informations d'assembly complètes \(nom, version, jeton de clé publique et culture\) et forcer le Common Language Runtime à rechercher l'assembly dans le Global Assembly Cache.  
  
 L'attribut **fullName** doit inclure les quatre champs d'identité d'un assembly : nom, version, jeton de clé publique et culture.  L'attribut **partialName** doit faire partiellement référence à un assembly.  Vous devez spécifier au moins le nom de l'assembly \(cas le plus courant\), mais vous pouvez également inclure la version, le jeton de clé publique ou la culture \(ou n'importe quelle association des quatre, mais pas les quatre à la fois\).  L'attribut **partialName** doit correspondre au nom spécifié dans votre appel.  Par exemple, vous ne pouvez pas spécifier `"math"` comme attribut **partialName** dans votre fichier de configuration et appeler `Assembly.Load("math, Version=3.3.3.3")` dans votre code.  
  
## Exemple  
 L'exemple suivant transforme logiquement l'appel `Assembly.Load("math")` en `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Méthode de localisation des assemblys par le runtime](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [NIB: Partial Assembly References](http://msdn.microsoft.com/fr-fr/ec90f07a-398c-4306-9401-0fc5ff9cb59f)