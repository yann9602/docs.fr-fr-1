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
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="416c7-102">Constantes et types de données littérales (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="416c7-102">Constant and Literal Data Types (Visual Basic)</span></span>
<span data-ttu-id="416c7-103">Un littéral est une valeur qui est exprimée comme elle-même plutôt que comme valeur d’une variable ou le résultat d’une expression, telles que le nombre 3 ou la chaîne « Hello ».</span><span class="sxs-lookup"><span data-stu-id="416c7-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="416c7-104">Une constante est un nom explicite qui prend la place d’un littéral et conserve cette même valeur tout au long du programme, par opposition à une variable dont la valeur peut changer.</span><span class="sxs-lookup"><span data-stu-id="416c7-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="416c7-105">Lorsque [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) est `Off` et [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) est `On`, vous devez déclarer explicitement toutes les constantes avec un type de données.</span><span class="sxs-lookup"><span data-stu-id="416c7-105">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="416c7-106">Dans l’exemple suivant, le type de données de `MyByte` est déclaré explicitement comme type de données `Byte`:</span><span class="sxs-lookup"><span data-stu-id="416c7-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 <span data-ttu-id="416c7-107">Lorsque `Option Infer` est `On` ou `Option Strict` est `Off`, vous pouvez déclarer une constante sans spécifier un type de données avec un `As` clause.</span><span class="sxs-lookup"><span data-stu-id="416c7-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="416c7-108">Le compilateur détermine le type de la constante du type de l’expression.</span><span class="sxs-lookup"><span data-stu-id="416c7-108">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="416c7-109">Un littéral entier numérique est effectué par défaut pour le `Integer` type de données.</span><span class="sxs-lookup"><span data-stu-id="416c7-109">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="416c7-110">Type de données par défaut pour les nombres à virgule flottante sont `Double`et les mots clés `True` et `False` spécifier un `Boolean` constante.</span><span class="sxs-lookup"><span data-stu-id="416c7-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="416c7-111">Les littéraux et contrainte de Type</span><span class="sxs-lookup"><span data-stu-id="416c7-111">Literals and Type Coercion</span></span>  
 <span data-ttu-id="416c7-112">Dans certains cas, vous souhaiterez forcer un littéral à un type de données particulier ; par exemple, lors de l’attribution d’une très grande valeur littérale intégrale à une variable de type `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="416c7-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="416c7-113">L’exemple suivant génère une erreur :</span><span class="sxs-lookup"><span data-stu-id="416c7-113">The following example produces an error:</span></span>  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="416c7-114">L’erreur produit de la représentation sous forme de littéral.</span><span class="sxs-lookup"><span data-stu-id="416c7-114">The error results from the representation of the literal.</span></span> <span data-ttu-id="416c7-115">Le `Decimal` type de données peut contenir une valeur de cette taille, mais le littéral est implicitement représenté comme un `Long`, qui ne peut pas.</span><span class="sxs-lookup"><span data-stu-id="416c7-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="416c7-116">Vous pouvez forcer un littéral à un type de données particulier de deux manières : en ajoutant un caractère de type à ce dernier, ou en le plaçant entre des caractères englobants.</span><span class="sxs-lookup"><span data-stu-id="416c7-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="416c7-117">Un caractère de type ou les caractères englobants doit immédiatement précéder et/ou suivre le littéral, sans espace intermédiaire ou les caractères de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="416c7-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="416c7-118">Pour que l’exemple précédent fonctionne, vous pouvez ajouter la `D` de type caractère au littéral, ce qui entraîne sa être représentée comme un `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="416c7-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 <span data-ttu-id="416c7-119">L’exemple suivant montre une utilisation correcte des caractères de type et des caractères englobants :</span><span class="sxs-lookup"><span data-stu-id="416c7-119">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 <span data-ttu-id="416c7-120">Le tableau suivant indique les caractères et le type englobant de caractères disponibles dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="416c7-120">The following table shows the enclosing characters and type characters available in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
|<span data-ttu-id="416c7-121">Type de données</span><span class="sxs-lookup"><span data-stu-id="416c7-121">Data type</span></span>|<span data-ttu-id="416c7-122">Caractère englobant</span><span class="sxs-lookup"><span data-stu-id="416c7-122">Enclosing character</span></span>|<span data-ttu-id="416c7-123">Caractère de type ajouté</span><span class="sxs-lookup"><span data-stu-id="416c7-123">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="416c7-124">(aucun)</span><span class="sxs-lookup"><span data-stu-id="416c7-124">(none)</span></span>|<span data-ttu-id="416c7-125">(aucun)</span><span class="sxs-lookup"><span data-stu-id="416c7-125">(none)</span></span>|  
|`Byte`|<span data-ttu-id="416c7-126">(aucun)</span><span class="sxs-lookup"><span data-stu-id="416c7-126">(none)</span></span>|<span data-ttu-id="416c7-127">(aucun)</span><span class="sxs-lookup"><span data-stu-id="416c7-127">(none)</span></span>|  
|`Char`|<span data-ttu-id="416c7-128">"</span><span class="sxs-lookup"><span data-stu-id="416c7-128">"</span></span>|<span data-ttu-id="416c7-129">C</span><span class="sxs-lookup"><span data-stu-id="416c7-129">C</span></span>|  
|`Date`|#|<span data-ttu-id="416c7-130">(aucun)</span><span class="sxs-lookup"><span data-stu-id="416c7-130">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="416c7-131">(aucun)</span><span class="sxs-lookup"><span data-stu-id="416c7-131">(none)</span></span>|<span data-ttu-id="416c7-132">D ou @</span><span class="sxs-lookup"><span data-stu-id="416c7-132">D or @</span></span>|  
|`Double`|<span data-ttu-id="416c7-133">(aucun)</span><span class="sxs-lookup"><span data-stu-id="416c7-133">(none)</span></span>|<span data-ttu-id="416c7-134">R ou #</span><span class="sxs-lookup"><span data-stu-id="416c7-134">R or #</span></span>|  
|`Integer`|<span data-ttu-id="416c7-135">(aucun)</span><span class="sxs-lookup"><span data-stu-id="416c7-135">(none)</span></span>|<span data-ttu-id="416c7-136">I ou %</span><span class="sxs-lookup"><span data-stu-id="416c7-136">I or %</span></span>|  
|`Long`|<span data-ttu-id="416c7-137">(aucun)</span><span class="sxs-lookup"><span data-stu-id="416c7-137">(none)</span></span>|<span data-ttu-id="416c7-138">L ou &</span><span class="sxs-lookup"><span data-stu-id="416c7-138">L or &</span></span>|  
|`Short`|<span data-ttu-id="416c7-139">(aucun)</span><span class="sxs-lookup"><span data-stu-id="416c7-139">(none)</span></span>|<span data-ttu-id="416c7-140">S</span><span class="sxs-lookup"><span data-stu-id="416c7-140">S</span></span>|  
|`Single`|<span data-ttu-id="416c7-141">(aucun)</span><span class="sxs-lookup"><span data-stu-id="416c7-141">(none)</span></span>|<span data-ttu-id="416c7-142">F ou !</span><span class="sxs-lookup"><span data-stu-id="416c7-142">F or !</span></span>|  
|`String`|<span data-ttu-id="416c7-143">"</span><span class="sxs-lookup"><span data-stu-id="416c7-143">"</span></span>|<span data-ttu-id="416c7-144">(aucun)</span><span class="sxs-lookup"><span data-stu-id="416c7-144">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="416c7-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="416c7-145">See Also</span></span>  
 [<span data-ttu-id="416c7-146">Constantes définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="416c7-146">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [<span data-ttu-id="416c7-147">Guide pratique : déclarer une constante</span><span class="sxs-lookup"><span data-stu-id="416c7-147">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [<span data-ttu-id="416c7-148">Vue d’ensemble des constantes</span><span class="sxs-lookup"><span data-stu-id="416c7-148">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="416c7-149">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="416c7-149">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="416c7-150">Option Explicit (instruction)</span><span class="sxs-lookup"><span data-stu-id="416c7-150">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="416c7-151">Vue d’ensemble des énumérations</span><span class="sxs-lookup"><span data-stu-id="416c7-151">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="416c7-152">Comment : déclarer une énumération</span><span class="sxs-lookup"><span data-stu-id="416c7-152">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="416c7-153">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="416c7-153">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="416c7-154">Types de données</span><span class="sxs-lookup"><span data-stu-id="416c7-154">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="416c7-155">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="416c7-155">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
