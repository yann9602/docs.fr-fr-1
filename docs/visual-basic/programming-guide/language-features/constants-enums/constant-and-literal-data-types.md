---
title: "Types de données littéraux et constantes (Visual Basic) | Documents Microsoft"
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
- declaring constants, literal data types
- data types [Visual Basic], declaring
- constants, declaring
- explicit declarations
- literals, coercing data type
- declarations, data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 22ad31415ab560b7fd0180a6dadd6d2dcd7ec77a
ms.lasthandoff: 03/13/2017

---
# <a name="constant-and-literal-data-types-visual-basic"></a>Constantes et types de données littérales (Visual Basic)
Un littéral est une valeur qui est exprimée comme elle-même plutôt que comme valeur d’une variable ou le résultat d’une expression, comme le nombre 3 ou la chaîne « Hello ». Une constante est un nom significatif qui prend la place d’un littéral et conserve cette même valeur tout au long du programme, par opposition à une variable, dont la valeur peut changer.  
  
 Lors de la [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) est `Off` et [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) est `On`, vous devez déclarer toutes les constantes explicitement avec un type de données. Dans l’exemple suivant, le type de données `MyByte` est déclaré explicitement comme type de données `Byte`:  
  
 [!code-vb[VbVbalrConstants n °&1;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 Lors de la `Option Infer` est `On` ou `Option Strict` est `Off`, vous pouvez déclarer une constante sans spécifier un type de données avec un `As` clause. Le compilateur détermine le type de la constante du type de l’expression. Un littéral entier numérique est effectué par défaut à la `Integer` type de données. Le type par défaut pour les nombres à virgule flottante sont `Double`et les mots clés `True` et `False` spécifier un `Boolean` constante.  
  
## <a name="literals-and-type-coercion"></a>Littéraux et contrainte de Type  
 Dans certains cas, vous pouvez souhaiter forcer un littéral à un type de données particulier ; par exemple, lorsque vous affectez une très grande valeur littérale intégrale à une variable de type `Decimal`. L’exemple suivant génère une erreur :  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 L’erreur provoque de la représentation du littéral. Le `Decimal` type de données peut contenir une valeur de cette taille, mais le littéral est implicitement représenté comme un `Long`, qui ne peut pas.  
  
 Vous pouvez forcer un littéral en un type de données particulier de deux manières : en ajoutant un caractère de type à celui-ci, ou en le plaçant entre des caractères englobants. Un caractère de type ou des caractères englobants doivent immédiatement précéder et/ou suivre le littéral, sans espace intermédiaire ou les caractères de n’importe quel type.  
  
 Pour que l’exemple précédent fonctionne, vous pouvez ajouter la `D` type caractère littéral, de sorte qu’il être représentée comme un `Decimal`:  
  
 [!code-vb[VbVbalrConstants n °&2;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 L’exemple suivant montre l’utilisation des caractères de type et des caractères englobants :  
  
 [!code-vb[VbVbalrConstants n °&3;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 Le tableau suivant répertorie les caractères et le type englobant caractères disponibles dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
|Type de données|Caractère englobant|Caractère de type ajouté|  
|---|---|---|  
|`Boolean`|(aucun)|(aucun)|  
|`Byte`|(aucun)|(aucun)|  
|`Char`|"|C|  
|`Date`|#|(aucun)|  
|`Decimal`|(aucun)|D ou @|  
|`Double`|(aucun)|R ou #|  
|`Integer`|(aucun)|I ou %|  
|`Long`|(aucun)|L ou se|  
|`Short`|(aucun)|S|  
|`Single`|(aucun)|F ou !|  
|`String`|"|(aucun)|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes définies par l’utilisateur](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)   
 [Comment : déclarer une constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)   
 [Vue d’ensemble des constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Option Explicit, instruction](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Vue d’ensemble des énumérations](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)
