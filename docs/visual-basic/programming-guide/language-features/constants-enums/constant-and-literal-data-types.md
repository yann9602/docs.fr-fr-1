---
title: "Constantes et types de données littérales (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 554753e26d185593ce43b741b3b2f9e3cb1ad6dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Constantes et types de données littérales (Visual Basic)
Un littéral est une valeur qui est exprimée comme elle-même plutôt que comme valeur d’une variable ou le résultat d’une expression, telles que le nombre 3 ou la chaîne « Hello ». Une constante est un nom explicite qui prend la place d’un littéral et conserve cette même valeur tout au long du programme, par opposition à une variable dont la valeur peut changer.  
  
 Lorsque [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) est `Off` et [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) est `On`, vous devez déclarer explicitement toutes les constantes avec un type de données. Dans l’exemple suivant, le type de données de `MyByte` est déclaré explicitement comme type de données `Byte`:  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 Lorsque `Option Infer` est `On` ou `Option Strict` est `Off`, vous pouvez déclarer une constante sans spécifier un type de données avec un `As` clause. Le compilateur détermine le type de la constante du type de l’expression. Un littéral entier numérique est effectué par défaut pour le `Integer` type de données. Type de données par défaut pour les nombres à virgule flottante sont `Double`et les mots clés `True` et `False` spécifier un `Boolean` constante.  
  
## <a name="literals-and-type-coercion"></a>Les littéraux et contrainte de Type  
 Dans certains cas, vous souhaiterez forcer un littéral à un type de données particulier ; par exemple, lors de l’attribution d’une très grande valeur littérale intégrale à une variable de type `Decimal`. L’exemple suivant génère une erreur :  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 L’erreur produit de la représentation sous forme de littéral. Le `Decimal` type de données peut contenir une valeur de cette taille, mais le littéral est implicitement représenté comme un `Long`, qui ne peut pas.  
  
 Vous pouvez forcer un littéral à un type de données particulier de deux manières : en ajoutant un caractère de type à ce dernier, ou en le plaçant entre des caractères englobants. Un caractère de type ou les caractères englobants doit immédiatement précéder et/ou suivre le littéral, sans espace intermédiaire ou les caractères de n’importe quel type.  
  
 Pour que l’exemple précédent fonctionne, vous pouvez ajouter la `D` de type caractère au littéral, ce qui entraîne sa être représentée comme un `Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 L’exemple suivant montre une utilisation correcte des caractères de type et des caractères englobants :  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 Le tableau suivant indique les caractères et le type englobant de caractères disponibles dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
|Type de données|Caractère englobant|Caractère de type ajouté|  
|---|---|---|  
|`Boolean`|(aucun)|(aucun)|  
|`Byte`|(aucun)|(aucun)|  
|`Char`|"|C|  
|`Date`|#|(aucun)|  
|`Decimal`|(aucun)|D ou @|  
|`Double`|(aucun)|R ou #|  
|`Integer`|(aucun)|I ou %|  
|`Long`|(aucun)|L ou &|  
|`Short`|(aucun)|S|  
|`Single`|(aucun)|F ou !|  
|`String`|"|(aucun)|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes définies par l’utilisateur](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [Guide pratique : déclarer une constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [Vue d’ensemble des constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Option Explicit (instruction)](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Vue d’ensemble des énumérations](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Énumérations et qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)
