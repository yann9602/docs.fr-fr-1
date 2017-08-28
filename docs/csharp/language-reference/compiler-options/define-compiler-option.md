---
title: -define (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /define
dev_langs:
- CSharp
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
caps.latest.revision: 21
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: dbe5532114864d9f76c6d9e19b669c46489709b2
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="define-c-compiler-options"></a>/define (Options du compilateur C#)
L’option **/define** définit `name` comme un symbole dans tous les fichiers de code source de votre programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/define:name[;name2]  
```  
  
## <a name="arguments"></a>Arguments  
 `name`, `name2`  
 Nom de chaque symbole que vous souhaitez définir.  
  
## <a name="remarks"></a>Remarques  
 L’option **/define** revient à utiliser une directive de préprocesseur [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), sauf que l’option de compilateur est appliquée à tous les fichiers du projet. Un symbole reste défini dans un fichier source jusqu’à ce qu’une directive [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) dans le fichier source en supprime la définition. Quand vous utilisez l’option /define, une directive `#undef` dans un fichier n’a aucun effet sur les autres fichiers de code source du projet.  
  
 Vous pouvez utiliser les symboles créés par cette option avec [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) et [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) pour effectuer une compilation conditionnelle des fichiers sources.  
  
 **/d** est la forme abrégée de **/define**.  
  
 Pour définir plusieurs symboles avec **/define**, séparez chaque nom de symbole par un point-virgule ou une virgule. Exemple :  
  
```console  
/define:DEBUG;TUESDAY  
```  
  
 Le compilateur C# lui-même ne définit aucun symbole ni aucune macro que vous pouvez utiliser dans votre code source ; toutes les définitions de symbole doivent être définies par l’utilisateur.  
  
> [!NOTE]
>  La directive C# `#define` ne permet de donner une valeur à un symbole, comme dans les langages tels que C++. Par exemple, l’option `#define` ne peut pas être utilisée pour créer une macro ni définir une constante. Si vous devez définir une constante, utilisez une variable `enum`. Si vous souhaitez créer une macro de style C++, envisagez l’alternative que constituent les génériques. Comme les macros sont notoirement sujettes aux erreurs, C# n’autorise pas leur utilisation, mais fournit des solutions plus sûres.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Dans l’onglet **Générer**, tapez le symbole à définir dans la zone **Symboles de compilation conditionnelle**. Par exemple, si vous utilisez l’exemple de code qui suit, tapez simplement `xx` dans la zone de texte.  
  
 Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.  
  
## <a name="example"></a>Exemple  
  
```csharp  
// preprocessor_define.cs  
// compile with: /define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test   
{  
    public static void Main()   
    {  
        #if (xx)   
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)

