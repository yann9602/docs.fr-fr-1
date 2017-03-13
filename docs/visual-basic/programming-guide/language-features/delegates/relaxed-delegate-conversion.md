---
title: "Relaxed Delegate Conversion (Visual Basic) | Microsoft Docs"
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
  - "relaxed delegate conversion [Visual Basic]"
  - "delegates [Visual Basic], relaxed conversion"
  - "conversions, relaxed delegate"
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Relaxed Delegate Conversion (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

La conversion simplifiée des délégués vous permet d'assigner des subs et des fonctions aux délégués ou aux gestionnaires même lorsque leurs signatures ne sont pas identiques. Par conséquent, la liaison aux délégués devient cohérente avec la liaison déjà autorisée pour les appels de méthodes.  
  
## Paramètres et type de retour  
 À la place d'une correspondance de signature exacte, la conversion simplifiée requiert que les conditions suivantes soient réunies lorsque `Option Strict` a la valeur `On` :  
  
-   Une conversion étendue doit avoir lieu, du type de données de chaque paramètre de délégué en type de données du paramètre correspondant de la fonction ou du `Sub` assigné.  Dans l'exemple suivant, le délégué `Del1` possède un seul paramètre, un `Integer`.  Le paramètre `m` dans les expressions lambda assignées doit présenter un type de données pour lequel il existe une conversion étendue de `Integer`, tel que `Long` ou `Double`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     Les conversions restrictives sont autorisées uniquement lorsque `Option Strict` a la valeur `Off`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   Une conversion étendue doit avoir lieu dans le sens opposé, du type de retour de la fonction ou du `Sub` assigné en type de retour du délégué.  Dans les exemples suivants, le corps de chaque expression lambda assignée doit avoir la valeur d'un type de données qui s'étend à `Integer` étant donné que le type de retour de `del1` est `Integer`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 Si `Option Strict` a la valeur `Off`, la restriction étendue est supprimée dans les deux directions.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## Omission des spécifications de paramètres  
 Les délégués simplifiés vous permettent également d'omettre complètement les spécifications de paramètres dans la méthode assignée :  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 Notez que vous ne pouvez pas spécifier certains paramètres et en omettre d'autres.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 L'omission des paramètres est utile par exemple lors de la définition d'un gestionnaire d'événements, où plusieurs paramètres complexes sont impliqués.  Les arguments de certains gestionnaires d'événements ne sont pas utilisés.  À la place, le gestionnaire accède directement à l'état du contrôle dans lequel l'événement est enregistré et ignore les arguments.  Les délégués simplifiés vous permettent d'omettre les arguments dans les déclarations qui ne comprennent aucune ambiguïté.  Dans l'exemple suivant, la méthode `OnClick` intégralement spécifiée peut être réécrite en tant que `RelaxedOnClick`.  
  
```vb#  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## Exemples d'AddressOf  
 Les expressions lambda sont utilisées dans les exemples précédents de manière à simplifier l'affichage des relations des types.  Toutefois, les mêmes simplifications sont autorisées pour les assignations de délégués qui utilisent `AddressOf`, `Handles` ou `AddHandler`.  
  
 Dans l'exemple suivant, les fonctions `f1`, `f2`, `f3` et `f4` peuvent toutes être assignées à `Del1`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 L'exemple suivant est valide uniquement lorsque `Option Strict` a la valeur `Off`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## Déplacement des retours de la fonction  
 La conversion simplifiée des délégués vous permet d'assigner une fonction à un délégué `Sub`, en ignorant la valeur de retour de la fonction.  Toutefois, vous ne pouvez pas assigner un `Sub` à un délégué de fonction.  Dans l'exemple suivant, l'adresse de la fonction `doubler` est assignée au délégué `Sub` `Del3`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## Voir aussi  
 [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)