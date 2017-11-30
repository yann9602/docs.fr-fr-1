---
title: "+ Opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb0d66db2d777c046ccec69acc1f2069d21baf6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>+, opérateur (Visual Basic)
Additionne deux nombres ou retourne la valeur positive d’une expression numérique. Peut également être utilisé pour concaténer deux expressions de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`expression1`|Obligatoire. Toute expression numérique ou chaîne.|  
|`expression2`|Requis sauf si la `+` opérateur calcule une valeur négative. Toute expression numérique ou chaîne.|  
  
## <a name="result"></a>Résultat  
 Si `expression1` et `expression2` sont toutes deux numériques, le résultat est leur somme arithmétique.  
  
 Si `expression2` est absent, le `+` opérateur est la *unaire* opérateur d’identité pour la valeur inchangée d’une expression. Dans ce sens, l’opération consiste à conserver le signe de `expression1`, de sorte que le résultat est un nombre négatif si `expression1` est un nombre négatif.  
  
 Si `expression1` et `expression2` sont des chaînes, le résultat est la concaténation de leurs valeurs.  
  
 Si `expression1` et `expression2` sont de types mixtes, l’action effectuée dépend de leurs types, leur contenu et le paramètre de la [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md). Pour plus d’informations, consultez les tables dans la section « Notes ».  
  
## <a name="supported-types"></a>Types pris en charge  
 Tous les types numériques, y compris les types non signés et à virgule flottante et `Decimal`, et `String`.  
  
## <a name="remarks"></a>Remarques  
 En règle générale, `+` effectue l’addition arithmétique lorsque cela est possible et concatène uniquement lorsque les deux expressions sont des chaînes.  
  
 Si aucune expression n’est un `Object`, Visual Basic effectue les actions suivantes.  
  
|Types de données des expressions|Action du compilateur|  
|---|---|  
|Les deux expressions sont des types de données numériques (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, ou `Double`)|Ajouter. Le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2`. Consultez les tableaux « Arithmétique sur les entiers » dans [Types de données de résultats de l’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Les deux expressions sont de type`String`|Concaténer.|  
|Une expression est un type de données numérique et l’autre est une chaîne|Si `Option Strict` est `On`, puis générer une erreur du compilateur.<br /><br /> Si `Option Strict` est `Off`, puis de convertir implicitement le `String` à `Double` et ajouter.<br /><br /> Si le `String` ne peut pas être converti en `Double`, levez une <xref:System.InvalidCastException> exception.|  
|Une expression est un type de données numérique, et l’autre est [Nothing](../../../visual-basic/language-reference/nothing.md)|Ajouter, avec `Nothing` évaluée à zéro.|  
|Une expression est une chaîne, et l’autre est`Nothing`|Concatène, avec `Nothing` évalués en tant que « ».|  
  
 Si une expression est un `Object` expression, Visual Basic effectue les actions suivantes.  
  
|Types de données des expressions|Action du compilateur|  
|---|---|  
|`Object`l’expression contient une valeur numérique et l’autre est un type de données numériques|Si `Option Strict` est `On`, puis générer une erreur du compilateur.<br /><br /> Si `Option Strict` est `Off`, puis ajouter.|  
|`Object`l’expression contient une valeur numérique et l’autre est de type`String`|Si `Option Strict` est `On`, puis générer une erreur du compilateur.<br /><br /> Si `Option Strict` est `Off`, puis de convertir implicitement le `String` à `Double` et ajouter.<br /><br /> Si le `String` ne peut pas être converti en `Double`, levez une <xref:System.InvalidCastException> exception.|  
|`Object`l’expression contient une chaîne et l’autre est un type de données numériques|Si `Option Strict` est `On`, puis générer une erreur du compilateur.<br /><br /> Si `Option Strict` est `Off`, puis convertit implicitement la chaîne `Object` à `Double` et ajouter.<br /><br /> Si la chaîne `Object` ne peut pas être converti en `Double`, levez une <xref:System.InvalidCastException> exception.|  
|`Object`l’expression contient une chaîne et l’autre est de type`String`|Si `Option Strict` est `On`, puis générer une erreur du compilateur.<br /><br /> Si `Option Strict` est `Off`, puis de convertir implicitement `Object` à `String` et concaténer.|  
  
 Si les deux expressions sont `Object` expressions, Visual Basic effectue les actions suivantes (`Option Strict Off` uniquement).  
  
|Types de données des expressions|Action du compilateur|  
|---|---|  
|Les deux `Object` expressions contiennent des valeurs numériques|Ajouter.|  
|Les deux `Object` expressions sont de type`String`|Concaténer.|  
|Un `Object` l’expression contient une valeur numérique et l’autre contient une chaîne|Convertit implicitement la chaîne `Object` à `Double` et ajouter.<br /><br /> Si la chaîne `Object` ne peut pas être converti en valeur numérique, puis lève une <xref:System.InvalidCastException> exception.|  
  
 Si le paramètre `Object` expression renvoie la valeur [rien](../../../visual-basic/language-reference/nothing.md) ou <xref:System.DBNull>, le `+` opérateur traite en tant qu’un `String` avec la valeur « ».  
  
> [!NOTE]
>  Lorsque vous utilisez la `+` (opérateur), vous peut-être pas en mesure de déterminer si la concaténation d’addition ou la chaîne aura lieu. Utilisez le `&` opérateur de concaténation pour éliminer toute ambiguïté et pour fournir un code auto-documenté.  
  
## <a name="overloading"></a>Surcharge  
 Le `+` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `+` pour ajouter des nombres. Si les opérandes sont tous numériques, Visual Basic calcule le résultat arithmétique. Le résultat arithmétique représente la somme des deux opérandes.  
  
 [!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]  
  
 Vous pouvez également utiliser le `+` pour concaténer des chaînes. Si les opérandes sont des chaînes, Visual Basic les concatène. Le résultat de concaténation représente une chaîne unique composée du contenu de deux opérandes l’un après l’autre.  
  
 Si les opérandes sont de types mixtes, le résultat dépend de la définition de la [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md). L’exemple suivant illustre le résultat lorsque `Option Strict` est `On`.  
  
 [!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]  
  
 L’exemple suivant illustre le résultat lorsque `Option Strict` est `Off`.  
  
 [!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]  
  
 Pour éliminer toute ambiguïté, vous devez utiliser le `&` opérateur à la place de `+` pour la concaténation.  
  
## <a name="see-also"></a>Voir aussi  
 [& (opérateur)](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [opérateur de concaténation](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Opérateurs arithmétiques en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)
