---
title: "/doc (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "FileProperties.BuildAction"
  - "/doc"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "comments, C# code"
  - "XML documentation [C#], comments in source files"
  - "doc compiler option [C#]"
  - "Visual C#, XML documentation for"
  - "-doc compiler option [C#]"
  - "/doc compiler option [C#]"
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# /doc (C# Compiler Options)
L'option **\/doc** vous permet de placer des commentaires de documentation dans un fichier XML.  
  
## Syntaxe  
  
```  
/doc:file  
```  
  
## Arguments  
 `file`  
 Fichier de sortie XML contenant les commentaires extraits des fichiers de code source de la compilation.  
  
## Notes  
 Dans les fichiers de code source, les commentaires de documentation qui précèdent les éléments suivants peuvent être traités et ajoutés au fichier XML :  
  
-   Des types définis par l'utilisateur, tels qu'une [classe](../../../csharp/language-reference/keywords/class.md), un [délégué](../../../csharp/language-reference/keywords/delegate.md) ou une [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   Des membres, tels qu'un champ, un [événement](../../../csharp/language-reference/keywords/event.md), une [propriété](../../../csharp/programming-guide/classes-and-structs/using-properties.md) ou une méthode  
  
 Le fichier de code source qui contient Main est traité en premier pour être placé dans le fichier XML.  
  
 Pour utiliser le fichier .xml généré avec la fonctionnalité [IntelliSense](/visual-studio/ide/using-intellisense), donnez au fichier .xml le même nom de fichier que celui de l'assembly que vous voulez prendre en charge et assurez\-vous qu'il se trouve dans le même répertoire que l'assembly.  De cette manière, lorsque l'assembly est référencé dans le projet Visual Studio, le fichier .xml est trouvé aussi.  Pour plus d'informations, consultez [Insertion de commentaires dans le code](/visual-studio/ide/supplying-xml-code-comments).  
  
 Sauf si vous compilez avec [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` contiendra les balises \<assembly\>\<\/assembly\> spécifiant le nom du fichier contenant le manifeste d'assembly pour le fichier de sortie de la compilation.  
  
> [!NOTE]
>  L'option \/doc s'applique à tous les fichiers d'entrée ; ou, si elle est définie dans Paramètres du projet, à tous les fichiers du projet.  Pour désactiver les avertissements relatifs aux commentaires de documentation pour un fichier spécifique ou une section de code, utilisez [\#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).  
  
 Pour découvrir des méthodes de génération de documentation à partir de commentaires contenus dans votre code, consultez [Balises recommandées pour commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md).  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur l'onglet **Générer**.  
  
3.  Modifiez la propriété **Fichier de documentation XML**.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)