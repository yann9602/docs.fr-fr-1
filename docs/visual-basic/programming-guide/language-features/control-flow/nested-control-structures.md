---
title: "Imbriqué des Structures de contrôle (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, control flow
- control structures, nested
- conditional statements, nested
- statements [Visual Basic], control flow
- control flow, nested control statements
- structures, nested control
- nested control statements
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4afc0afc2ad63d03f2c4251640d3682b2b184504
ms.lasthandoff: 03/13/2017

---
# <a name="nested-control-structures-visual-basic"></a>Structures de contrôle imbriquées (Visual Basic)
Vous pouvez placer des instructions de contrôle dans d’autres instructions de contrôle, par exemple un `If...Then...Else` bloquer dans un `For...Next` boucle. Une instruction de contrôle dans une autre instruction de contrôle est dite *imbriquées*.  
  
## <a name="nesting-levels"></a>Niveaux d’imbrication  
 Contrôler les structures dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] peuvent être imbriquées sur autant de niveaux que vous le souhaitez. Il est courant d’améliorer la lisibilité des structures imbriquées en retrait le corps de chacun d’eux. L’éditeur d’environnement (IDE) de développement intégré fait automatiquement.  
  
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
  
 Dans l’exemple précédent, la première `Next` instruction ferme interne `For` boucle et le dernier `Next` instruction ferme externe `For` boucle.  
  
 De même, imbriqués dans `If` instructions, le `End If` instructions s’appliquent automatiquement à la précédente la plus proche `If` instruction. Imbriquées `Do` boucles fonctionnent de la même manière, avec le plus interne `Loop` instruction correspondant à celui du `Do` instruction.  
  
> [!NOTE]
>  Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés de la structure sont mis en surbrillance. Par exemple, lorsque vous cliquez sur `If` dans un `If...Then...Else` construction, toutes les instances de `If`, `Then`, `ElseIf`, `Else`, et `End If` dans la construction sont mises en surbrillance. Pour passer au mot clé en surbrillance suivant ou précédent, appuyez sur CTRL + MAJ + BAS ou CTRL + MAJ + flèche haut.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Imbrication des différents types de Structures de contrôle  
 Vous pouvez imbriquer un type au sein d’un autre type de contrôle. L’exemple suivant utilise un `With` bloquer à l’intérieur d’un `For Each` une boucle et imbriqués `If` bloque à l’intérieur de la `With` bloc.  
  
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
 Structures de contrôle ne peut pas se chevauchent. Cela signifie que toute structure imbriquée doit être entièrement contenue dans la structure la plus profonde suivante. Par exemple, la disposition suivante n’est pas valide, car le `For` boucle se termine avant interne `With` fin du bloc.  
  
 ![Diagramme graphique d’imbrication non valide](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")  
Imbrication non valide de structures For et With  
  
 Le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur détecte les structures de contrôle qui se chevauchent et signale une erreur de compilation.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Structures de décision](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Structures de boucle](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Autres structures de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
