---
title: "Nested Control Structures (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, control flow"
  - "control structures, nested"
  - "conditional statements, nested"
  - "statements [Visual Basic], control flow"
  - "control flow, nested control statements"
  - "structures, nested control"
  - "nested control statements"
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Nested Control Structures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez insérer des instructions de contrôle dans d'autres instructions de contrôle, par exemple un bloc `If...Then...Else` dans une boucle `For...Next`.  Dans ce cas, l'instruction de contrôle est *imbriquée* dans une autre instruction de contrôle.  
  
## Niveaux d'imbrication  
 Dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)], les structures de contrôle peuvent être imbriquées selon le nombre de niveaux voulu.  Il est courant de mettre en retrait le corps de chaque structure imbriquée afin d'accroître la lisibilité.  L'éditeur d'environnement de développement intégré le fait automatiquement.  
  
 Dans l'exemple suivant, la procédure `sumRows` additionne les éléments positifs de chaque ligne de la matrice.  
  
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
  
 Dans l'exemple précédent, la première instruction `Next` ferme la boucle `For` interne et la dernière instruction `Next` ferme la boucle `For` externe.  
  
 De même, dans les instructions `If` imbriquées, les instructions `End If` s'appliquent automatiquement à l'instruction `If` précédente la plus proche.  Les boucles `Do` imbriquées fonctionnent de la même manière, dans le sens où l'instruction `Loop` la plus profonde correspond à l'instruction `Do` la plus profonde.  
  
> [!NOTE]
>  Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés de la structure sont mis en surbrillance.  Par exemple, lorsque vous cliquez sur `If` dans une construction `If...Then...Else`, toutes les instances des mots clés `If`, `Then`, `ElseIf`, `Else` et  `End If` de la construction sont mises en surbrillance.  Pour passer au mot clé en surbrillance suivant ou revenir au précédent, appuyez sur CTRL\+MAJ\+FLÈCHE BAS ou CTRL\+MAJ\+FLÈCHE HAUT.  
  
## Imbrication de genres de structures de contrôle différents  
 Vous pouvez imbriquer un genre de structure de contrôle dans un autre.  L'exemple suivant utilise un bloc `With` à l'intérieur d'une boucle `For Each` et des blocs `If` imbriqués à l'intérieur du bloc `With`.  
  
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
  
## Chevauchement de structures de contrôle  
 Vous ne devez pas faire en sorte que des structures de contrôle se chevauchent.  Cela signifie que toute structure imbriquée doit être entièrement contenue dans la structure la plus profonde suivante.  Par exemple, la disposition suivante n'est pas valide car la boucle `For` se termine avant la fin du bloc `With` interne.  
  
 ![Diagramme graphique d'imbrication non valide](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.png "NestExampleInvalid")  
Imbrication non valide de structures For et With  
  
 Le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] détecte ces chevauchements de structures de contrôle et signale une erreur de compilation.  
  
## Voir aussi  
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)