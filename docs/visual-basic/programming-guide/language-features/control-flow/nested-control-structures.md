---
title: "Structures de contrôle imbriquées (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22adf4086cd494202a540b2ec16310072329b6ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="nested-control-structures-visual-basic"></a>Structures de contrôle imbriquées (Visual Basic)
Vous pouvez placer des instructions de contrôle dans d’autres instructions de contrôle, par exemple un `If...Then...Else` bloquer dans un `For...Next` boucle. Une instruction de contrôle à l’intérieur d’une autre instruction de contrôle est dite *imbriquée*.  
  
## <a name="nesting-levels"></a>Niveaux d’imbrication  
 Contrôler les structures dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] peuvent être imbriquées au nombre de niveaux que vous le souhaitez. Il est courant d’améliorer la lisibilité des structures imbriquées en retrait le corps de chacun d’eux. L’éditeur d’environnement (IDE) de développement intégré fait automatiquement.  
  
 Dans l’exemple suivant, la procédure `sumRows` additionne les éléments positifs de chaque ligne de la matrice.  
  
```  
Public Sub sumRows(ByVal a(,) As Double, ByRef r() As Double)  
    Dim i, j As Integer  
    For i = 0 To UBound(a, 1)  
        r(i) = 0  
        For j = 0 To UBound(a, 2)  
            If a(i, j) > 0 Then  
                r(i) = r(i) + a(i, j)  
            End If  
        Next j  
    Next i  
End Sub  
```  
  
 Dans l’exemple précédent, la première `Next` instruction ferme interne `For` boucle et la dernière `Next` instruction ferme externe `For` boucle.  
  
 De même, dans imbriqués `If` instructions, le `End If` instructions s’appliquent automatiquement à la précédente la plus proche `If` instruction. Imbriqué `Do` boucles fonctionnent de manière similaire, avec la plus profonde `Loop` instruction mise en correspondance la plus profonde `Do` instruction.  
  
> [!NOTE]
>  Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés de la structure sont mis en surbrillance. Par exemple, lorsque vous cliquez sur `If` dans un `If...Then...Else` construction, toutes les instances de `If`, `Then`, `ElseIf`, `Else`, et `End If` dans la construction sont mises en surbrillance. Pour déplacer vers le mot clé en surbrillance suivant ou précédent, appuyez sur CTRL + MAJ + flèche bas ou CTRL + MAJ + flèche haut.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Imbrication des différents types de Structures de contrôle  
 Vous pouvez imbriquer un type au sein d’un autre type de contrôle. L’exemple suivant utilise un `With` bloquer à l’intérieur d’un `For Each` boucle et imbriquées `If` bloque à l’intérieur de la `With` bloc.  
  
```  
For Each ctl As System.Windows.Forms.Control In Me.Controls  
    With ctl  
        .BackColor = System.Drawing.Color.Yellow  
        .ForeColor = System.Drawing.Color.Black  
        If .CanFocus Then  
            .Text = "Colors changed"  
            If Not .Focus() Then  
                ' Insert code to process failed focus.  
            End If  
        End If  
    End With  
Next ctl  
```  
  
## <a name="overlapping-control-structures"></a>Structures de contrôle qui se chevauchent  
 Vous ne peut pas chevaucher les structures de contrôle. Cela signifie que toute structure imbriquée doit être entièrement contenue dans la structure la plus profonde suivante. Par exemple, la disposition suivante n’est pas valide, car le `For` boucle se termine avant interne `With` fin du bloc.  
  
 ![Diagramme graphique d’imbrication non valide](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")  
Imbrication non valide de structures For et With  
  
 Le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur détecte les structures de contrôle qui se chevauchent et signale une erreur de compilation.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Structures de décision](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Structures de boucle](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Autres structures de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
