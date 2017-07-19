---
title: "Sp&#233;cification de l&#39;emplacement d&#39;un assembly | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "configuration d'applications (.NET Framework)"
  - "assemblys (.NET Framework), spécifier l'emplacement"
  - "configuration (.NET Framework), applications"
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# Sp&#233;cification de l&#39;emplacement d&#39;un assembly
L'emplacement d'un assembly peut être spécifié de deux manières :  
  
-   Utilisation de l'élément [\<codeBase\>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md).  
  
-   Utilisation de l'élément [\<probing\>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md).  
  
 Vous pouvez également utiliser [outil .NET Framework Configuration \(Mscorcfg.msc\)](http://msdn.microsoft.com/fr-fr/a7106c52-68da-490e-b129-971b2c743764) pour spécifier les emplacements des assemblys ou pour indiquer au Common Language Runtime les emplacements à utiliser pour la détection des assemblys.  
  
## Utilisation de l'élément \<codeBase\> .  
 L'élément **\<codeBase\>** ne peut être employé que dans les fichiers de configuration machine ou de stratégie d'éditeur qui redirigent également la version d'assembly.  Lorsque le runtime détermine la version d'assembly à utiliser, il utilise le paramètre de base de code du fichier qui définit la version.  Si aucune base de code n'est indiquée, le runtime recherche l'assembly normalement.  Pour plus d'informations, consultez [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 L'exemple suivant montre comment spécifier l'emplacement d'un assembly.  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 L'attribut **version** est requis pour tous les assemblys portant un nom fort, mais doit être évité pour les autres assemblys.  L'élément **\<codeBase\>** nécessite l'attribut **href**.  Il n'est pas possible de spécifier de plages de versions dans l'élément **\<codeBase\>**.  
  
> [!NOTE]
>  Si vous indiquez des préférences de base de code pour un assembly qui ne porte pas un nom fort, il est impératif de pointer vers la base de l'application ou vers un sous\-répertoire du répertoire de base de l'application.  
  
## Utilisation de l'élément \<probing\>.  
 Le runtime localise les assemblys qui ne comportent pas de base de code au moyen d'une procédure de détection.  Pour de plus amples informations sur la détection, consultez [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Vous pouvez utiliser l'élément [\<probing\>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) dans le fichier de configuration de l'application pour spécifier les sous\-répertoires dans lesquels le runtime doit rechercher les assemblys.  L'exemple suivant montre comment indiquer au runtime les répertoires dans lesquels effectuer sa recherche.  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 L'attribut **privatePath** contient les répertoires dans lesquels le runtime doit rechercher les assemblys.  Si l'application est située dans le répertoire C:\\Program Files\\MyApp, le runtime recherchera les assemblys ne spécifiant pas de base de code dans C:\\Program Files\\MyApp\\Bin, C:\\Program Files\\MyApp\\Bin2\\Subbin et C:\\Program Files\\MyApp\\Bin3.  Les répertoires spécifiés dans **privatePath** doivent être des sous\-répertoires du répertoire de base de l'application.  
  
## Voir aussi  
 [Assemblys dans le Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)   
 [Programmation à l'aide d'assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)   
 [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [Configuring .NET Framework Apps](http://msdn.microsoft.com/fr-fr/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)