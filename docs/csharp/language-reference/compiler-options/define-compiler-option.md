---
title: "/define (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/define"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-define compiler option [C#]"
  - "/define compiler option [C#]"
  - "-d compiler option [C#]"
  - "define compiler option [C#]"
  - "/d compiler option [C#]"
  - "d compiler option [C#]"
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /define (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'option **\/define** définit `name` comme un symbole dans tous les fichiers de code source de votre programme.  
  
## Syntaxe  
  
```  
/define:name[;name2]  
```  
  
## Arguments  
 `name`, `name2`  
 Nom de chaque symbole que vous souhaitez définir.  
  
## Notes  
 L'option **\/define** a le même effet qu'utiliser une directive de préprocesseur [\#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), sauf que l'option de compilateur est appliquée à tous les fichiers du projet.  Un symbole reste défini dans un fichier source jusqu'à ce qu'une directive [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) dans le fichier source en supprime la définition.  Lorsque vous utilisez l'option \/define, une directive `#undef` dans un fichier n'a aucun effet sur les autres fichiers de code source du projet.  
  
 Vous pouvez utiliser les symboles créés par cette option avec [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [\#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [\#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) et [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) pour effectuer une compilation conditionnelle des fichiers sources.  
  
 **\/d** est la forme abrégée de **\/define**.  
  
 Pour définir plusieurs symboles avec l'option **\/define**, séparez chaque nom de symbole par un point\-virgule ou une virgule.  Par exemple :  
  
```  
/define:DEBUG;TUESDAY  
```  
  
 Le compilateur C\# lui\-même ne définit aucun symbole ou macro que vous pouvez utiliser dans votre code source ; toutes les définitions de symbole doivent être définies par l'utilisateur.  
  
> [!NOTE]
>  La directive C\# `#define` ne permet de donner une valeur à un symbole, comme dans les langages tels que C\+\+.  Par exemple, `#define` ne peuvent pas être utilisés pour créer une macro ou définir une constante.  Si vous devez définir une constante, utilisez une variable `enum`.  Si vous souhaitez créer une macro de style C\+\+, utilisez l'alternative que constituent les génériques.  Comme les macros sont notoirement sujettes aux erreurs, C\# n'autorise pas leur utilisation, mais fournit des solutions plus sûres.  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Dans l'onglet **Générer**, tapez le symbole à définir dans la zone de texte **Symboles de compilation conditionnelle**.  Par exemple, si vous utilisez l'exemple de code qui suit, tapez seulement `xx` dans la zone de texte.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.  
  
## Exemple  
  
```  
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
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)