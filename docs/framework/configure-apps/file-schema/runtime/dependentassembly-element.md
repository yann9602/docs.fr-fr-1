---
title: "&lt;dependentAssembly&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<dependentAssembly> (élément)"
  - "balises conteneurs, <dependentAssembly> (élément)"
  - "dependentAssembly (élément)"
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# &lt;dependentAssembly&gt;, &#233;l&#233;ment
Encapsule la stratégie de liaisons et l'emplacement de chaque assembly.  Utilisez un élément `dependentAssembly` pour chaque assembly.  
  
## Syntaxe  
  
```  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|`assemblyIdentity`|Contient des informations d'identification sur l'assembly.  Cet élément doit être inclus dans chaque élément `dependentAssembly`.|  
|`codeBase`|Spécifie l'endroit où le runtime peut trouver un assembly partagé s'il n'est pas installé sur l'ordinateur.|  
|`bindingRedirect`|Redirige une version d'assembly vers une autre.|  
|`publisherPolicy`|Spécifie si le runtime applique la stratégie de l'éditeur pour cet assembly.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`assemblyBinding`|Contient des informations sur la redirection des versions des assemblys et sur l'emplacement de ces derniers.|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Exemple  
 L'exemple suivant montre comment encapsuler des informations sur deux assemblys.  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Redirection des versions d'assemblys](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)