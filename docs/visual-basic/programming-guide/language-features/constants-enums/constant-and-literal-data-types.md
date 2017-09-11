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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 29a997ee0dd847e8505d1a5c24cacfdfdb0a42cc
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="c0698-102">Constantes et types de données littérales (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0698-102">Constant and Literal Data Types (Visual Basic)</span></span>
<span data-ttu-id="c0698-103">Un littéral est une valeur qui est exprimée comme elle-même plutôt que comme valeur d’une variable ou le résultat d’une expression, comme le nombre 3 ou la chaîne « Hello ».</span><span class="sxs-lookup"><span data-stu-id="c0698-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="c0698-104">Une constante est un nom significatif qui prend la place d’un littéral et conserve cette même valeur tout au long du programme, par opposition à une variable, dont la valeur peut changer.</span><span class="sxs-lookup"><span data-stu-id="c0698-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="c0698-105">Lors de la [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) est `Off` et [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) est `On`, vous devez déclarer toutes les constantes explicitement avec un type de données.</span><span class="sxs-lookup"><span data-stu-id="c0698-105">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="c0698-106">Dans l’exemple suivant, le type de données `MyByte` est déclaré explicitement comme type de données `Byte`:</span><span class="sxs-lookup"><span data-stu-id="c0698-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 <span data-ttu-id="c0698-107">[!code-vb[VbVbalrConstants n °&1;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c0698-107">[!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]</span></span>  
  
 <span data-ttu-id="c0698-108">Lors de la `Option Infer` est `On` ou `Option Strict` est `Off`, vous pouvez déclarer une constante sans spécifier un type de données avec un `As` clause.</span><span class="sxs-lookup"><span data-stu-id="c0698-108">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="c0698-109">Le compilateur détermine le type de la constante du type de l’expression.</span><span class="sxs-lookup"><span data-stu-id="c0698-109">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="c0698-110">Un littéral entier numérique est effectué par défaut à la `Integer` type de données.</span><span class="sxs-lookup"><span data-stu-id="c0698-110">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="c0698-111">Le type par défaut pour les nombres à virgule flottante sont `Double`et les mots clés `True` et `False` spécifier un `Boolean` constante.</span><span class="sxs-lookup"><span data-stu-id="c0698-111">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="c0698-112">Littéraux et contrainte de Type</span><span class="sxs-lookup"><span data-stu-id="c0698-112">Literals and Type Coercion</span></span>  
 <span data-ttu-id="c0698-113">Dans certains cas, vous pouvez souhaiter forcer un littéral à un type de données particulier ; par exemple, lorsque vous affectez une très grande valeur littérale intégrale à une variable de type `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c0698-113">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="c0698-114">L’exemple suivant génère une erreur :</span><span class="sxs-lookup"><span data-stu-id="c0698-114">The following example produces an error:</span></span>  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="c0698-115">L’erreur provoque de la représentation du littéral.</span><span class="sxs-lookup"><span data-stu-id="c0698-115">The error results from the representation of the literal.</span></span> <span data-ttu-id="c0698-116">Le `Decimal` type de données peut contenir une valeur de cette taille, mais le littéral est implicitement représenté comme un `Long`, qui ne peut pas.</span><span class="sxs-lookup"><span data-stu-id="c0698-116">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="c0698-117">Vous pouvez forcer un littéral en un type de données particulier de deux manières : en ajoutant un caractère de type à celui-ci, ou en le plaçant entre des caractères englobants.</span><span class="sxs-lookup"><span data-stu-id="c0698-117">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="c0698-118">Un caractère de type ou des caractères englobants doivent immédiatement précéder et/ou suivre le littéral, sans espace intermédiaire ou les caractères de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="c0698-118">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="c0698-119">Pour que l’exemple précédent fonctionne, vous pouvez ajouter la `D` type caractère littéral, de sorte qu’il être représentée comme un `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="c0698-119">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 <span data-ttu-id="c0698-120">[!code-vb[VbVbalrConstants n °&2;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c0698-120">[!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]</span></span>  
  
 <span data-ttu-id="c0698-121">L’exemple suivant montre l’utilisation des caractères de type et des caractères englobants :</span><span class="sxs-lookup"><span data-stu-id="c0698-121">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 <span data-ttu-id="c0698-122">[!code-vb[VbVbalrConstants n °&3;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="c0698-122">[!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]</span></span>  
  
 <span data-ttu-id="c0698-123">Le tableau suivant répertorie les caractères et le type englobant caractères disponibles dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0698-123">The following table shows the enclosing characters and type characters available in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
|<span data-ttu-id="c0698-124">Type de données</span><span class="sxs-lookup"><span data-stu-id="c0698-124">Data type</span></span>|<span data-ttu-id="c0698-125">Caractère englobant</span><span class="sxs-lookup"><span data-stu-id="c0698-125">Enclosing character</span></span>|<span data-ttu-id="c0698-126">Caractère de type ajouté</span><span class="sxs-lookup"><span data-stu-id="c0698-126">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="c0698-127">(aucun)</span><span class="sxs-lookup"><span data-stu-id="c0698-127">(none)</span></span>|<span data-ttu-id="c0698-128">(aucun)</span><span class="sxs-lookup"><span data-stu-id="c0698-128">(none)</span></span>|  
|`Byte`|<span data-ttu-id="c0698-129">(aucun)</span><span class="sxs-lookup"><span data-stu-id="c0698-129">(none)</span></span>|<span data-ttu-id="c0698-130">(aucun)</span><span class="sxs-lookup"><span data-stu-id="c0698-130">(none)</span></span>|  
|`Char`|<span data-ttu-id="c0698-131">"</span><span class="sxs-lookup"><span data-stu-id="c0698-131">"</span></span>|<span data-ttu-id="c0698-132">C</span><span class="sxs-lookup"><span data-stu-id="c0698-132">C</span></span>|  
|`Date`|#|<span data-ttu-id="c0698-133">(aucun)</span><span class="sxs-lookup"><span data-stu-id="c0698-133">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="c0698-134">(aucun)</span><span class="sxs-lookup"><span data-stu-id="c0698-134">(none)</span></span>|<span data-ttu-id="c0698-135">D ou @</span><span class="sxs-lookup"><span data-stu-id="c0698-135">D or @</span></span>|  
|`Double`|<span data-ttu-id="c0698-136">(aucun)</span><span class="sxs-lookup"><span data-stu-id="c0698-136">(none)</span></span>|<span data-ttu-id="c0698-137">R ou</span><span class="sxs-lookup"><span data-stu-id="c0698-137">R or</span></span> #|  
|`Integer`|<span data-ttu-id="c0698-138">(aucun)</span><span class="sxs-lookup"><span data-stu-id="c0698-138">(none)</span></span>|<span data-ttu-id="c0698-139">I ou %</span><span class="sxs-lookup"><span data-stu-id="c0698-139">I or %</span></span>|  
|`Long`|<span data-ttu-id="c0698-140">(aucun)</span><span class="sxs-lookup"><span data-stu-id="c0698-140">(none)</span></span>|<span data-ttu-id="c0698-141">L ou se</span><span class="sxs-lookup"><span data-stu-id="c0698-141">L or &</span></span>|  
|`Short`|<span data-ttu-id="c0698-142">(aucun)</span><span class="sxs-lookup"><span data-stu-id="c0698-142">(none)</span></span>|<span data-ttu-id="c0698-143">S</span><span class="sxs-lookup"><span data-stu-id="c0698-143">S</span></span>|  
|`Single`|<span data-ttu-id="c0698-144">(aucun)</span><span class="sxs-lookup"><span data-stu-id="c0698-144">(none)</span></span>|<span data-ttu-id="c0698-145">F ou !</span><span class="sxs-lookup"><span data-stu-id="c0698-145">F or !</span></span>|  
|`String`|<span data-ttu-id="c0698-146">"</span><span class="sxs-lookup"><span data-stu-id="c0698-146">"</span></span>|<span data-ttu-id="c0698-147">(aucun)</span><span class="sxs-lookup"><span data-stu-id="c0698-147">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0698-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0698-148">See Also</span></span>  
 <span data-ttu-id="c0698-149">[Constantes définies par l’utilisateur](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md) </span><span class="sxs-lookup"><span data-stu-id="c0698-149">[User-Defined Constants](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md) </span></span>  
<span data-ttu-id="c0698-150"> [Comment : déclarer une constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md) </span><span class="sxs-lookup"><span data-stu-id="c0698-150"> [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md) </span></span>  
<span data-ttu-id="c0698-151"> [Vue d’ensemble des constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="c0698-151"> [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span></span>  
<span data-ttu-id="c0698-152"> [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c0698-152"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="c0698-153"> [Option Explicit, instruction](../../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c0698-153"> [Option Explicit Statement](../../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="c0698-154"> [Vue d’ensemble des énumérations](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="c0698-154"> [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span></span>  
<span data-ttu-id="c0698-155"> [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="c0698-155"> [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="c0698-156"> [Énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="c0698-156"> [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="c0698-157"> [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="c0698-157"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="c0698-158"> [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="c0698-158"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>
