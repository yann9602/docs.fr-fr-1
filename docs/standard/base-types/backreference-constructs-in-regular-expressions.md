---
title: "Constructions de backreference dans les expressions régulières"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- backreferences
- constructs, backreference
- .NET Framework regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a884e70f542c2ed7ff63e39cb7eadedf0ef7b4d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="backreference-constructs-in-regular-expressions"></a><span data-ttu-id="2f1d1-102">Constructions de backreference dans les expressions régulières</span><span class="sxs-lookup"><span data-stu-id="2f1d1-102">Backreference Constructs in Regular Expressions</span></span>
<span data-ttu-id="2f1d1-103">Les références arrière offrent un moyen pratique d’identifier un caractère répété ou une sous-chaîne répétée dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-103">Backreferences provide a convenient way to identify a repeated character or substring within a string.</span></span> <span data-ttu-id="2f1d1-104">Par exemple, si la chaîne d’entrée contient plusieurs occurrences d’une sous-chaîne arbitraire, vous pouvez faire correspondre la première occurrence à un groupe de capture, puis utiliser une référence arrière pour faire correspondre les occurrences suivantes de la sous-chaîne.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-104">For example, if the input string contains multiple occurrences of an arbitrary substring, you can match the first occurrence with a capturing group, and then use a backreference to match subsequent occurrences of the substring.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f1d1-105">Une syntaxe distincte est utilisée pour faire référence à des groupes de capture nommés et numérotés dans les chaînes de remplacement.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-105">A separate syntax is used to refer to named and numbered capturing groups in replacement strings.</span></span> <span data-ttu-id="2f1d1-106">Pour plus d'informations, consultez [Substitutions](substitutions-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2f1d1-106">For more information, see [Substitutions](substitutions-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="2f1d1-107">.NET définit des éléments de langage différents pour faire référence aux groupes de capture nommés et numérotés.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-107">.NET defines separate language elements to refer to numbered and named capturing groups.</span></span> <span data-ttu-id="2f1d1-108">Pour plus d’informations sur les groupes de capture, consultez [constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2f1d1-108">For more information about capturing groups, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span></span>  
  
