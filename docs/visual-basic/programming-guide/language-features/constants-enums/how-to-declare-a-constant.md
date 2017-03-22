---
title: "Comment : déclarer une constante (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.constant
dev_langs:
- VB
helpviewer_keywords:
- Integer data type, declaring constants
- Single data type, declaring constants
- Const statement [Visual Basic], declaring constants
- procedures, declaration
- data types [Visual Basic], constants
- Long data type, declaring constants
- Visual Basic code, declaring variables and constants
- Double data type, declaring constants
- Boolean data type, declaring constants
- modules, declaring constants
- Byte data type, declaring constants
- constants, declaring
- Date data type, declaring constants
- String data type, declaring constants
- declaring constants, const keyword
- Currency data type, declaring constants and variants
- module-level constants and variables
- Object data type, declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
caps.latest.revision: 20
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
ms.openlocfilehash: 401d0feb85fccf94a25308d38c3c75198ef9294c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-a-constant-visual-basic"></a>Comment : déclarer une constante (Visual Basic)
Vous utilisez la `Const` instruction pour déclarer une constante et définir sa valeur. En déclarant une constante, vous affectez un nom significatif à une valeur. Une fois qu’une constante est déclarée, elle ne peut pas être modifiée ou attribuer une nouvelle valeur.  
  
 Vous déclarez une constante dans une procédure ou dans la section des déclarations d’un module, classe ou structure. Une ou plusieurs constantes au niveau de la structure sont `Private` par défaut, mais peuvent également être déclarées comme `Public`, `Friend`, `Protected`, ou `Protected Friend` pour le niveau approprié d’accès au code.  
  
 La constante doit avoir un nom symbolique valid (les règles sont les mêmes que celles permettant de créer des noms de variable) et une expression composée de numérique ou chaîne de constantes et opérateurs (mais aucun appel de fonction).  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-declare-a-constant"></a>Pour déclarer une constante  
  
-   Écrivez une déclaration qui inclut un spécificateur d’accès, le `Const` (mot clé) et une expression, comme dans les exemples suivants :  
  
     [!code-vb[VbEnumsTask n °&8;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     Lors de la [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) est `Off` et [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) est `On`, vous devez déclarer explicitement une constante en spécifiant un type de données (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, ou `String`).  
  
     Lors de la `Option Infer` est `On` ou `Option Strict` est `Off`, vous pouvez déclarer une constante sans spécifier un type de données avec un `As` clause. Le compilateur détermine le type de la constante du type de l’expression. Pour plus d’informations, consultez [constante et des Types de données littérales](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>Pour déclarer une constante qui possède un type de données indiqué explicitement  
  
-   Écrivez une déclaration qui inclut le `As` (mot clé) et une explicites type de données, comme dans les exemples suivants :  
  
     [!code-vb[VbEnumsTask&#9;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     Vous pouvez déclarer plusieurs constantes sur une seule ligne, même si votre code est plus lisible si vous ne déclarez qu’une seule constante par ligne. Si vous déclarez plusieurs constantes sur une seule ligne, elles doivent toutes avoir le même niveau d’accès (`Public`, `Private`, `Friend`, `Protected`, ou `Protected Friend`).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>Pour déclarer plusieurs constantes sur une seule ligne  
  
-   Séparez les déclarations par une virgule et un espace, comme dans l’exemple suivant :  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Const (instruction)](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [Types de données littéraux et constantes](constant-and-literal-data-types.md)   
 [Vue d’ensemble des constantes](constants-overview.md)
 [Comment : déclarer une constante](how-to-declare-a-constant.md)
 [constantes définies par l’utilisateur](user-defined-constants.md)
 [des Types de données littéraux et constantes](constant-and-literal-data-types.md)
 [Comment : regrouper les valeurs de constante connexes](how-to-group-related-constant-values-together.md)
 [vue d’ensemble des énumérations](enumerations-overview.md)
 [Comment : déclarer des énumérations](how-to-declare-enumerations.md)
 [Comment : faire référence à un membre d’énumération](how-to-refer-to-an-enumeration-member.md)
 [énumérations et Qualification de noms](enumerations-and-name-qualification.md)
 [Comment : parcourir une énumération](how-to-iterate-through-an-enumeration.md)
 [Comment : déterminer la chaîne Associé à une valeur d’énumération](how-to-determine-the-string-associated-with-an-enumeration-value.md)
 [quand utiliser une énumération](when-to-use-an-enumeration.md)

 [Vue d’ensemble des énumérations](enumerations-overview.md)   
 [Vue d’ensemble des constantes](constants-overview.md)   
 [Comment : déclarer une énumération](how-to-declare-enumerations.md)   
 [Énumérations et Qualification de noms](enumerations-and-name-qualification.md)   
 [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)

