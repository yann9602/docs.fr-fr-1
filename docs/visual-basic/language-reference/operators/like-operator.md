---
title: "Like (opérateur Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ad5729515362bfd52b0c3b401f218a49f569726e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="acbbb-102">Like (opérateur Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acbbb-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="acbbb-103">Compare une chaîne à un modèle.</span><span class="sxs-lookup"><span data-stu-id="acbbb-103">Compares a string against a pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acbbb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acbbb-104">Syntax</span></span>  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="acbbb-105">Composants</span><span class="sxs-lookup"><span data-stu-id="acbbb-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="acbbb-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="acbbb-106">Required.</span></span> <span data-ttu-id="acbbb-107">N’importe quel `Boolean` variable.</span><span class="sxs-lookup"><span data-stu-id="acbbb-107">Any `Boolean` variable.</span></span> <span data-ttu-id="acbbb-108">Le résultat est un `Boolean` valeur indiquant ou non la `string` satisfait la `pattern`.</span><span class="sxs-lookup"><span data-stu-id="acbbb-108">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="acbbb-109">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="acbbb-109">Required.</span></span> <span data-ttu-id="acbbb-110">Toute expression `String`.</span><span class="sxs-lookup"><span data-stu-id="acbbb-110">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="acbbb-111">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="acbbb-111">Required.</span></span> <span data-ttu-id="acbbb-112">N’importe quel `String` expression conforme aux critères spéciaux décrits dans la section « Notes ».</span><span class="sxs-lookup"><span data-stu-id="acbbb-112">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acbbb-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="acbbb-113">Remarks</span></span>  
 <span data-ttu-id="acbbb-114">Si la valeur de `string` est conforme au modèle contenu dans `pattern`, `result` est `True`.</span><span class="sxs-lookup"><span data-stu-id="acbbb-114">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="acbbb-115">Si la chaîne ne satisfait pas le modèle, `result` est `False`.</span><span class="sxs-lookup"><span data-stu-id="acbbb-115">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="acbbb-116">Si les deux `string` et `pattern` sont des chaînes vides, le résultat est `True`.</span><span class="sxs-lookup"><span data-stu-id="acbbb-116">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="acbbb-117">Méthode de comparaison</span><span class="sxs-lookup"><span data-stu-id="acbbb-117">Comparison Method</span></span>  
 <span data-ttu-id="acbbb-118">Le comportement de la `Like` opérateur varie selon le [instruction Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="acbbb-118">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="acbbb-119">La méthode de comparaison de chaînes par défaut pour chaque fichier source est `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="acbbb-119">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="acbbb-120">Options de modèle</span><span class="sxs-lookup"><span data-stu-id="acbbb-120">Pattern Options</span></span>  
 <span data-ttu-id="acbbb-121">Intégrée des critères spéciaux de fournit un outil polyvalent pour les comparaisons de chaînes.</span><span class="sxs-lookup"><span data-stu-id="acbbb-121">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="acbbb-122">Les fonctionnalités de mise en correspondance de modèle permettent de faire correspondre chaque caractère `string` sur un caractère spécifique, un caractère générique, une liste de caractères ou une plage de caractères.</span><span class="sxs-lookup"><span data-stu-id="acbbb-122">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="acbbb-123">Le tableau suivant montre les caractères autorisés dans `pattern` et leur correspondance.</span><span class="sxs-lookup"><span data-stu-id="acbbb-123">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="acbbb-124">Caractères dans`pattern`</span><span class="sxs-lookup"><span data-stu-id="acbbb-124">Characters in `pattern`</span></span>|<span data-ttu-id="acbbb-125">Correspondances dans`string`</span><span class="sxs-lookup"><span data-stu-id="acbbb-125">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="acbbb-126">Tout caractère unique</span><span class="sxs-lookup"><span data-stu-id="acbbb-126">Any single character</span></span>|  
|`*`|<span data-ttu-id="acbbb-127">Zéro ou plusieurs caractères</span><span class="sxs-lookup"><span data-stu-id="acbbb-127">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="acbbb-128">Tout chiffre (0 à 9)</span><span class="sxs-lookup"><span data-stu-id="acbbb-128">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="acbbb-129">Tout caractère unique dans`charlist`</span><span class="sxs-lookup"><span data-stu-id="acbbb-129">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="acbbb-130">N’importe quel caractère ne figurant pas dans`charlist`</span><span class="sxs-lookup"><span data-stu-id="acbbb-130">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="acbbb-131">Listes de caractères</span><span class="sxs-lookup"><span data-stu-id="acbbb-131">Character Lists</span></span>  
 <span data-ttu-id="acbbb-132">Un groupe d’un ou plusieurs caractères (`charlist`) placés entre crochets (`[ ]`) peut être utilisé pour correspondre à n’importe quel caractère unique dans `string` et peut inclure le code de presque n’importe quel caractère, y compris les chiffres.</span><span class="sxs-lookup"><span data-stu-id="acbbb-132">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="acbbb-133">Un point d’exclamation (`!`) au début de `charlist` signifie qu’une correspondance est établie si un caractère à l’exception des caractères de `charlist` se trouve dans `string`.</span><span class="sxs-lookup"><span data-stu-id="acbbb-133">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="acbbb-134">Lorsqu’il est utilisé en dehors de crochets, le point d’exclamation correspond à lui-même.</span><span class="sxs-lookup"><span data-stu-id="acbbb-134">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="acbbb-135">Caractères spéciaux</span><span class="sxs-lookup"><span data-stu-id="acbbb-135">Special Characters</span></span>  
 <span data-ttu-id="acbbb-136">Pour mettre en correspondance le crochet de caractères spéciaux (`[`), point d’interrogation (`?`), signe dièse (`#`) et l’astérisque (`*`), les mettre entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="acbbb-136">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="acbbb-137">Le crochet droit (`]`) ne peut pas être utilisé dans un groupe pour correspondre à lui-même, mais il peut être utilisé en dehors d’un groupe de caractères.</span><span class="sxs-lookup"><span data-stu-id="acbbb-137">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="acbbb-138">La séquence de caractères `[]` est considérée comme une chaîne de longueur nulle (`""`).</span><span class="sxs-lookup"><span data-stu-id="acbbb-138">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="acbbb-139">Toutefois, il ne peut pas faire partie d’une liste de caractères placés entourée crochets.</span><span class="sxs-lookup"><span data-stu-id="acbbb-139">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="acbbb-140">Si vous souhaitez vérifier si une position dans `string` contient l’un d’un groupe de caractères ou aucun caractère, vous pouvez utiliser `Like` à deux reprises.</span><span class="sxs-lookup"><span data-stu-id="acbbb-140">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="acbbb-141">Pour obtenir un exemple, consultez [Comment : faire correspondre une chaîne à un modèle](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="acbbb-141">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="acbbb-142">Plages de caractères</span><span class="sxs-lookup"><span data-stu-id="acbbb-142">Character Ranges</span></span>  
 <span data-ttu-id="acbbb-143">À l’aide d’un trait d’union (`–`) pour séparer les limites inférieure et supérieure de la plage, `charlist` peut spécifier une plage de caractères.</span><span class="sxs-lookup"><span data-stu-id="acbbb-143">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="acbbb-144">Par exemple, `[A–Z]` trouve une correspondance si la position de caractère correspondant dans `string` contient un caractère dans la plage `A`–`Z`, et `[!H–L]` trouve une correspondance si la position de caractère correspondant contient un caractère en dehors de la plage `H`–`L`.</span><span class="sxs-lookup"><span data-stu-id="acbbb-144">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="acbbb-145">Lorsque vous spécifiez une plage de caractères, ils doivent apparaître dans l’ordre croissant, autrement dit, du plus petit au plus grand.</span><span class="sxs-lookup"><span data-stu-id="acbbb-145">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="acbbb-146">Par conséquent, `[A–Z]` est un modèle valide, mais `[Z–A]` n’est pas.</span><span class="sxs-lookup"><span data-stu-id="acbbb-146">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="acbbb-147">Plusieurs plages de caractères</span><span class="sxs-lookup"><span data-stu-id="acbbb-147">Multiple Character Ranges</span></span>  
 <span data-ttu-id="acbbb-148">Pour spécifier plusieurs plages pour la même position de caractère, placez les crochets sans délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="acbbb-148">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="acbbb-149">Par exemple, `[A–CX–Z]` trouve une correspondance si la position de caractère correspondant dans `string` contient un caractère dans la plage de `A`–`C` ou la plage `X`–`Z`.</span><span class="sxs-lookup"><span data-stu-id="acbbb-149">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="acbbb-150">Utilisation du trait d’union</span><span class="sxs-lookup"><span data-stu-id="acbbb-150">Usage of the Hyphen</span></span>  
 <span data-ttu-id="acbbb-151">Un trait d’union (`–`) peuvent apparaître au début (après un point d’exclamation, le cas échéant) ou à la fin de `charlist` pour correspondre à lui-même.</span><span class="sxs-lookup"><span data-stu-id="acbbb-151">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="acbbb-152">Dans un autre emplacement, le trait d’union identifie une plage de caractères délimitée par les caractères de chaque côté du trait d’union.</span><span class="sxs-lookup"><span data-stu-id="acbbb-152">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="acbbb-153">Séquence de classement</span><span class="sxs-lookup"><span data-stu-id="acbbb-153">Collating Sequence</span></span>  
 <span data-ttu-id="acbbb-154">La signification d’une plage spécifiée dépend de l’ordre au moment de l’exécution, comme déterminé par des caractères `Option``Compare` et les paramètres régionaux du système, le code s’exécute.</span><span class="sxs-lookup"><span data-stu-id="acbbb-154">The meaning of a specified range depends on the character ordering at run time, as determined by `Option``Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="acbbb-155">Avec `Option``Compare``Binary`, la plage `[A–E]` correspond à `A`, `B`, `C`, `D`, et `E`.</span><span class="sxs-lookup"><span data-stu-id="acbbb-155">With `Option``Compare``Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="acbbb-156">Avec `Option``Compare``Text`, `[A–E]` correspond à `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, et `e`.</span><span class="sxs-lookup"><span data-stu-id="acbbb-156">With `Option``Compare``Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="acbbb-157">La plage ne correspond pas à `Ê` ou `ê` , car les caractères accentués sont des caractères non accentués dans l’ordre de tri.</span><span class="sxs-lookup"><span data-stu-id="acbbb-157">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="acbbb-158">Caractères digrammes</span><span class="sxs-lookup"><span data-stu-id="acbbb-158">Digraph Characters</span></span>  
 <span data-ttu-id="acbbb-159">Dans certaines langues, il existe des caractères alphabétiques représentent deux caractères distincts.</span><span class="sxs-lookup"><span data-stu-id="acbbb-159">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="acbbb-160">Par exemple, plusieurs langues utilisent le caractère `æ` pour représenter les caractères `a` et `e` lorsqu’ils apparaissent ensemble.</span><span class="sxs-lookup"><span data-stu-id="acbbb-160">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="acbbb-161">Le `Like` opérateur reconnaît que le caractère digramme simple et deux caractères sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="acbbb-161">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="acbbb-162">Lorsqu’une langue qui utilise un caractère digramme est spécifiée dans les paramètres régionaux du système, une occurrence du caractère digramme simple, que ce soit `pattern` ou `string` correspond à la séquence de deux caractères équivalente dans l’autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="acbbb-162">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="acbbb-163">De même, un caractère digramme dans `pattern` entre crochets (lui-même, dans une liste ou dans une plage) correspond à la séquence de deux caractères équivalente dans `string`.</span><span class="sxs-lookup"><span data-stu-id="acbbb-163">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="acbbb-164">Surcharge</span><span class="sxs-lookup"><span data-stu-id="acbbb-164">Overloading</span></span>  
 <span data-ttu-id="acbbb-165">Le `Like` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="acbbb-165">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="acbbb-166">Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="acbbb-166">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="acbbb-167">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="acbbb-167">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="acbbb-168">Exemple</span><span class="sxs-lookup"><span data-stu-id="acbbb-168">Example</span></span>  
 <span data-ttu-id="acbbb-169">Cet exemple utilise le `Like` pour comparer des chaînes de plusieurs modèles.</span><span class="sxs-lookup"><span data-stu-id="acbbb-169">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="acbbb-170">Les résultats se dirigent vers un `Boolean` variable qui indique si chaque chaîne satisfait le modèle.</span><span class="sxs-lookup"><span data-stu-id="acbbb-170">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="acbbb-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acbbb-171">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [<span data-ttu-id="acbbb-172">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="acbbb-172">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="acbbb-173">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="acbbb-173">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="acbbb-174">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="acbbb-174">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="acbbb-175">Option Compare (instruction)</span><span class="sxs-lookup"><span data-stu-id="acbbb-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="acbbb-176">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="acbbb-176">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="acbbb-177">Guide pratique : faire correspondre une chaîne à un modèle</span><span class="sxs-lookup"><span data-stu-id="acbbb-177">How to: Match a String against a Pattern</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
