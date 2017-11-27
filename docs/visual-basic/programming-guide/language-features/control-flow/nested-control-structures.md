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
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="8c3a2-102">Structures de contrôle imbriquées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c3a2-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="8c3a2-103">Vous pouvez placer des instructions de contrôle dans d’autres instructions de contrôle, par exemple un `If...Then...Else` bloquer dans un `For...Next` boucle.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="8c3a2-104">Une instruction de contrôle à l’intérieur d’une autre instruction de contrôle est dite *imbriquée*.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="8c3a2-105">Niveaux d’imbrication</span><span class="sxs-lookup"><span data-stu-id="8c3a2-105">Nesting Levels</span></span>  
 <span data-ttu-id="8c3a2-106">Contrôler les structures dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] peuvent être imbriquées au nombre de niveaux que vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-106">Control structures in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can be nested to as many levels as you want.</span></span> <span data-ttu-id="8c3a2-107">Il est courant d’améliorer la lisibilité des structures imbriquées en retrait le corps de chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="8c3a2-108">L’éditeur d’environnement (IDE) de développement intégré fait automatiquement.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="8c3a2-109">Dans l’exemple suivant, la procédure `sumRows` additionne les éléments positifs de chaque ligne de la matrice.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="8c3a2-110">Dans l’exemple précédent, la première `Next` instruction ferme interne `For` boucle et la dernière `Next` instruction ferme externe `For` boucle.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="8c3a2-111">De même, dans imbriqués `If` instructions, le `End If` instructions s’appliquent automatiquement à la précédente la plus proche `If` instruction.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="8c3a2-112">Imbriqué `Do` boucles fonctionnent de manière similaire, avec la plus profonde `Loop` instruction mise en correspondance la plus profonde `Do` instruction.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c3a2-113">Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés de la structure sont mis en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="8c3a2-114">Par exemple, lorsque vous cliquez sur `If` dans un `If...Then...Else` construction, toutes les instances de `If`, `Then`, `ElseIf`, `Else`, et `End If` dans la construction sont mises en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="8c3a2-115">Pour déplacer vers le mot clé en surbrillance suivant ou précédent, appuyez sur CTRL + MAJ + flèche bas ou CTRL + MAJ + flèche haut.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="8c3a2-116">Imbrication des différents types de Structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="8c3a2-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="8c3a2-117">Vous pouvez imbriquer un type au sein d’un autre type de contrôle.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="8c3a2-118">L’exemple suivant utilise un `With` bloquer à l’intérieur d’un `For Each` boucle et imbriquées `If` bloque à l’intérieur de la `With` bloc.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="8c3a2-119">Structures de contrôle qui se chevauchent</span><span class="sxs-lookup"><span data-stu-id="8c3a2-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="8c3a2-120">Vous ne peut pas chevaucher les structures de contrôle.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-120">You cannot overlap control structures.</span></span> <span data-ttu-id="8c3a2-121">Cela signifie que toute structure imbriquée doit être entièrement contenue dans la structure la plus profonde suivante.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="8c3a2-122">Par exemple, la disposition suivante n’est pas valide, car le `For` boucle se termine avant interne `With` fin du bloc.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 <span data-ttu-id="8c3a2-123">![Diagramme graphique d’imbrication non valide](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span><span class="sxs-lookup"><span data-stu-id="8c3a2-123">![Graphic diagram of invalid nesting](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span></span>  
<span data-ttu-id="8c3a2-124">Imbrication non valide de structures For et With</span><span class="sxs-lookup"><span data-stu-id="8c3a2-124">Invalid nesting of For and With structures</span></span>  
  
 <span data-ttu-id="8c3a2-125">Le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur détecte les structures de contrôle qui se chevauchent et signale une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="8c3a2-125">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c3a2-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c3a2-126">See Also</span></span>  
 [<span data-ttu-id="8c3a2-127">Flux de contrôle</span><span class="sxs-lookup"><span data-stu-id="8c3a2-127">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="8c3a2-128">Structures de décision</span><span class="sxs-lookup"><span data-stu-id="8c3a2-128">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="8c3a2-129">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="8c3a2-129">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="8c3a2-130">Autres structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="8c3a2-130">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
