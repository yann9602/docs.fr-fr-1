---
title: "&lt;assemblyIdentity&gt;, &#233;l&#233;ment de &lt;runtime&gt; | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<assemblyIdentity> (élément)"
  - "assemblyIdentity (élément)"
  - "balises conteneurs, <assemblyIdentity> (élément)"
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 17
---
# &lt;assemblyIdentity&gt;, &#233;l&#233;ment de &lt;runtime&gt;
Contient des informations d'identification sur l'assembly.  
  
## Syntaxe  
  
```  
  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`name`|Attribut requis.<br /><br /> Nom de l'assembly|  
|`culture`|Attribut facultatif.<br /><br /> Chaîne qui spécifie la langue et le pays ou la région de l'assembly.|  
|`publicKeyToken`|Attribut facultatif.<br /><br /> Valeur hexadécimale qui spécifie le nom fort de l'assembly.|  
|`processorArchitecture`|Attribut facultatif.<br /><br /> L'une des valeurs "x86", "amd64", "msil" ou "ia64" spécifiant l'architecture de processeur pour un assembly qui contient un code spécifique au processeur.  Les valeurs ne respectent pas la casse.  Si une autre valeur est assignée à l'attribut, l'élément `<assemblyIdentity>` entier est ignoré.  Consultez <xref:System.Reflection.ProcessorArchitecture>.|  
  
## processorArchitecture, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|`amd64`|Processeur AMD 64 bits uniquement.|  
|`ia64`|Processeur Intel 64 bits uniquement.|  
|`msil`|Neutre en ce qui concerne le processeur et les bits par mot|  
|`x86`|Processeur Intel 32 bits, natif ou dans l'environnement Windows on Windows \(WOW\) sur une plateforme 64 bits.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`assemblyBinding`|Contient des informations sur la redirection des versions des assemblys et sur l'emplacement de ces derniers.|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`dependentAssembly`|Encapsule la stratégie de liaisons et l'emplacement de chaque assembly.  Utilisez un élément `<dependentAssembly>` pour chaque assembly.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Chaque élément **\<dependentAssembly\>** doit avoir un élément enfant **\<assemblyIdentity\>**.  
  
 Si l'attribut `processorArchitecture` est présent, l'élément `<assemblyIdentity>` s'applique uniquement à l'assembly avec l'architecture de processeur correspondante.  Si l'attribut `processorArchitecture` n'est pas présent, l'élément `<assemblyIdentity>` peut s'appliquer à un assembly avec une architecture de processeur.  
  
 L'exemple suivant affiche un fichier de configuration pour deux assemblys de même nom qui ciblent deux architectures de processeur différentes, et dont les versions n'ont pas été maintenues de manière synchronisée.  Lorsque l'application est exécutée sur la plateforme x86, le premier élément `<assemblyIdentity>` s'applique et l'autre est ignoré.  Si l'application est exécutée sur une plateforme autre que x86 ou ia64, les deux éléments sont ignorés.  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"   
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"   
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"   
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Si un fichier de configuration contient un élément `<assemblyIdentity>` sans attribut `processorArchitecture` et s'il ne contient pas d'élément correspondant à la plateforme, l'élément sans l'attribut `processorArchitecture` est utilisé.  
  
## Exemple  
 L'exemple suivant montre comment fournir des informations sur un assembly.  
  
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
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Redirection des versions d'assemblys](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)