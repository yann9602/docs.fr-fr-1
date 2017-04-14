---
title: "&lt;codeBase&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<codeBase> (élément)"
  - "codeBase (élément)"
  - "balises conteneurs, <codeBase> (élément)"
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# &lt;codeBase&gt;, &#233;l&#233;ment
Spécifie où le Common Language Runtime peut trouver un assembly.  
  
## Syntaxe  
  
```  
  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`href`|Attribut requis.<br /><br /> Spécifie l'URL où le runtime peut trouver la version spécifiée de l'assembly.|  
|`version`|Attribut requis.<br /><br /> Spécifie la version de l'assembly à laquelle le paramètre codebase s'applique.  Un numéro de version d'assembly suit le format *major.minor.build.revision*.|  
  
## version, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Les valeurs valides pour chaque partie du numéro de version vont de 0 à 65535.|Non applicable.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`buildproviders`|Définit une collection de fournisseurs de générations utilisés pour compiler des fichiers de ressources personnalisés.  Vous pouvez avoir n'importe quel nombre de fournisseurs de générations.|  
|`compilation`|Configure tous les paramètres de compilation utilisés par ASP.NET.|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`System.web`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
  
## Notes  
 Pour que le runtime utilise le paramètre **\<codeBase\>** dans un fichier de configuration de l'ordinateur ou de stratégie de l'éditeur, ce fichier doit également rediriger la version d'assembly.  Les fichiers de configuration des applications peuvent contenir un paramètre codebase sans rediriger la version d'assembly.  Après avoir déterminé quelle version d'assembly il doit utiliser, le runtime applique le paramètre codebase du fichier qui détermine la version.  Si aucun paramètre codebase n'est indiqué, le runtime détecte l'assembly de la manière habituelle.  
  
 Si l'assembly a un nom fort, le paramètre codebase peut se trouver n'importe où sur l'intranet local ou sur Internet.  Si l'assembly est privé, le paramètre codebase doit se trouver dans un chemin d'accès relatif par rapport au répertoire de l'application.  
  
 Pour des assemblys sans nom fort, la version est ignorée et le chargeur utilise la première occurrence de \<codebase\> dans \<dependentAssembly\>.  S'il existe une entrée dans le fichier de configuration de l'application qui redirige la liaison à un autre assembly, la redirection est prioritaire même si la version de l'assembly ne correspond pas à la demande de liaison.  
  
## Exemple  
 L'exemple suivant montre comment indiquer au runtime l'emplacement d'un assembly.  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Spécification de l'emplacement d'un assembly](../../../../../docs/framework/configure-apps/specify-assembly-location.md)   
 [Méthode de localisation des assemblys par le runtime](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)