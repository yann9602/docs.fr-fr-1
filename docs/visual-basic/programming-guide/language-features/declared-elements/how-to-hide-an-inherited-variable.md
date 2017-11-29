---
title: "Comment : masquer une variable héritée (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d2059da873f8b9ec9ea51191139c652a9e01d92b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>Comment : masquer une variable héritée (Visual Basic)
Une classe dérivée hérite de toutes les définitions de sa classe de base. Si vous souhaitez définir une variable à l’aide du même nom qu’un élément de la classe de base, vous pouvez masquer, ou *ombre*, cet élément de la classe de base lorsque vous définissez votre variable dans la classe dérivée. Si vous faites cela, le code dans la classe dérivée accède à votre variable, sauf si elle ignore explicitement le mécanisme d’occultation.  
  
 Une autre raison, que vous souhaiterez peut-être masquer une variable héritée est pour vous protéger contre la révision de la classe de base. La classe de base peut subir une modification qui modifie l’élément que vous héritez. Si cela se produit, le `Shadows` modificateur force les références de la classe dérivée pour être résolu à votre variable, au lieu de l’élément de la classe de base.  
  
### <a name="to-hide-an-inherited-variable"></a>Pour masquer une variable héritée  
  
1.  Assurez-vous que la variable que vous souhaitez masquer est déclarée au niveau de la classe (en dehors de toute procédure). Sinon vous n’avez pas besoin de le masquer.  
  
2.  À l’intérieur de votre classe dérivée, écrivez une [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) déclarer votre variable. Utiliser le même nom que celui de la variable héritée.  
  
3.  Inclure le [ombres](../../../../visual-basic/language-reference/modifiers/shadows.md) mot clé dans la déclaration.  
  
     Lorsque le code de la classe dérivée fait référence au nom de variable, le compilateur résout la référence à la variable.  
  
     L’exemple suivant illustre l’occultation d’une variable héritée.  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     L’exemple précédent déclare la variable `shadowString` dans la classe de base et la masque dans la classe dérivée. La procédure `showStrings` dans la classe dérivée affiche la version de masquage de la chaîne lorsque le nom `shadowString` n’est pas qualifié. Il affiche ensuite la version occultée lorsque `shadowString` est qualifié avec le `MyBase` (mot clé).  
  
## <a name="robust-programming"></a>Programmation fiable  
 L’occultation introduit plusieurs versions d’une variable portant le même nom. Lorsqu’une instruction de code fait référence au nom de variable, la version à laquelle le compilateur résout la référence dépend de facteurs tels que l’emplacement de l’instruction de code et la présence d’une chaîne qualifiante. Cela peut augmenter le risque de faire référence à une version non souhaitée d’une variable occultée. Vous pouvez réduire ce risque en qualifier complètement toutes les références à une variable occultée.  
  
## <a name="see-also"></a>Voir aussi  
 [Références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Occultation dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Différences entre l'occultation et la substitution](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [Guide pratique : masquer une variable portant le même nom que votre variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Guide pratique : accéder à une variable masquée par une classe dérivée](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me, My, MyBase et MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Éléments fondamentaux de l’héritage](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
