---
title: "How to: Declare A Constant (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.constant"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Integer data type, declaring constants"
  - "Single data type, declaring constants"
  - "Const statement [Visual Basic], declaring constants"
  - "procedures, declaration"
  - "data types [Visual Basic], constants"
  - "Long data type, declaring constants"
  - "Visual Basic code, declaring variables and constants"
  - "Double data type, declaring constants"
  - "Boolean data type, declaring constants"
  - "modules, declaring constants"
  - "Byte data type, declaring constants"
  - "constants, declaring"
  - "Date data type, declaring constants"
  - "String data type, declaring constants"
  - "declaring constants, const keyword"
  - "Currency data type, declaring constants and variants"
  - "module-level constants and variables"
  - "Object data type, declaring constants"
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# How to: Declare A Constant (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

L'instruction `Const` permet de déclarer une constante et de définir sa valeur.  En déclarant une constante, vous assignez un nom significatif à une valeur.  Une fois qu'une constante est déclarée, vous ne pouvez plus la modifier ou lui assigner une nouvelle valeur.  
  
 Vous déclarez une constante dans une procédure ou bien dans la section des déclarations d'un module, d'une classe ou d'une structure.  Les constantes de niveau classe ou structure sont `Private` par défaut, mais elles peuvent également être déclarées comme `Public`, `Friend`, `Protected` ou `Protected Friend` pour le niveau approprié d'accès au code.  
  
 La constante doit avoir un nom symbolique valide \(les règles sont identiques à celles permettant de créer des noms de variables\) et une expression composée de constantes et d'opérateurs numériques ou de type chaîne \(pas d'appels de fonction\).  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### Pour déclarer une constante  
  
-   Écrivez une déclaration qui inclut un spécificateur d'accès, le mot clé `Const` et une expression, comme illustré dans les exemples suivants :  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#8)]  
  
     Si [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) a la valeur `Off` et si [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) a la valeur `On`, vous devez déclarer explicitement une constante en spécifiant un type de données \(`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single` ou `String`\).  
  
     Si `Option Infer` a la valeur `On` ou si `Option Strict` a la valeur `Off`, vous pouvez déclarer une constante sans spécifier de type de données avec une clause `As`.  Le compilateur détermine le type de la constante à partir du type de l'expression.  Pour plus d'informations, consultez [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md).  
  
### Pour déclarer une constante qui possède un type de données indiqué explicitement  
  
-   Écrivez une déclaration qui inclut le mot clé `As` et un type de données explicite, comme illustré dans les exemples suivants :  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#9)]  
  
     Vous pouvez déclarer plusieurs constantes sur une même ligne, mais il est recommandé de ne déclarer qu'une seule constante par ligne pour simplifier la lisibilité du code.  Si vous déclarez plusieurs constantes sur une seule ligne, elles doivent toutes avoir le même niveau d'accès \(`Public`, `Private`, `Friend`, `Protected` ou `Protected Friend`\).  
  
### Pour déclarer plusieurs constantes sur une même ligne  
  
-   Séparez les déclarations par une virgule et un espace, comme dans l'exemple suivant :  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## Voir aussi  
 [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constants and Enumerations](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)