## <a name="numbered-backreferences"></a><span data-ttu-id="2f1d1-109">Références arrière numérotées</span><span class="sxs-lookup"><span data-stu-id="2f1d1-109">Numbered Backreferences</span></span>  
 <span data-ttu-id="2f1d1-110">Une référence arrière numérotée utilise la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="2f1d1-110">A numbered backreference uses the following syntax:</span></span>  
  
 <span data-ttu-id="2f1d1-111">`\` *nombre*</span><span class="sxs-lookup"><span data-stu-id="2f1d1-111">`\` *number*</span></span>  
  
 <span data-ttu-id="2f1d1-112">où *numéro* est la position ordinale du groupe de capture dans l’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-112">where *number* is the ordinal position of the capturing group in the regular expression.</span></span> <span data-ttu-id="2f1d1-113">Par exemple, `\4` correspond au contenu du quatrième groupe de capture.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-113">For example, `\4` matches the contents of the fourth capturing group.</span></span> <span data-ttu-id="2f1d1-114">Si *nombre* est ne pas défini dans le modèle d’expression régulière, une erreur d’analyse se produite, et le moteur des expressions régulières lève une <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-114">If *number* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="2f1d1-115">Par exemple, l’expression régulière `\b(\w+)\s\1` est valide, car `(\w+)` est le premier et unique groupe de capture dans l’expression.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-115">For example, the regular expression `\b(\w+)\s\1` is valid, because `(\w+)` is the first and only capturing group in the expression.</span></span> <span data-ttu-id="2f1d1-116">D’un autre côté, `\b(\w+)\s\2` n’est pas valide et lève une exception d’argument, car il n’existe aucun groupe de capture numéroté `\2`.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-116">On the other hand, `\b(\w+)\s\2` is invalid and throws an argument exception, because there is no capturing group numbered `\2`.</span></span>  
  
 <span data-ttu-id="2f1d1-117">Notez l’ambiguïté entre les codes d’échappement octale (tel que `\16`) et `\` *nombre* références arrière qui utilisent la même notation.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-117">Note the ambiguity between octal escape codes (such as `\16`) and `\`*number* backreferences that use the same notation.</span></span> <span data-ttu-id="2f1d1-118">Cette ambiguïté est résolue comme suit :</span><span class="sxs-lookup"><span data-stu-id="2f1d1-118">This ambiguity is resolved as follows:</span></span>  
  
-   <span data-ttu-id="2f1d1-119">Les expressions `\1` à `\9` sont toujours interprétées comme références arrière et non comme codes octaux.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-119">The expressions `\1` through `\9` are always interpreted as backreferences, and not as octal codes.</span></span>  
  
-   <span data-ttu-id="2f1d1-120">Si le premier chiffre d’une expression à plusieurs chiffres est 8 ou 9 (comme `\80` ou `\91`), l’expression est interprétée comme littéral.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-120">If the first digit of a multidigit expression is 8 or 9 (such as `\80` or `\91`), the expression as interpreted as a literal.</span></span>  
  
-   <span data-ttu-id="2f1d1-121">Les expressions à partir de `\10` et plus sont considérées comme des références arrière s’il existe une référence arrière correspondant à ce numéro ; sinon, elles sont interprétées comme des codes octaux.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-121">Expressions from `\10` and greater are considered backreferences if there is a backreference corresponding to that number; otherwise, they are interpreted as octal codes.</span></span>  
  
-   <span data-ttu-id="2f1d1-122">Si une expression régulière contient une backreference à un numéro de groupe non défini, une erreur d’analyse se produit et le moteur des expressions régulières lève une <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-122">If a regular expression contains a backreference to an undefined group number, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="2f1d1-123">Si l’ambiguïté est un problème, vous pouvez utiliser la `\k<` *nom* `>` notation, qui est sans équivoque et ne peut pas être confondue avec les codes de caractère octal.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-123">If the ambiguity is a problem, you can use the `\k<`*name*`>` notation, which is unambiguous and cannot be confused with octal character codes.</span></span> <span data-ttu-id="2f1d1-124">De même, les codes hexadécimaux tels que `\xdd` ne sont pas ambigus et ne peuvent pas être confondus avec les références arrière.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-124">Similarly, hexadecimal codes such as `\xdd` are unambiguous and cannot be confused with backreferences.</span></span>  
  
 <span data-ttu-id="2f1d1-125">L’exemple suivant recherche des caractères de mot doubles dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-125">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="2f1d1-126">Il définit une expression régulière, `(\w)\1`, qui se compose des éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-126">It defines a regular expression, `(\w)\1`, which consists of the following elements.</span></span>  
  
|<span data-ttu-id="2f1d1-127">Élément</span><span class="sxs-lookup"><span data-stu-id="2f1d1-127">Element</span></span>|<span data-ttu-id="2f1d1-128">Description</span><span class="sxs-lookup"><span data-stu-id="2f1d1-128">Description</span></span>|  
|-------------|-----------------|  
|`(\w)`|<span data-ttu-id="2f1d1-129">Mettre en correspondance un caractère de mot et l’affecter au premier groupe de capture.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-129">Match a word character and assign it to the first capturing group.</span></span>|  
|`\1`|<span data-ttu-id="2f1d1-130">Mettre en correspondance le caractère suivant dont la valeur est identique à celle du premier groupe de capture.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-130">Match the next character that is the same as the value of the first capturing group.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## <a name="named-backreferences"></a><span data-ttu-id="2f1d1-131">Références arrière nommées</span><span class="sxs-lookup"><span data-stu-id="2f1d1-131">Named Backreferences</span></span>  
 <span data-ttu-id="2f1d1-132">Une référence arrière nommée est définie avec la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="2f1d1-132">A named backreference is defined by using the following syntax:</span></span>  
  
 <span data-ttu-id="2f1d1-133">`\k<` *name* `>`</span><span class="sxs-lookup"><span data-stu-id="2f1d1-133">`\k<` *name* `>`</span></span>  
  
 <span data-ttu-id="2f1d1-134">ou :</span><span class="sxs-lookup"><span data-stu-id="2f1d1-134">or:</span></span>  
  
 <span data-ttu-id="2f1d1-135">`\k'` *nom* `'`</span><span class="sxs-lookup"><span data-stu-id="2f1d1-135">`\k'` *name* `'`</span></span>  
  
 <span data-ttu-id="2f1d1-136">où *nom* est le nom d’un groupe de capture défini dans le modèle d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-136">where *name* is the name of a capturing group defined in the regular expression pattern.</span></span> <span data-ttu-id="2f1d1-137">Si *nom* est ne pas défini dans le modèle d’expression régulière, une erreur d’analyse se produite, et le moteur des expressions régulières lève une <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-137">If *name* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="2f1d1-138">L’exemple suivant recherche des caractères de mot doubles dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-138">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="2f1d1-139">Il définit une expression régulière, `(?<char>\w)\k<char>`, qui se compose des éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-139">It defines a regular expression, `(?<char>\w)\k<char>`, which consists of the following elements.</span></span>  
  
|<span data-ttu-id="2f1d1-140">Élément</span><span class="sxs-lookup"><span data-stu-id="2f1d1-140">Element</span></span>|<span data-ttu-id="2f1d1-141">Description</span><span class="sxs-lookup"><span data-stu-id="2f1d1-141">Description</span></span>|  
|-------------|-----------------|  
|`(?<char>\w)`|<span data-ttu-id="2f1d1-142">Correspond à un caractère alphabétique et l’assigner à un groupe de capture nommé `char`.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-142">Match a word character and assign it to a capturing group named `char`.</span></span>|  
|`\k<char>`|<span data-ttu-id="2f1d1-143">Le caractère suivant qui est identique à la valeur de le `char` groupe de capture.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-143">Match the next character that is the same as the value of the `char` capturing group.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  
  
 <span data-ttu-id="2f1d1-144">Remarquez que *nom* peut également être la représentation sous forme de chaîne d’un numéro.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-144">Note that *name* can also be the string representation of a number.</span></span> <span data-ttu-id="2f1d1-145">Par exemple, l’exemple suivant utilise l’expression régulière `(?<2>\w)\k<2>` pour rechercher des caractères de mot doubles dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-145">For example, the following example uses the regular expression `(?<2>\w)\k<2>` to find doubled word characters in a string.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  
  
## <a name="what-backreferences-match"></a><span data-ttu-id="2f1d1-146">Correspondance des références arrière</span><span class="sxs-lookup"><span data-stu-id="2f1d1-146">What Backreferences Match</span></span>  
 <span data-ttu-id="2f1d1-147">Une référence arrière référence la définition la plus récente d’un groupe (la définition la plus immédiatement à gauche, dans le cadre d’une mise en correspondance de gauche à droite).</span><span class="sxs-lookup"><span data-stu-id="2f1d1-147">A backreference refers to the most recent definition of a group (the definition most immediately to the left, when matching left to right).</span></span> <span data-ttu-id="2f1d1-148">Quand un groupe effectue plusieurs captures, une référence arrière référence la capture la plus récente.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-148">When a group makes multiple captures, a backreference refers to the most recent capture.</span></span>  
  
 <span data-ttu-id="2f1d1-149">L’exemple suivant inclut un modèle d’expression régulière, `(?<1>a)(?<1>\1b)*`, qui redéfinit le groupe nommé \1.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-149">The following example includes a regular expression pattern, `(?<1>a)(?<1>\1b)*`, which redefines the \1 named group.</span></span> <span data-ttu-id="2f1d1-150">Le tableau suivant décrit chaque modèle dans l’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-150">The following table describes each pattern in the regular expression.</span></span>  
  
|<span data-ttu-id="2f1d1-151">Modèle</span><span class="sxs-lookup"><span data-stu-id="2f1d1-151">Pattern</span></span>|<span data-ttu-id="2f1d1-152">Description</span><span class="sxs-lookup"><span data-stu-id="2f1d1-152">Description</span></span>|  
|-------------|-----------------|  
|`(?<1>a)`|<span data-ttu-id="2f1d1-153">Le caractère « a » et assigner le résultat au groupe de capture nommé `1`.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-153">Match the character "a" and assign the result to the capturing group named `1`.</span></span>|  
|`(?<1>\1b)*`|<span data-ttu-id="2f1d1-154">Occurrence de mettre en correspondance 0 ou 1 du groupe nommé `1` avec un « b » et assigner le résultat au groupe de capture nommé `1`.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-154">Match 0 or 1 occurrence of the group named `1` along with a "b", and assign the result to the capturing group named `1`.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 <span data-ttu-id="2f1d1-155">En comparant l’expression régulière à la chaîne d’entrée (« aababb »), le moteur d’expression régulière effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="2f1d1-155">In comparing the regular expression with the input string ("aababb"), the regular expression engine performs the following operations:</span></span>  
  
1.  <span data-ttu-id="2f1d1-156">Il commence au début de la chaîne et réussit à mettre en correspondance « a » avec l’expression `(?<1>a)`.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-156">It starts at the beginning of the string, and successfully matches "a" with the expression `(?<1>a)`.</span></span> <span data-ttu-id="2f1d1-157">La valeur de le `1` groupe est désormais « a ».</span><span class="sxs-lookup"><span data-stu-id="2f1d1-157">The value of the `1` group is now "a".</span></span>  
  
2.  <span data-ttu-id="2f1d1-158">Il passe au deuxième caractère et réussit à mettre en correspondance la chaîne « ab » avec l’expression `\1b`, ou « ab ».</span><span class="sxs-lookup"><span data-stu-id="2f1d1-158">It advances to the second character, and successfully matches the string "ab" with the expression `\1b`, or "ab".</span></span> <span data-ttu-id="2f1d1-159">Il affecte ensuite le résultat, « ab », à `\1`.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-159">It then assigns the result, "ab" to `\1`.</span></span>  
  
3.  <span data-ttu-id="2f1d1-160">Il passe au quatrième caractère.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-160">It advances to the fourth character.</span></span> <span data-ttu-id="2f1d1-161">L’expression `(?<1>\1b)` doit être mise en correspondance zéro fois ou plus, donc il réussit à mettre en correspondance la chaîne « abb » avec l’expression `\1b`.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-161">The expression `(?<1>\1b)` is to be matched zero or more times, so it successfully matches the string "abb" with the expression `\1b`.</span></span> <span data-ttu-id="2f1d1-162">Il réaffecte le résultat, « abb », à `\1`.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-162">It assigns the result, "abb", back to `\1`.</span></span>  
  
 <span data-ttu-id="2f1d1-163">Dans cet exemple, `*` est un quantificateur en boucle : il est évalué à plusieurs reprises jusqu’à ce que le moteur d’expression régulière ne puisse pas mettre en correspondance le modèle qu’il définit.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-163">In this example, `*` is a looping quantifier -- it is evaluated repeatedly until the regular expression engine cannot match the pattern it defines.</span></span> <span data-ttu-id="2f1d1-164">Les quantificateurs en boucle ne suppriment pas les définitions de groupe.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-164">Looping quantifiers do not clear group definitions.</span></span>  
  
 <span data-ttu-id="2f1d1-165">Si un groupe n’a capturé aucune sous-chaîne, aucune référence arrière à ce groupe n’est définie et aucune correspondance n’est trouvée.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-165">If a group has not captured any substrings, a backreference to that group is undefined and never matches.</span></span> <span data-ttu-id="2f1d1-166">Ceci est illustré dans le modèle d’expression régulière `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, qui est défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="2f1d1-166">This is illustrated by the regular expression pattern `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, which is defined as follows:</span></span>  
  
|<span data-ttu-id="2f1d1-167">Modèle</span><span class="sxs-lookup"><span data-stu-id="2f1d1-167">Pattern</span></span>|<span data-ttu-id="2f1d1-168">Description</span><span class="sxs-lookup"><span data-stu-id="2f1d1-168">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="2f1d1-169">Commencer la correspondance à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-169">Begin the match on a word boundary.</span></span>|  
|`(\p{Lu}{2})`|<span data-ttu-id="2f1d1-170">Mettre en correspondance deux lettres majuscules.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-170">Match two uppercase letters.</span></span> <span data-ttu-id="2f1d1-171">Il s'agit du premier groupe de capture.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-171">This is the first capturing group.</span></span>|  
|`(\d{2})?`|<span data-ttu-id="2f1d1-172">Mettre en correspondance zéro ou une occurrence de deux chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-172">Match zero or one occurrence of two decimal digits.</span></span> <span data-ttu-id="2f1d1-173">Il s'agit du deuxième groupe de capture.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-173">This is the second capturing group.</span></span>|  
|`(\p{Lu}{2})`|<span data-ttu-id="2f1d1-174">Mettre en correspondance deux lettres majuscules.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-174">Match two uppercase letters.</span></span> <span data-ttu-id="2f1d1-175">Il s'agit du troisième groupe de capture.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-175">This is the third capturing group.</span></span>|  
|`\b`|<span data-ttu-id="2f1d1-176">Terminer la correspondance à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-176">End the match on a word boundary.</span></span>|  
  
 <span data-ttu-id="2f1d1-177">Une chaîne d’entrée peut mettre en correspondre cette expression régulière même si les deux chiffres décimaux définis par le deuxième groupe de capture ne sont pas présents.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-177">An input string can match this regular expression even if the two decimal digits that are defined by the second capturing group are not present.</span></span> <span data-ttu-id="2f1d1-178">L’exemple suivant montre que, même si la mise en correspondance réussit, un groupe de capture vide est trouvé entre deux groupes de capture trouvés.</span><span class="sxs-lookup"><span data-stu-id="2f1d1-178">The following example shows that even though the match is successful, an empty capturing group is found between two successful capturing groups.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="2f1d1-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f1d1-179">See Also</span></span>  
 [<span data-ttu-id="2f1d1-180">Langage des expressions régulières - Aide-mémoire</span><span class="sxs-lookup"><span data-stu-id="2f1d1-180">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
