---
title: "+ Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.+"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arithmetic operators, addition"
  - "+ operator"
  - "concatenation operators, syntax"
  - "strings [Visual Basic], concatenating"
  - "sum operator"
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
caps.latest.revision: 26
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 26
---
# + Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Ajoute deux nombres ou retourne la valeur positive d'une expression numérique.  Peut être également utilisé pour concaténer deux expressions de chaîne.  
  
## Syntaxe  
  
```  
  
      expression1 + expression2  
- or -  
+ expression1  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`expression1`|Obligatoire.  Toute expression numérique ou de chaîne.|  
|`expression2`|Requis sauf si l'opérateur `+` calcule une valeur négative.  Toute expression numérique ou de chaîne.|  
  
## Résultat  
 Si `expression1` et `expression2` sont tous les deux numériques, le résultat est leur somme arithmétique.  
  
 Si `expression2` est absent, l'opérateur `+` est l'opérateur d'identité *unaire* pour la valeur inchangée d'une expression.  Dans ce sens, l'opération consiste à conserver le signe de `expression1` ; le résultat est donc négatif si `expression1` est négatif.  
  
 Si `expression1` et `expression2` sont tous les deux des chaînes, le résultat est la concaténation de leurs valeurs.  
  
 Si `expression1` et `expression2` sont de types mixtes, l'action effectuée dépend de leurs types, leur contenu et le paramètre de l'[Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  Pour plus d'informations, consultez les tableaux dans « Remarks ».  
  
## Types pris en charge  
 Tous les types numériques, y compris les types non signés et à virgule flottante, ainsi que `Decimal` et `String`.  
  
## Notes  
 En général, `+` effectue l'addition arithmétique lorsque cela est possible et concatène uniquement lorsque les deux expressions sont des chaînes.  
  
 Si aucune expression n'est un `Object`, Visual Basic effectue les actions suivantes.  
  
|||  
|-|-|  
|Types de données d'expressions|Action du compilateur|  
|Toutes les expressions sont de types de données numériques \(`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single` ou `Double`\)|Additionne.  Le type de données de résultat est un type numérique approprié aux types de données de `expression1` et `expression2`.  Consultez les tableaux « Arithmétique sur les entiers » dans [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Toutes les expressions sont de type `String`|Concatène.|  
|Une expression est un type de données numérique et l'autre est une chaîne.|Si `Option Strict` est `On`, une erreur du compilateur est générée.<br /><br /> Si `Option Strict` est `Off`, le `String` est implicitement converti en `Double`, puis il est ajouté.<br /><br /> Si `String` ne peut pas être converti en `Double`, une exception <xref:System.InvalidCastException> est levée.|  
|Une expression est un type de données numérique et l'autre est [Nothing](../../../visual-basic/language-reference/nothing.md).|Ajoute, avec `Nothing` évaluée à zéro.|  
|Une expression est une chaîne, l'autre est `Nothing`.|Concatène, avec `Nothing` évalué comme "".|  
  
 Si une expression est une expression `Object`, Visual Basic effectue les actions suivantes.  
  
|||  
|-|-|  
|Types de données d'expressions|Action du compilateur|  
|L'expression `Object` contient une valeur numérique et l'autre est un type de données numérique|Si `Option Strict` est `On`, une erreur du compilateur est générée.<br /><br /> Ajoute si `Option Strict` est `Off`.|  
|L'expression `Object` contient une valeur numérique et l'autre est de type `String`|Si `Option Strict` est `On`, une erreur du compilateur est générée.<br /><br /> Si `Option Strict` est `Off`, le `String` est implicitement converti en `Double`, puis il est ajouté.<br /><br /> Si `String` ne peut pas être converti en `Double`, une exception <xref:System.InvalidCastException> est levée.|  
|L'expression `Object` contient une chaîne et l'autre est un type de données numérique|Si `Option Strict` est `On`, une erreur du compilateur est générée.<br /><br /> Si `Option Strict` est `Off`, la chaîne `Object` est implicitement convertie en `Double`, puis elle est ajoutée.<br /><br /> Si la chaîne `Object` ne peut pas être convertie en `Double`, une exception <xref:System.InvalidCastException> est levée.|  
|L'expression `Object` contient une chaîne et l'autre est de type `String`|Si `Option Strict` est `On`, une erreur du compilateur est générée.<br /><br /> Si `Option Strict` est `Off`, `Object` est implicitement converti en `String` et est concaténé.|  
  
 Si les deux expressions sont des expressions `Object`, Visual Basic effectue les actions suivantes \(`Option Strict Off` uniquement\).  
  
|||  
|-|-|  
|Types de données d'expressions|Action du compilateur|  
|Toutes les expressions `Object` contiennent des valeurs numériques|Additionne.|  
|Toutes les expressions `Object` sont de type `String`|Concatène.|  
|Une expression `Object` contient une valeur numérique et l'autre contient une chaîne|Convertit implicitement la chaîne `Object` en `Double` et l'ajoute.<br /><br /> Si la chaîne `Object` ne peut pas être convertie en une valeur numérique, une exception <xref:System.InvalidCastException> est levée.|  
  
 Si l'une des expressions `Object` prend la valeur [Nothing](../../../visual-basic/language-reference/nothing.md) ou <xref:System.DBNull>, l'opérateur `+` la considère comme un `String` de valeur "".  
  
> [!NOTE]
>  Si vous utilisez l'opérateur `+`, il vous sera parfois difficile de déterminer si une addition ou une concaténation de chaînes se produira.  Utilisez l'opérateur `&` pour la concaténation afin d'éliminer toute ambiguïté et de fournir un code auto\-documenté.  
  
## Surcharge  
 L'opérateur `+` peut être *surchargé*, ce qui signifie qu'une classe ou structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou structure.  Si votre code utilise cet opérateur sur une telle classe ou structure, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 Cet exemple suivant utilise l'opérateur `+` pour ajouter des nombres.  Si les opérandes sont tous numériques, Visual Basic calcule le résultat arithmétique.  Le résultat arithmétique représente la somme des deux opérandes.  
  
 [!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/addition-operator_1.vb)]  
  
 Vous pouvez également utiliser l'opérateur `+` pour concaténer des chaînes.  Si les opérandes sont tous des chaînes, Visual Basic les concatène.  Le résultat de concaténation représente une chaîne unique composée du contenu des deux opérandes l'un après l'autre.  
  
 Si les opérandes sont de types mixtes, le résultat dépend du paramètre de l'[Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  L'exemple suivant illustre le résultat lorsque `Option Strict` est `On`.  
  
 [!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/addition-operator_4.vb)]  
  
 L'exemple suivant illustre le résultat lorsque `Option Strict` est `Off`.  
  
 [!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/addition-operator_6.vb)]  
  
 Pour éliminer toute ambiguïté, vous devez utiliser l'opérateur `&` au lieu de `+` pour la concaténation.  
  
## Voir aussi  
 [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md)   
 [Concatenation Operators](../../../visual-basic/language-reference/operators/concatenation-operators.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)