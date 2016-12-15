---
title: "Mod, op&#233;rateur (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Mod"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "reste, opérateur Mod"
  - "opérateur de division, opérateur Mod"
  - "opérateur modulo, Visual Basic"
  - "opérateur Mod [Visual Basic]"
  - "opérateurs [Visual Basic], division"
  - "opérateurs arithmétiques, Mod"
  - "opérateurs mathématiques"
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Mod, op&#233;rateur (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Effectue la division de deux nombres et retourne seulement le reste.  
  
## Syntaxe  
  
```  
  
number1 Mod number2  
```  
  
## Composants  
 `number1`  
 Requis.  Toute expression numérique.  
  
 `number2`  
 Requis.  Toute expression numérique.  
  
## Types pris en charge  
 Tous les types numériques.  Cela inclut les types non signés et à virgule flottante et `Decimal`.  
  
## Résultat  
 Le résultat représente le reste après la division de `number1` par `number2`.  Par exemple, l'expression `14 Mod 4` prend la valeur 2.  
  
## Notes  
 Si `number1` ou `number2` est une valeur à virgule flottante, le reste à virgule flottante de la division est retourné.  Le type de données du résultat est le plus petit type de données pouvant contenir toutes les valeurs possibles résultant de la division avec les types de données de `number1` et `number2`.  
  
 Si `number1` ou `number2` correspond à [Nothing](../../../visual-basic/language-reference/nothing.md), elle est considérée comme un zéro.  
  
 Les opérateurs connexes incluent les éléments suivants :  
  
-   [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md) retourne le quotient entier d'une division.  Par exemple, l'expression `14 \ 4` prend la valeur 3.  
  
-   [\/ Operator](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retourne le quotient complet, y compris le reste, en tant que nombre à virgule flottante.  Par exemple, l'expression `14 / 4` prend la valeur 3,5.  
  
## Essai de division par zéro  
 Si `number2` correspond à zéro, le comportement de l'opérateur `Mod` dépend du type de données des opérandes.  Une division intégrale lève une exception <xref:System.DivideByZeroException>.  Une division de nombres à virgule flottante retourne <xref:System.Double.NaN>.  
  
## Formule équivalente  
 L'expression `a Mod b` est équivalente à l'une ou l'autre des formules suivantes :  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## Imprécision des nombres à virgule flottante  
 Lorsque vous utilisez des nombres à virgule flottante, n'oubliez pas qu'ils n'ont pas toujours de représentation précise dans la mémoire.  Certaines opérations pourraient avoir des résultats inattendus, comme la comparaison de valeur et l'opérateur `Mod`.  Pour plus d'informations, consultez [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## Surcharge  
 L'opérateur `Mod` *peut être surchargé*, ce qui signifie qu'une classe ou une structure peut redéfinir son comportement.  Si votre code applique `Mod` sur l'instance d'une classe ou d'une structure qui inclut une telle surcharge, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `Mod` pour diviser deux nombres et retourner seulement le reste.  Si l'un des nombres est à virgule flottante, le résultat est un nombre à virgule flottante représentant le reste.  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## Exemple  
 L'exemple suivant montre l'imprécision potentielle des opérandes à virgule flottante.  Dans la première instruction, les opérandes sont `Double` et 0,2 représente une fraction binaire se répétant à l'infini avec une valeur stockée de 0,20000000000000001.  Dans la deuxième instruction, le caractère de type de littéral `D` force les deux opérandes sur la valeur `Decimal` et 0,2 a une représentation précise.  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md)