---
title: "Constant and Literal Data Types (Visual Basic) | Microsoft Docs"
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
  - "declaring constants, literal data types"
  - "data types [Visual Basic], declaring"
  - "constants, declaring"
  - "explicit declarations"
  - "literals, coercing data type"
  - "declarations, data types"
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Constant and Literal Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Un littéral est une valeur qui est exprimée comme elle\-même plutôt que comme la valeur d'une variable ou le résultat d'une expression, tel que le nombre 3 ou la chaîne "Hello".  Une constante est un nom significatif qui prend la place d'un littéral et conserve cette même valeur partout dans le programme, par opposition à une variable dont la valeur peut se modifier.  
  
 Si [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) a la valeur `Off` et si [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) a la valeur `On`, vous devez déclarer toutes les constantes explicitement avec un type de données.  Dans l'exemple suivant, le type de données de `MyByte` est déclaré explicitement comme type de données `Byte` :  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/visualbasic/constant-and-literal-dat_1.vb)]  
  
 Si `Option Infer` a la valeur `On` ou si `Option Strict` a la valeur `Off`, vous pouvez déclarer une constante sans spécifier de type de données avec une clause `As`.  Le compilateur détermine le type de la constante à partir du type de l'expression.  Par défaut, un littéral entier numérique est casté en un type de données `Integer`.  Le type de données par défaut des nombres à virgule flottante est `Double`, et les mots clés `True` et `False` spécifient une constante `Boolean`.  
  
## Littéraux et contrainte de type  
 Il arrive parfois que vous vouliez forcer un littéral en un type de données particulier ; par exemple, lors de l'assignation d'une très grande valeur littérale intégrale à une variable de type `Decimal`.  L'exemple suivant génère une erreur :  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 L'erreur provient de la représentation du littéral.  Le type de données `Decimal` peut avoir une valeur de cette taille, mais le littéral est implicitement représenté comme un type `Long` qui ne peut pas contenir une telle valeur.  
  
 Vous pouvez forcer un littéral en un type de données particulier de deux façons : en lui ajoutant un caractère de type ou en le plaçant entre des caractères englobants.  Un caractère de type ou des caractères englobants doivent immédiatement précéder et\/ou suivre le littéral \(aucun autre caractère ou espace ne doit venir s'interposer\).  
  
 Pour que l'exemple précédent fonctionne, vous devez ajouter au littéral le caractère de type `D`, de sorte qu'il soit représenté en tant que type `Decimal` :  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/visualbasic/constant-and-literal-dat_2.vb)]  
  
 L'exemple suivant illustre l'utilisation correcte des caractères de type et des caractères englobants :  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/visualbasic/constant-and-literal-dat_3.vb)]  
  
 Le tableau suivant répertorie les caractères englobants et les caractères de type disponibles dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
||||  
|-|-|-|  
|Type de données|Caractère englobant|Caractère de type ajouté|  
|`Boolean`|\(aucun\)|\(aucun\)|  
|`Byte`|\(aucun\)|\(aucun\)|  
|`Char`|"|C|  
|`Date`|\#|\(aucun\)|  
|`Decimal`|\(aucun\)|D ou @|  
|`Double`|\(aucun\)|R ou \#|  
|`Integer`|\(aucun\)|I ou %|  
|`Long`|\(aucun\)|L ou &|  
|`Short`|\(aucun\)|S|  
|`Single`|\(aucun\)|F ou \!|  
|`String`|"|\(aucun\)|  
  
## Voir aussi  
 [User\-Defined Constants](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)   
 [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)   
 [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Option Explicit Statement](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)