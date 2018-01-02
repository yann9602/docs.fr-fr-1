---
title: "&lt;compilateur&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2ef50301a5188193cc13cd0e657f53593ef0d93e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcompilergt-element"></a>&lt;compilateur&gt; élément
Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.  
  
 \<Élément de configuration >  
\<System.CodeDom (élément) >  
\<compilateurs élément >  
\<compilateur > élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`compilerOptions`|Attribut facultatif.<br /><br /> Spécifie des arguments supplémentaires spécifiques au compilateur pour la compilation. Les valeurs pour le `compilerOptions` attribut sont généralement répertoriées dans une rubrique d’options du compilateur pour le compilateur. Dans la documentation de Visual Studio 2005, vous pouvez localiser les options du compilateur en recherchant « options du compilateur » dans l’index.|  
|`extension`|Attribut requis.<br /><br /> Fournit une liste délimitée par des points-virgules des extensions de nom de fichier utilisé par les fichiers sources pour le fournisseur de langage. Par exemple, « .cs ».|  
|`language`|Attribut requis.<br /><br /> Fournit une liste délimitée par des points-virgules de noms de langages pris en charge par le fournisseur de langage. Par exemple, « c# ; cs ; csharp ».|  
|`type`|Attribut requis.<br /><br /> Spécifie le nom de type du fournisseur de langage, y compris le nom de l’assembly contenant l’implémentation du fournisseur. Le nom de type doit respecter les exigences définies dans [en spécifiant des noms de types qualifiés complets](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`warningLevel`|Attribut facultatif.<br /><br /> Spécifie le niveau d’avertissement du compilateur par défaut ; Détermine le niveau auquel le fournisseur de langage traite les avertissements de compilation comme des erreurs.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<providerOption > élément](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|Spécifie les attributs de version du compilateur pour un fournisseur de langage.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>, élément](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|[\<System.CodeDom > élément](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.|  
|[\<compilateurs > élément](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Conteneur pour les éléments de configuration du compilateur ; contient zéro ou plusieurs `<compiler>` éléments.|  
  
## <a name="remarks"></a>Notes  
 Chaque `<compiler>` élément spécifie les attributs de configuration du compilateur pour un fournisseur de langage spécifique. Le fournisseur étend la <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> classe pour une langue spécifique ; la `<compiler>` élément définit les paramètres de générateur de code pour le fournisseur de langage et le compilateur.  
  
 Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l’ordinateur (Machine.config). Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider>. Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.  
  
 Éléments du compilateur dans l’application ou le fichier de configuration Web peuvent compléter ou remplacer les paramètres dans le fichier de configuration machine. Si plusieurs implémentations de fournisseur sont configurée pour le même nom de la langue ou la même extension de fichier, la dernière configuration correspondante remplace tous les fournisseurs configurés précédentes pour cette extension de fichier ou le nom de langue.  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration machine et le fichier de configuration d’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre un élément de configuration du compilateur classique.  
  
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
        warningLevel="1" />  
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
 [compilateur, élément pour les compilateurs pour compilation (schéma des paramètres ASP.NET)](http://msdn.microsoft.com/en-us/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
