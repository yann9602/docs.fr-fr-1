---
title: "&lt;codeBase&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 272a4262295b5dd67414dd0ef6523f90b2125836
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcodebasegt-element"></a>&lt;codeBase&gt; élément
Spécifie où le common language runtime peut trouver un assembly.  
  
 \<configuration>  
\<runtime >  
\<assemblyBinding >  
\<dependentAssembly >  
\<codeBase >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`href`|Attribut requis.<br /><br /> Spécifie l’URL où le runtime peut trouver la version spécifiée de l’assembly.|  
|`version`|Attribut requis.<br /><br /> Spécifie la version de l’assembly d’à que la base de code s’applique. Le format du numéro de version est *major.minor.build.revision*.|  
  
## <a name="version-attribute"></a>Attribut de version  
  
|Value|Description|  
|-----------|-----------------|  
|Les valeurs valides pour chaque partie du numéro de version sont compris entre 0 et 65535.|Non applicable.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`buildproviders`|Définit une collection de fournisseurs de générations utilisés pour compiler des fichiers de ressources personnalisés. Le nombre de fournisseurs de générations n'est pas défini.|  
|`compilation`|Configure tous les paramètres de compilation ASP.NET utilise.|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`System.web`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
  
## <a name="remarks"></a>Notes  
 Le runtime doit utiliser le  **\<codeBase >** défini dans un fichier de configuration machine ou d’un fichier de stratégie d’éditeur, le fichier doit également rediriger la version d’assembly. Fichiers de configuration d’application peuvent avoir un paramètre codebase sans rediriger la version d’assembly. Après avoir déterminé la version de l’assembly à utiliser, le runtime applique le paramètre de la base de code à partir du fichier qui détermine la version. Si aucun code de base n’est indiquée, le runtime détecte l’assembly de manière habituelle.  
  
 Si l’assembly a un nom fort, le paramètre codebase peut être n’importe où sur l’intranet local ou sur Internet. Si l’assembly est un assembly privé, le paramètre codebase doit être un chemin d’accès relatif au répertoire de l’application.  
  
 Pour les assemblys sans nom fort, la version est ignorée et le chargeur utilise la première occurrence de \<codebase > à l’intérieur de \<dependentAssembly >. Si une entrée existe dans le fichier de configuration d’application qui redirige la liaison à un autre assembly, la redirection est prioritaire même si la version d’assembly ne correspond pas à la demande de liaison.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier où le runtime peut trouver un assembly.  
  
```xml  
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
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Spécification de l'emplacement d'un assembly](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [Méthode de localisation des assemblys par le runtime](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
