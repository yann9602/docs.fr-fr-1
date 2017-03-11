---
title: "Option Explicit Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Explicit"
  - "vb.OptionExplicit"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declaring variables, explicit"
  - "forced variable declaration in Option Explicit statement"
  - "Explicit keyword"
  - "explicit variable declaration"
  - "Option Explicit statement"
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Option Explicit Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Force la déclaration explicite de toutes les variables d'un fichier, ou permet les déclarations implicites de variables.  
  
## Syntaxe  
  
```  
Option Explicit { On | Off }  
```  
  
## Composants  
 `On`  
 Facultatif.  Active la vérification `Option Explicit`.  Si `On` ou `Off` n'est pas spécifié, la valeur par défaut est `On`.  
  
 `Off`  
 Facultatif.  Désactive la vérification `Option Explicit`.  
  
## Notes  
 Lorsque `Option Explicit On` ou `Option Explicit` apparaît dans un fichier, vous devez déclarer explicitement toutes les variables à l'aide des instructions `Dim` ou `ReDim`.  Si vous tentez d'utiliser un nom de variable non déclarée, une erreur se produit au moment de la compilation.  L'instruction `Option Explicit Off` permet une déclaration implicite des variables.  
  
 Si elle est utilisée, l'instruction `Option Explicit` doit apparaître dans un fichier avant toute autre instruction de code source.  
  
> [!NOTE]
>  Affecter à `Option Explicit` la valeur `Off` n'est pas une bonne pratique en général.  Vous risquez de mal orthographier un nom de variable dans un ou plusieurs emplacements, ce qui peut provoquer des résultats inattendus lors de l'exécution du programme.  
  
## Lorsqu'aucune instruction Option Explicit n'est présente  
 Si le code source ne contient pas d'instruction `Option Explicit`, le paramètre **Option Explicit** sur [Page Compiler, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) est utilisé.  Si le compilateur de ligne de commande est utilisé, l'option de compilateur [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) est utilisée.  
  
#### Pour définir Option Explicit dans l'IDE  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez un projet.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Cliquez sur l'onglet **Compiler**.  
  
3.  Définissez la valeur dans la zone **Option Explicit**.  
  
 Lorsque vous créez un projet, le paramètre **Option Explicit** dans l'onglet **Compiler** correspond au paramètre **Option Explicit** dans la boîte de dialogue **Valeurs par défaut VB**.  Pour accéder à la boîte de dialogue **Valeurs par défaut VB**, cliquez sur **Options** dans le menu **Outils**.  Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**.  Le paramètre par défaut initial dans **Valeurs par défaut VB** est `On`.  
  
#### Pour définir Option Explicit dans la ligne de commande  
  
-   Incluez l'option du compilateur [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) dans la commande **vbc**.  
  
## Exemple  
 L'exemple suivant utilise l'instruction `Option Explicit` pour forcer la déclaration explicite de toutes les variables.  Toute tentative d'utilisation d'une variable non déclarée se traduit par une erreur au moment de la compilation.  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/option-explicit-statement_2.vb)]  
  
## Voir aussi  
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)