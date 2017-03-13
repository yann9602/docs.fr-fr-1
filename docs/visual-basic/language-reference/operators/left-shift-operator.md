---
title: "&lt;&lt; Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.<<"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "bit shift operators"
  - "<< operator [Visual Basic]"
  - "operator <<, Visual Basic left shift operator"
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# &lt;&lt; Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Effectue un décalage arithmétique vers la gauche sur un modèle binaire.  
  
## Syntaxe  
  
```  
  
result = pattern << amount  
```  
  
## Composants  
 `result`  
 Obligatoire.  Valeur numérique intégrale.  Résultat du décalage du modèle binaire.  Le type de données est le même que celui de `pattern`.  
  
 `pattern`  
 Obligatoire.  Expression numérique entière.  Modèle binaire qui doit être décalé.  Le type de données doit être un type entier \(`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` ou `ULong`\).  
  
 `amount`  
 Obligatoire.  Expression numérique.  Nombre de bits pour décaler le modèle binaire.  Le type de données doit être `Integer` ou étendu à `Integer`.  
  
## Notes  
 Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés à une extrémité du résultat ne sont pas réintroduits à l'autre extrémité.  Dans un décalage arithmétique vers la gauche, les bits décalés au\-delà de la plage du type de données de résultat sont ignorés, et les positions des bits libérées à droite ont la valeur zéro.  
  
 Pour empêcher que le décalage soit effectué par plus de bits que ne peut en contenir le résultat, Visual Basic masque la valeur de `amount` avec un masque de taille correspondant au type de données de `pattern`.  L'opérateur binaire AND de ces valeurs est utilisé pour le nombre de positions de décalage.  Les masques de taille sont les suivants :  
  
|Type de données de `pattern`|Masque de taille \(décimal\)|Masque de taille \(hexadécimal\)|  
|----------------------------------|----------------------------------|--------------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Si la valeur de `amount` est zéro, la valeur de `result` est identique à la valeur de `pattern`.  Si la valeur de `amount` est négative, elle est considérée comme une valeur non signée et masquée avec le masque de taille approprié.  
  
 Les décalages arithmétiques ne génèrent jamais d'exception de dépassement de capacité.  
  
> [!NOTE]
>  L'opérateur `<<` peut être *surchargé*, ce qui signifie qu'une classe ou une structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou de cette structure.  Si votre code utilise cet opérateur sur une telle classe ou structure, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `<<` pour effectuer des décalages arithmétiques vers la gauche sur des valeurs intégrales.  Le résultat a toujours le même type de données que celui de l'expression décalée.  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 Les résultats de l'exemple précédent sont les suivants :  
  
-   `result1` est 192 \(0000 0000 1100 0000\).  
  
-   `result2` est 3072 \(0000 1100 0000 0000\).  
  
-   `result3` est \-32 768 \(1000 0000 0000 0000\).  
  
-   `result4` est 384 \(0000 0001 1000 0000\).  
  
-   `result5` est 0 \(décalé de 15 places vers la gauche\).  
  
 Le nombre de positions de décalage pour `result4` est calculé comme 17 AND 15, ce qui équivaut à 1.  
  
## Voir aussi  
 [Bit Shift Operators](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [\<\<\= Operator](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)