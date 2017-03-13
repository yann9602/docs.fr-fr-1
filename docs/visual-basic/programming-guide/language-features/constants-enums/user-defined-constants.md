---
title: "User-Defined Constants (Visual Basic) | Microsoft Docs"
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
  - "constants, circular references"
  - "Const statement [Visual Basic], user-defined constants"
  - "user-defined constants"
  - "scope, constants"
  - "constants, user-defined"
  - "circular references between constants"
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# User-Defined Constants (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Une constante est un nom significatif qui symbolise un nombre ou une chaîne invariable.  Les constantes stockent des valeurs qui, comme leur nom l'indique, demeurent constantes lors de l'exécution d'une application.  Vous pouvez utiliser des constantes qui sont définies par les contrôles ou les composants que vous utilisez ; vous pouvez également créer vos propres constantes.  Les constantes que vous créez sont appelées des constantes *définies par l'utilisateur*.  
  
 Vous déclarez une constante par l'instruction `Const`, en utilisant les mêmes indications que celles permettant de créer un nom de variable.  Si `Option Strict` est `On`, vous devez déclarer le type de constante de manière explicite.  
  
## Utilisation de l'instruction Const  
 Une instruction `Const` peut représenter une valeur mathématique ou de date\/heure :  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 Elle peut également définir des constantes `String` :  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 L'expression à la droite du signe égal \(`=`\) est souvent un nombre ou une chaîne littérale, mais elle peut également être une expression dont le résultat est un nombre ou une chaîne \(même si cette expression ne peut pas contenir d'appels à des fonctions\).  Vous pouvez également définir des constantes en termes de constantes définies préalablement :  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## Portée des constantes définies par l'utilisateur  
 La portée d'une instruction `Const` est identique à celle d'une variable déclarée au même emplacement.  Vous pouvez spécifier la portée de l'une des façons suivantes :  
  
-   Pour créer une constante existant uniquement dans une procédure, vous devez la déclarer dans cette procédure.  
  
-   Pour créer une constante qui soit disponible pour toutes les procédures d'une classe, mais pas pour le code en dehors du module, vous devez la déclarer dans la section des déclarations de la classe.  
  
-   Pour créer une constante qui soit disponible pour tous les membres d'un assembly, mais pas pour les clients externes de cet assembly, vous devez la déclarer à l'aide du mot clé `Friend` dans la section des déclarations de la classe.  
  
-   Pour créer une constante qui soit disponible pour l'ensemble de l'application, vous devez la déclarer à l'aide du mot clé `Public` dans la section des déclarations de la classe.  
  
 Pour plus d'informations, consultez [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).  
  
### Comment éviter des références circulaires  
 Dans la mesure où les constantes peuvent être définies en termes d'autres constantes, le risque est de créer un *cycle* \(ou une référence circulaire\) par inadvertance entre deux constantes ou plus.  Un cycle se produit en présence d'au moins deux constantes publiques \(Public\), chacune étant définie par rapport à l'autre, comme illustré dans cet exemple :  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 Lorsqu'un cycle se produit, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] génère une erreur de compilateur.  
  
## Voir aussi  
 [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constants and Enumerations](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)