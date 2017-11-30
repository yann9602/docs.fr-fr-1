---
title: "&lt;assemblyBinding&gt; , élément pour &lt;runtime&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fdf2bc90c496c9906b5d31bad0065e01bdb47942
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltassemblybindinggt-element-for-ltruntimegt"></a>&lt;assemblyBinding&gt; , élément pour &lt;runtime&gt;
Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.  
  
 \<configuration>  
\<runtime >  
\<assemblyBinding >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
      <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**xmlns**|Attribut requis.<br /><br /> Spécifie l'espace de noms XML requis pour la liaison d'assembly. Utilisez la chaîne « urn:schemas-microsoft-com:asm.v1 » comme valeur.|  
|**appliesTo**|Spécifie la version du runtime à laquelle s'applique la redirection d'assembly .NET Framework. Cet attribut facultatif utilise un numéro de version .NET Framework pour indiquer la version à laquelle il s'applique. Si l’attribut **appliesTo** n’est pas spécifié, l’élément **\<assemblyBinding>** s’applique à toutes les versions du .NET Framework. Le **appliesTo** attribut a été introduit dans .NET Framework version 1.1 ; il est ignoré par le .NET Framework version 1.0. Cela signifie que tous les éléments **\<assemblyBinding>** sont appliqués lors de l’utilisation du .NET Framework 1.0, même si un attribut **appliesTo** est spécifié.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<dependentAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|Encapsule la stratégie de liaison et l’emplacement d’un assembly. Utilisez une  **\<dependentAssembly >** balise pour chaque assembly.|  
|[\<probing>](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|Spécifie les sous-répertoires interrogés par le Common Language Runtime lors du chargement des assemblys.|  
|[\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|Spécifie si le runtime applique la stratégie de l'éditeur.|  
|[\<qualifyAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|Spécifie le nom complet de l'assembly qui doit être chargé dynamiquement quand un nom partiel est utilisé.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment rediriger une version d'assembly vers une autre et fournir une base de code.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 L’exemple suivant montre comment utiliser le **appliesTo** attribut pour rediriger la liaison d’un assembly .NET Framework.  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>   
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Redirection des versions d'assemblys](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
