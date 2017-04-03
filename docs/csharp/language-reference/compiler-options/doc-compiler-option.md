---
title: -doc (Options du compilateur C#) | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- FileProperties.BuildAction
- /doc
dev_langs:
- CSharp
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8addbbfe1e854feee560192292b713da4fc67e6c
ms.lasthandoff: 03/13/2017

---
# <a name="doc-c-compiler-options"></a>/doc (Options du compilateur C#)
L’option **/doc** vous permet de placer des commentaires de documentation dans un fichier XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/doc:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Fichier de sortie XML, qui est rempli avec les commentaires des fichiers de code source de la compilation.  
  
## <a name="remarks"></a>Remarques  
 Dans les fichiers de code source, les commentaires de documentation qui précèdent les éléments suivants peuvent être traités et ajoutés au fichier XML :  
  
-   Types définis par l’utilisateur, tels qu’une [classe](../../../csharp/language-reference/keywords/class.md), un [délégué](../../../csharp/language-reference/keywords/delegate.md) ou une [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   Membres tels qu’un champ, un [événement](../../../csharp/language-reference/keywords/event.md), une [propriété](../../../csharp/programming-guide/classes-and-structs/using-properties.md) ou une méthode  
  
 Le fichier de code source qui contient Main est sorti en premier dans le document XML.  
  
 Pour utiliser le fichier .xml généré avec la fonctionnalité [IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense), faites en sorte que le nom du fichier .xml soit identique à l’assembly que vous souhaitez prendre en charge, puis vérifiez que le fichier .xml est dans le même répertoire que l’assembly. Ainsi, quand l’assembly est référencé dans le projet Visual Studio, le fichier .xml est également trouvé. Pour plus d’informations, consultez [Insertion de commentaires dans le code XML](https://docs.microsoft.com/visualstudio/ide/supplying-xml-code-comments).  
  
 Sauf si vous compilez avec [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` contiendra des balises \<assembly>\</assembly> spécifiant le nom du fichier qui contient le manifeste d’assembly pour le fichier de sortie de la compilation.  
  
> [!NOTE]
>  L’option /doc s’applique à tous les fichiers d’entrée ou, si elle est définie dans les paramètres de projet, à tous les fichiers du projet. Pour désactiver les avertissements relatifs aux commentaires de documentation pour un fichier ou une section de code spécifique, utilisez [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).  
  
 Pour découvrir comment générer de la documentation à partir de commentaires dans votre code, consultez [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur l’onglet **Générer**.  
  
3.  Modifiez la propriété **Fichier de documentation XML**.  
  
 Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB Guide pratique pour modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
