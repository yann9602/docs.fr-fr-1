---
title: "&lt;providerOption&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
caps.latest.revision: "22"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f28b7b43f2f782744a0dbc81bd0b91bbbcd8abba
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ltprovideroptiongt-element"></a>&lt;providerOption&gt; élément
Spécifie les attributs de version du compilateur pour un fournisseur de langage.  
  
 \<Élément de configuration >  
\<System.CodeDom (élément) >  
\<compilateurs élément >  
\<compilateur > élément  
\<providerOption > élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Attribut requis.<br /><br /> Spécifie le nom de l’option ; par exemple, « CompilerVersion ».|  
|`value`|Attribut requis.<br /><br /> Spécifie la valeur de l’option ; par exemple, « v3.5 ».|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>, élément](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Élément racine dans chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|[\<system.codedom> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.|  
|[\<compilateurs > élément](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Conteneur pour les éléments de configuration du compilateur ; contient zéro ou plusieurs `<compiler>` éléments.|  
|[\<compiler> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.|  
  
## <a name="remarks"></a>Notes  
 Dans le .NET Framework version 3.5, les fournisseurs de code Code Document Object Model (CodeDOM) peuvent prendre en charge les options spécifiques au fournisseur à l’aide de la `<providerOption>` élément.  
  
 Le .NET Framework 3.5 inclut des assemblys mis à jour de .NET Framework 2.0 et fournit des assemblys 3.5 qui contiennent de nouveaux types. Les fournisseurs de code Microsoft c# et Visual Basic sont contenus dans des assemblys .NET Framework 2.0, mais ont été mis à jour pour prendre en charge les compilateurs de la version 3.5. Par défaut, les fournisseurs de code mis à jour génèrent du code pour les compilateurs de la version 2.0. Vous pouvez utiliser la `<providerOption>` élément pour modifier la version de compilateur cible en 3.5. Pour ce faire, spécifiez « CompilerVersion » pour le `name` attribut et « v3.5 » pour le `value` attribut. Vous devez faire précéder le numéro de version avec un « v » en minuscules.  
  
 Vous pouvez rendre la spécification de version global en ajoutant la `<providerOption>` élément vers le fichier Machine.config de .NET Framework 2.0 ou le fichier Web.config racine. Si vous mettez à jour la version du compilateur par défaut à 3.5 dans le fichier Machine.config, vous pouvez le modifier à 2.0 sur chaque application à l’aide de la `<providerOption>` élément dans le fichier de configuration d’application.  
  
 Les implémenteurs de fournisseur de code codeDOM peuvent traiter des options personnalisées en fournissant un constructeur qui accepte un `providerOptions` paramètre de type <xref:System.Collections.Generic.IDictionary%602>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier la version 3.5 du fournisseur de code c# doit être utilisée.  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<compilateurs > élément](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [Spécification des noms de types complets](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [compilateur, élément pour les compilateurs pour compilation (schéma des paramètres ASP.NET)](http://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
