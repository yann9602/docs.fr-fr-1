---
title: "&gt;&gt; Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.>>"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operator>>"
  - ">> operator [Visual Basic]"
  - "bit shift operators"
  - "operator >>"
  - "right shift operators"
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# &gt;&gt; Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Effectue un décalage arithmétique vers la droite sur un modèle binaire.  
  
## Syntaxe  
  
```  
  
result = pattern >> amount  
```  
  
## Composants  
 `result`  
 Obligatoire.  Valeur numérique intégrale.  Résultat du décalage du modèle binaire.  Le type de données est le même que celui de `pattern`.  
  
 `pattern`  
 Obligatoire.  Expression numérique entière.  Modèle binaire qui doit être décalé.  Le type de données doit être un type entier \(`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` ou `ULong`\).  
  
 `amount`  
 Obligatoire.  Expression numérique.  Nombre de bits pour décaler le modèle binaire.  Le type de données doit être `Integer` ou étendu à `Integer`.  
  
## Notes  
 Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés à une extrémité du résultat ne sont pas réintroduits à l'autre extrémité.  Dans un décalage arithmétique vers la droite, les bits décalés au\-delà de la position de bit la plus à droite sont supprimés, et le bit \(de signe\) le plus à gauche est propagé vers les positions de bit libérées à gauche.  Ainsi, si la valeur de `pattern` est négative, les positions libérées ont la valeur un ; sinon, elles ont la valeur zéro.  
  
 Sachez que les types de données `Byte`, `UShort`, `UInteger` et `ULong` sont considérés comme non signés, et qu'il n'y a donc aucun bit de signe à propager.  Si `pattern` est de type non signé, les positions libérées ont toujours la valeur zéro.  
  
 Pour empêcher que le décalage soit effectué par plus de bits que ne peut en contenir le résultat, Visual Basic masque la valeur de `amount` avec un masque de taille correspondant au type de données de `pattern`.  L'opérateur binaire AND de ces valeurs est utilisé pour le nombre de positions de décalage.  Les masques de taille sont les suivants :  
  
|Type de données de `pattern`|Masque de taille \(décimal\)|Masque de taille \(hexadécimal\)|  
|----------------------------------|----------------------------------|--------------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Si la valeur de `amount` est zéro, la valeur de `result` est identique à la valeur de `pattern`.  Si la valeur de `amount` est négative, elle est considérée comme une valeur non signée et masquée avec le masque de taille approprié.  
  
 Les décalages arithmétiques ne génèrent jamais d'exception de dépassement de capacité.  
  
## Surcharge  
 L'opérateur `>>` peut être *surchargé*, ce qui signifie qu'une classe ou une structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou de cette structure.  Si votre code utilise cet opérateur sur une telle classe ou structure, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `>>` pour effectuer des décalages arithmétiques vers la droite sur des valeurs intégrales.  Le résultat a toujours le même type de données que celui de l'expression décalée.  
  
 [!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/right-shift-operator_1.vb)]  
  
 Les résultats de l'exemple précédent sont les suivants :  
  
-   `result1` est 2560 \(0000 1010 0000 0000\).  
  
-   `result2` est 160 \(0000 0000 1010 0000\).  
  
-   `result3` est 2 \(0000 0000 0000 0010\).  
  
-   `result4` est 640 \(0000 0010 1000 0000\).  
  
-   `result5` est 0 \(décalé de 15 places vers la droite\).  
  
 Le nombre de positions de décalage pour `result4` est calculé comme 18 AND 15, ce qui équivaut à 2.  
  
 L'exemple suivant affiche des décalages arithmétiques sur une valeur négative.  
  
 [!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/right-shift-operator_2.vb)]  
  
 Les résultats de l'exemple précédent sont les suivants :  
  
-   `negresult1` est \-512 \(1111 1110 0000 0000\).  
  
-   `negresult2` est \-1 \(le bit de signe est propagé\).  
  
## Voir aussi  
 [Bit Shift Operators](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [\>\>\= Operator](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)