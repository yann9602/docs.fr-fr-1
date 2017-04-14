---
title: "&lt;compiler&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<compiler> (élément)"
  - "attributs de configuration du compilateur"
  - "éléments de configuration du compilateur, <compiler> (élément)"
  - "compiler (élément)"
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
caps.latest.revision: 20
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 20
---
# &lt;compiler&gt;, &#233;l&#233;ment
Spécifie les attributs de configuration du compilateur pour un fournisseur de langages.  
  
## Syntaxe  
  
```  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`compilerOptions`|Attribut facultatif.<br /><br /> Spécifie des arguments supplémentaires, spécifiques au compilateur, pour la compilation.  Les valeurs de l'attribut `compilerOptions` sont généralement répertoriées dans une rubrique d'options du compilateur.  Dans la documentation Visual Studio 2005, vous pouvez localiser les options du compilateur en recherchant « options du compilateur » dans l'index.|  
|`extension`|Attribut requis.<br /><br /> Propose une liste séparée par des points\-virgules des extensions de nom de fichier utilisées par les fichiers source pour le fournisseur de langage.  Par exemple, « .cs ».|  
|`language`|Attribut requis.<br /><br /> Fournit une liste délimitée par des points\-virgules de noms de langages pris en charge par le fournisseur de langage.  Par exemple, « c\#;cs;csharp ».|  
|`type`|Attribut requis.<br /><br /> Spécifie le nom complet du type du fournisseur de langage, en incluant le nom de l'assembly qui contient l'implémentation du fournisseur.  Le nom du type doit répondre aux conditions requises définies dans [Spécification des noms de types qualifiés complets](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`warningLevel`|Attribut facultatif.<br /><br /> Spécifie le niveau d'avertissement de compilateur par défaut ; détermine le niveau auquel le fournisseur de langages traite les avertissements de compilation comme des erreurs.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<providerOption\>, élément](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|Spécifie les attributs de version du compilateur pour un fournisseur de langages.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration\>, élément](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|[\<system.codedom\>, élément](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Spécifie des paramètres de configuration du compilateur pour les fournisseurs de langage disponibles.|  
|[\<compilers\>, élément](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Conteneur d'éléments de configuration de compilateur ; contient zéro, un ou plusieurs éléments `<compiler>`.|  
  
## Notes  
 Chaque élément `<compiler>` spécifie les attributs de la configuration du compilateur pour un fournisseur de langages spécifique.  Le fournisseur étend la classe <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=fullName> pour un langage spécifique ; l'élément `<compiler>` définit les paramètres du compilateur et du générateur de code pour le fournisseur du langage.  
  
 Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l'ordinateur \(Machine.config\).  Les développeurs et fournisseurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation de <xref:System.CodeDom.Compiler.CodeDomProvider>.  Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=fullName> pour énumérer par programme le fournisseur de langages et les paramètres de configuration du compilateur sur un ordinateur.  
  
 Des éléments de compilateur présents dans l'application ou le fichier de configuration Web peuvent remplacer les paramètres du fichier de configuration de l'ordinateur ou s'y ajouter.  Si plusieurs implémentations de fournisseur sont configurées pour le même nom de langage ou la même extension de fichier, la dernière configuration correspondante remplace tous les fournisseurs déjà configurés pour ce nom de langage ou cette extension de fichier.  
  
## Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'ordinateur et dans le fichier de configuration de l'application.  
  
## Exemple  
 L'exemple suivant illustre un élément de configuration de compilateur classique :  
  
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
        warningLevel="1" />  
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