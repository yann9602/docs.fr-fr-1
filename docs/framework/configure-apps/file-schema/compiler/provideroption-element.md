---
title: "&lt;providerOption&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "provideroption"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<provideroption> (élément)"
  - "provideroption (élément)"
  - "providerOptions"
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
caps.latest.revision: 22
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 22
---
# &lt;providerOption&gt;, &#233;l&#233;ment
Spécifie les attributs de version du compilateur pour un fournisseur de langages.  
  
## Syntaxe  
  
```  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`name`|Attribut requis.<br /><br /> Spécifie le nom de l'option, par exemple, « CompilerVersion ».|  
|`value`|Attribut requis.<br /><br /> Spécifie la valeur de l'option, par exemple, « 3.5 ».|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration\>, élément](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Élément racine dans chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|[\<system.codedom\>, élément](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Spécifie des paramètres de configuration du compilateur pour les fournisseurs de langage disponibles.|  
|[\<compilers\>, élément](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Conteneur d'éléments de configuration de compilateur ; contient zéro, un ou plusieurs éléments `<compiler>`.|  
|[\<compiler\>, élément](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Spécifie les attributs de configuration du compilateur pour un fournisseur de langages.|  
  
## Notes  
 Dans le .NET Framework version 3.5, les fournisseurs de code CodeDOM \(Code Document Object Model\) peuvent prendre en charge des options spécifiques au fournisseur grâce à l'élément `<providerOption>`.  
  
 Le .NET Framework 3.5 inclut des assemblys .NET Framework 2.0 mis à jour et fournit des assemblys 3.5 qui contiennent de nouveaux types.  Les fournisseurs de code Microsoft C\# et Visual Basic sont contenus dans les assemblys .NET Framework 2.0, mais ils ont été mis à jour pour prendre en charge les compilateurs de la version 3.5.  Par défaut, les fournisseurs de code mis à jour génèrent le code pour les compilateurs de la version 2.0.  Vous pouvez utiliser l'élément `<providerOption>` pour modifier la version de compilateur cible en 3.5.  Pour cela, spécifiez "CompilerVersion" pour l'attribut `name` et "v3.5" pour l'attribut `value`.  Vous devez faire précéder le numéro de version d'un « v » en minuscule.  
  
 Vous pouvez généraliser la spécification de version en ajoutant l'élément `<providerOption>` au fichier Machine.config ou Web.config racine du .NET Framework 2.0.  Si vous mettez à jour la version du compilateur par défaut vers 3.5 dans le fichier Machine.config, vous pouvez revenir à la version 2.0 pour chacune des applications en faisant appel à l'élément `<providerOption>` dans le fichier de configuration de l'application.  
  
 Les implémenteurs de fournisseur de code CodeDOM peuvent traiter des options personnalisées en proposant un constructeur qui accepte un paramètre `providerOptions` de type <xref:System.Collections.Generic.IDictionary%602>.  
  
## Exemple  
 L'exemple suivant montre comment spécifier que la version 3.5 du fournisseur de code C\# doit être utilisée.  
  
```  
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
  
## Voir aussi  
 <xref:System.CodeDom.Compiler.CompilerInfo>   
 <xref:System.CodeDom.Compiler.CodeDomProvider>   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<compilers\>, élément](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)   
 [Spécification des noms de types qualifiés complets](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)   
 [compiler, élément de compilers pour compilation \(Schéma des paramètres ASP.NET\)](http://msdn.microsoft.com/fr-fr/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)