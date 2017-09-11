---
title: "Caractères spéciaux dans le Code (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
dev_langs:
- VB
helpviewer_keywords:
- special characters, in code
- parentheses, using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator
- concatenation operators, special characters in code
- concatenation operators, vs. addition operator
- '! operator'
- separators, using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator
- addition operator
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
caps.latest.revision: 21
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
ms.openlocfilehash: cd7fbce5c382c3acd88a12277a3d7899b823d049
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="97d62-102">Caractères spéciaux dans le code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97d62-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="97d62-103">Parfois, vous devez utiliser des caractères spéciaux dans votre code, autrement dit, les caractères qui ne sont pas alphabétiques ou numériques.</span><span class="sxs-lookup"><span data-stu-id="97d62-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="97d62-104">Les signes de ponctuation et caractères spéciaux dans le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] jeu de caractères ont plusieurs utilisations, de l’organisation du texte de programme à la définition des tâches effectuées par le compilateur ou le programme compilé.</span><span class="sxs-lookup"><span data-stu-id="97d62-104">The punctuation and special characters in the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="97d62-105">Ils ne spécifient pas d'opération à effectuer.</span><span class="sxs-lookup"><span data-stu-id="97d62-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="97d62-106">Entre parenthèses</span><span class="sxs-lookup"><span data-stu-id="97d62-106">Parentheses</span></span>  
 <span data-ttu-id="97d62-107">Utilisez des parenthèses lorsque vous définissez une procédure, comme un `Sub` ou `Function`.</span><span class="sxs-lookup"><span data-stu-id="97d62-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="97d62-108">Vous devez placer toutes les listes d’arguments de procédure entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="97d62-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="97d62-109">Vous également utiliser des parenthèses pour insérer des variables ou arguments en groupes logiques, en particulier pour substituer l’ordre de priorité des opérateurs dans une expression complexe par défaut.</span><span class="sxs-lookup"><span data-stu-id="97d62-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="97d62-110">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="97d62-110">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="97d62-111">[!code-vb[VbVbcnConventions&#11;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="97d62-111">[!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]</span></span>  
  
 <span data-ttu-id="97d62-112">Après l’exécution du code précédent, la valeur de `d` est 8.225 et la valeur de `e` est 3.</span><span class="sxs-lookup"><span data-stu-id="97d62-112">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="97d62-113">Le calcul de `d` utilise la priorité par défaut de `/` sur `+` et équivaut à `d = b + (c / a)`.</span><span class="sxs-lookup"><span data-stu-id="97d62-113">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="97d62-114">Les parenthèses dans le calcul de `e` la priorité par défaut.</span><span class="sxs-lookup"><span data-stu-id="97d62-114">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="97d62-115">Séparateurs</span><span class="sxs-lookup"><span data-stu-id="97d62-115">Separators</span></span>  
 <span data-ttu-id="97d62-116">Séparateurs de faire ce que leur nom suggère : séparent les différentes sections de code.</span><span class="sxs-lookup"><span data-stu-id="97d62-116">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="97d62-117">Dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], le caractère de séparation est le signe deux-points (`:`).</span><span class="sxs-lookup"><span data-stu-id="97d62-117">In [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], the separator character is the colon (`:`).</span></span> <span data-ttu-id="97d62-118">Utilisez des séparateurs lorsque vous voulez inclure plusieurs instructions sur une seule ligne au lieu de lignes distinctes.</span><span class="sxs-lookup"><span data-stu-id="97d62-118">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="97d62-119">Cela économise de l’espace et améliore la lisibilité de votre code.</span><span class="sxs-lookup"><span data-stu-id="97d62-119">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="97d62-120">L’exemple suivant montre les trois instructions sont séparées par un signe deux-points.</span><span class="sxs-lookup"><span data-stu-id="97d62-120">The following example shows three statements separated by colons.</span></span>  
  
 <span data-ttu-id="97d62-121">[!code-vb[VbVbcnConventions&#12;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="97d62-121">[!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]</span></span>  
  
 <span data-ttu-id="97d62-122">Pour plus d’informations, consultez [Comment : interrompre et combiner des instructions dans le Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="97d62-122">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="97d62-123">Le signe deux-points (`:`) caractères sont également utilisé pour identifier une étiquette d’instruction.</span><span class="sxs-lookup"><span data-stu-id="97d62-123">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="97d62-124">Pour plus d’informations, consultez [Comment : Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="97d62-124">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="97d62-125">Concaténation</span><span class="sxs-lookup"><span data-stu-id="97d62-125">Concatenation</span></span>  
 <span data-ttu-id="97d62-126">Utilisez le `&` opérateur pour *concaténation*, ou lier plusieurs chaînes.</span><span class="sxs-lookup"><span data-stu-id="97d62-126">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="97d62-127">Ne confondez pas avec le `+` opérateur, qui additionne les valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="97d62-127">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="97d62-128">Si vous utilisez le `+` pour concaténer lorsque vous utilisez des valeurs numériques, vous pouvez obtenir des résultats incorrects.</span><span class="sxs-lookup"><span data-stu-id="97d62-128">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="97d62-129">Cela est illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="97d62-129">The following example demonstrates this.</span></span>  
  
 <span data-ttu-id="97d62-130">[!code-vb[VbVbcnConventions&#13;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="97d62-130">[!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]</span></span>  
  
 <span data-ttu-id="97d62-131">Après l’exécution du code précédent, la valeur de `resultA` est 21.01 et la valeur de `resultB` est « 10.0111 ».</span><span class="sxs-lookup"><span data-stu-id="97d62-131">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="97d62-132">Opérateurs d’accès au membre</span><span class="sxs-lookup"><span data-stu-id="97d62-132">Member Access Operators</span></span>  
 <span data-ttu-id="97d62-133">Pour accéder à un membre d’un type, utilisez le point (`.`) ou un point d’exclamation (`!`) opérateur entre le nom de type et le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="97d62-133">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="97d62-134">Point (.) Opérateur</span><span class="sxs-lookup"><span data-stu-id="97d62-134">Dot (.) Operator</span></span>  
 <span data-ttu-id="97d62-135">Utilisez le `.` opérateur sur une classe, une structure, une interface ou une énumération comme un opérateur d’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="97d62-135">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="97d62-136">Le membre peut être un champ, une propriété, un événement ou une méthode.</span><span class="sxs-lookup"><span data-stu-id="97d62-136">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="97d62-137">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="97d62-137">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="97d62-138">[!code-vb[VbVbcnConventions&#14;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="97d62-138">[!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]</span></span>  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="97d62-139">Point d’exclamation ( !) Opérateur</span><span class="sxs-lookup"><span data-stu-id="97d62-139">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="97d62-140">Utilisez le `!` opérateur uniquement sur une classe ou une interface comme un opérateur d’accès au dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="97d62-140">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="97d62-141">La classe ou interface doit avoir une propriété par défaut qui accepte un seul `String` argument.</span><span class="sxs-lookup"><span data-stu-id="97d62-141">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="97d62-142">L’identificateur qui suit immédiatement la `!` devient la valeur de l’argument passée à la propriété par défaut sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="97d62-142">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="97d62-143">Cela est illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="97d62-143">The following example demonstrates this.</span></span>  
  
 <span data-ttu-id="97d62-144">[!code-vb[VbVbcnConventions&#15;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="97d62-144">[!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]</span></span>  
  
 <span data-ttu-id="97d62-145">Les trois lignes de sortie de `MsgBox` tous affichent la valeur `32856`.</span><span class="sxs-lookup"><span data-stu-id="97d62-145">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="97d62-146">La première ligne utilise l’accès traditionnel à la propriété `index`, la seconde utilise le fait que `index` est la propriété par défaut de la classe `hasDefault`, et la troisième utilise l’accès au dictionnaire à la classe.</span><span class="sxs-lookup"><span data-stu-id="97d62-146">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="97d62-147">Notez que le deuxième opérande de le `!` opérateur doit être un identificateur Visual Basic valide ne pas entouré de guillemets doubles (`" "`).</span><span class="sxs-lookup"><span data-stu-id="97d62-147">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="97d62-148">En d’autres termes, vous ne pouvez pas utiliser un littéral de chaîne ou une variable de chaîne.</span><span class="sxs-lookup"><span data-stu-id="97d62-148">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="97d62-149">La modification ci-dessous à la dernière ligne de la `MsgBox` appel génère une erreur car `"X"` est une chaîne entre parenthèses littéral.</span><span class="sxs-lookup"><span data-stu-id="97d62-149">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  <span data-ttu-id="97d62-150">Références aux collections par défaut doivent être explicites.</span><span class="sxs-lookup"><span data-stu-id="97d62-150">References to default collections must be explicit.</span></span> <span data-ttu-id="97d62-151">En particulier, vous ne pouvez pas utiliser le `!` opérateur sur une variable à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="97d62-151">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="97d62-152">Le `!` caractère est également utilisé comme le `Single` caractère de type.</span><span class="sxs-lookup"><span data-stu-id="97d62-152">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d62-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97d62-153">See Also</span></span>  
 <span data-ttu-id="97d62-154">[Structure de programme et Conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="97d62-154">[Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="97d62-155"> [Caractères de type](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span><span class="sxs-lookup"><span data-stu-id="97d62-155"> [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span></span>
