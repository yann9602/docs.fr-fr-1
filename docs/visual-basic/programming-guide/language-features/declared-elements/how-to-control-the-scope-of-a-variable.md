---
title: "Comment : contrôler la portée d'une variable (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7284d344e3bf0fdd0f900f2a820d6c8db4a4bf74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Comment : contrôler la portée d'une variable (Visual Basic)
Normalement, une variable est dans *étendue*, ou est visible par référence, tout au long de la région dans laquelle vous la déclarez. Dans de certains cas, la variable *niveau d’accès* peut influencer sa portée.  
  
 Pour plus d’informations, consultez [étendue en Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="scope-at-block-or-procedure-level"></a>Portée au niveau de la procédure ou de bloc  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Pour rendre une variable visible uniquement dans un bloc  
  
-   Place le [Dim (instruction)](../../../../visual-basic/language-reference/statements/dim-statement.md) de la variable entre le début et de fin des instructions de déclaration de ce bloc, par exemple entre le `For` et `Next` instructions d’un `For` boucle.  
  
     Vous pouvez faire référence à la variable uniquement à partir du bloc.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Pour rendre une variable visible uniquement dans une procédure  
  
-   Place le `Dim` instruction de la variable à l’intérieur de la procédure, mais en dehors de tout bloc (comme un `With`... `End With` bloc).  
  
     Vous pouvez faire référence à la variable uniquement à partir de la procédure, y compris à l’intérieur d’un bloc contenu dans la procédure.  
  
## <a name="scope-at-module-or-namespace-level"></a>Portée au niveau du Module ou Namespace  
 Pour plus de commodité, le terme unique *au niveau du module* s’applique aussi aux modules, les classes et structures. Le niveau d’accès d’une variable de niveau module détermine sa portée. L’espace de noms qui contient le module, classe ou structure influence également la portée.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Pour rendre une variable visible dans l’ensemble d’un module, classe ou structure  
  
1.  Place la `Dim` instruction de la variable à l’intérieur du module, classe ou structure, mais en dehors de toute procédure.  
  
2.  Inclure le [privé](../../../../visual-basic/language-reference/modifiers/private.md) mot clé dans la `Dim` instruction.  
  
3.  Vous pouvez faire référence à la variable à partir de n’importe où dans le module, classe ou structure, mais pas à l’extérieur.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Pour rendre une variable visible dans l’ensemble d’un espace de noms  
  
1.  Place la `Dim` instruction de la variable à l’intérieur du module, classe ou structure, mais en dehors de toute procédure.  
  
2.  Inclure le [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) ou [Public](../../../../visual-basic/language-reference/modifiers/public.md) mot clé dans la `Dim` instruction.  
  
3.  Vous pouvez faire référence à la variable à partir de n’importe où dans l’espace de noms contenant le module, classe ou structure.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant déclare une variable au niveau du module et limite sa visibilité au code dans le module.  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 Dans l’exemple précédent, toutes les procédures définies dans le module `demonstrateScope` peuvent faire référence à la `String` variable `strMsg`. Lorsque le `usePrivateVariable` procédure est appelée, elle affiche le contenu de la variable chaîne `strMsg` dans une boîte de dialogue.  
  
 Avec la modification suivante apportée à l’exemple précédent, la variable chaîne `strMsg` peuvent être référencés par le code n’importe où dans l’espace de noms de sa déclaration.  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Programmation fiable  
 Plus la portée d’une variable, les opportunités moins pour accidentellement qui fait référence à la place d’une autre variable portant le même nom. Vous pouvez également réduire les problèmes de correspondance de référence.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Plus la portée d’une variable limitée, moins vous risquez constituant un code malveillant peut incorrect utiliser.  
  
## <a name="see-also"></a>Voir aussi  
 [Portée dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Durée de vie dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Dim (instruction)](../../../../visual-basic/language-reference/statements/dim-statement.md)
