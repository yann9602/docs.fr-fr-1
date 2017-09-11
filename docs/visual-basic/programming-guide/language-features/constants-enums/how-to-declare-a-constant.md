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
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: b7fc499336c2b5db3b4d2fe9c0cd11799ea0ad77
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="de63c-102">Comment : déclarer une constante (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de63c-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="de63c-103">Vous utilisez la `Const` instruction pour déclarer une constante et définir sa valeur.</span><span class="sxs-lookup"><span data-stu-id="de63c-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="de63c-104">En déclarant une constante, vous affectez un nom significatif à une valeur.</span><span class="sxs-lookup"><span data-stu-id="de63c-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="de63c-105">Une fois qu’une constante est déclarée, elle ne peut pas être modifiée ou attribuer une nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="de63c-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="de63c-106">Vous déclarez une constante dans une procédure ou dans la section des déclarations d’un module, classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="de63c-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="de63c-107">Une ou plusieurs constantes au niveau de la structure sont `Private` par défaut, mais peuvent également être déclarées comme `Public`, `Friend`, `Protected`, ou `Protected Friend` pour le niveau approprié d’accès au code.</span><span class="sxs-lookup"><span data-stu-id="de63c-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="de63c-108">La constante doit avoir un nom symbolique valid (les règles sont les mêmes que celles permettant de créer des noms de variable) et une expression composée de numérique ou chaîne de constantes et opérateurs (mais aucun appel de fonction).</span><span class="sxs-lookup"><span data-stu-id="de63c-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="de63c-109">Pour déclarer une constante</span><span class="sxs-lookup"><span data-stu-id="de63c-109">To declare a constant</span></span>  
  
-   <span data-ttu-id="de63c-110">Écrivez une déclaration qui inclut un spécificateur d’accès, le `Const` (mot clé) et une expression, comme dans les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="de63c-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     <span data-ttu-id="de63c-111">[!code-vb[VbEnumsTask n °&8;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="de63c-111">[!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]</span></span>  
  
     <span data-ttu-id="de63c-112">Lors de la [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) est `Off` et [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) est `On`, vous devez déclarer explicitement une constante en spécifiant un type de données (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, ou `String`).</span><span class="sxs-lookup"><span data-stu-id="de63c-112">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="de63c-113">Lors de la `Option Infer` est `On` ou `Option Strict` est `Off`, vous pouvez déclarer une constante sans spécifier un type de données avec un `As` clause.</span><span class="sxs-lookup"><span data-stu-id="de63c-113">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="de63c-114">Le compilateur détermine le type de la constante du type de l’expression.</span><span class="sxs-lookup"><span data-stu-id="de63c-114">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="de63c-115">Pour plus d’informations, consultez [constante et des Types de données littérales](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="de63c-115">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="de63c-116">Pour déclarer une constante qui possède un type de données indiqué explicitement</span><span class="sxs-lookup"><span data-stu-id="de63c-116">To declare a constant that has an explicitly stated data type</span></span>  
  
-   <span data-ttu-id="de63c-117">Écrivez une déclaration qui inclut le `As` (mot clé) et une explicites type de données, comme dans les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="de63c-117">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     <span data-ttu-id="de63c-118">[!code-vb[VbEnumsTask&#9;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="de63c-118">[!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]</span></span>  
  
     <span data-ttu-id="de63c-119">Vous pouvez déclarer plusieurs constantes sur une seule ligne, même si votre code est plus lisible si vous ne déclarez qu’une seule constante par ligne.</span><span class="sxs-lookup"><span data-stu-id="de63c-119">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="de63c-120">Si vous déclarez plusieurs constantes sur une seule ligne, elles doivent toutes avoir le même niveau d’accès (`Public`, `Private`, `Friend`, `Protected`, ou `Protected Friend`).</span><span class="sxs-lookup"><span data-stu-id="de63c-120">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="de63c-121">Pour déclarer plusieurs constantes sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="de63c-121">To declare multiple constants on a single line</span></span>  
  
-   <span data-ttu-id="de63c-122">Séparez les déclarations par une virgule et un espace, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="de63c-122">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="de63c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de63c-123">See Also</span></span>  
 <span data-ttu-id="de63c-124">[Const (instruction)](../../../../visual-basic/language-reference/statements/const-statement.md) </span><span class="sxs-lookup"><span data-stu-id="de63c-124">[Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) </span></span>  
<span data-ttu-id="de63c-125"> [Types de données littéraux et constantes](constant-and-literal-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="de63c-125"> [Constant and Literal Data Types](constant-and-literal-data-types.md) </span></span>  
<span data-ttu-id="de63c-126"> [Vue d’ensemble des constantes](constants-overview.md)
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
 [quand utiliser une énumération](when-to-use-an-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="de63c-126"> [Constants Overview](constants-overview.md)
 [How to: Declare A Constant](how-to-declare-a-constant.md)
 [User-Defined Constants](user-defined-constants.md)
 [Constant and Literal Data Types](constant-and-literal-data-types.md)
 [How to: Group Related Constant Values Together](how-to-group-related-constant-values-together.md)
 [Enumerations Overview](enumerations-overview.md)
 [How to: Declare Enumerations](how-to-declare-enumerations.md)
 [How to: Refer to an Enumeration Member](how-to-refer-to-an-enumeration-member.md)
 [Enumerations and Name Qualification](enumerations-and-name-qualification.md)
 [How to: Iterate Through An Enumeration](how-to-iterate-through-an-enumeration.md)
 [How to: Determine the String Associated with an Enumeration Value](how-to-determine-the-string-associated-with-an-enumeration-value.md)
 [When to Use an Enumeration](when-to-use-an-enumeration.md)</span></span>

 <span data-ttu-id="de63c-127">[Vue d’ensemble des énumérations](enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="de63c-127">[Enumerations Overview](enumerations-overview.md) </span></span>  
<span data-ttu-id="de63c-128"> [Vue d’ensemble des constantes](constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="de63c-128"> [Constants Overview](constants-overview.md) </span></span>  
<span data-ttu-id="de63c-129"> [Comment : déclarer une énumération](how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="de63c-129"> [How to: Declare an Enumeration](how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="de63c-130"> [Énumérations et Qualification de noms](enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="de63c-130"> [Enumerations and Name Qualification](enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="de63c-131"> [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="de63c-131"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="de63c-132"> [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="de63c-132"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>

