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
# <a name="like-operator-visual-basic"></a>Like (opérateur Visual Basic)
Compare une chaîne à un modèle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Obligatoire. N’importe quel `Boolean` variable. Le résultat est un `Boolean` valeur indiquant ou non la `string` satisfait la `pattern`.  
  
 `string`  
 Obligatoire. Toute expression `String`.  
  
 `pattern`  
 Obligatoire. N’importe quel `String` expression conforme aux critères spéciaux décrits dans la section « Notes ».  
  
## <a name="remarks"></a>Remarques  
 Si la valeur de `string` est conforme au modèle contenu dans `pattern`, `result` est `True`. Si la chaîne ne satisfait pas le modèle, `result` est `False`. Si les deux `string` et `pattern` sont des chaînes vides, le résultat est `True`.  
  
## <a name="comparison-method"></a>Méthode de comparaison  
 Le comportement de la `Like` opérateur varie selon le [instruction Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md). La méthode de comparaison de chaînes par défaut pour chaque fichier source est `Option Compare Binary`.  
  
## <a name="pattern-options"></a>Options de modèle  
 Intégrée des critères spéciaux de fournit un outil polyvalent pour les comparaisons de chaînes. Les fonctionnalités de mise en correspondance de modèle permettent de faire correspondre chaque caractère `string` sur un caractère spécifique, un caractère générique, une liste de caractères ou une plage de caractères. Le tableau suivant montre les caractères autorisés dans `pattern` et leur correspondance.  
  
|Caractères dans`pattern`|Correspondances dans`string`|  
|-----------------------------|-------------------------|  
|`?`|Tout caractère unique|  
|`*`|Zéro ou plusieurs caractères|  
|`#`|Tout chiffre (0 à 9)|  
|`[charlist]`|Tout caractère unique dans`charlist`|  
|`[!charlist]`|N’importe quel caractère ne figurant pas dans`charlist`|  
  
## <a name="character-lists"></a>Listes de caractères  
 Un groupe d’un ou plusieurs caractères (`charlist`) placés entre crochets (`[ ]`) peut être utilisé pour correspondre à n’importe quel caractère unique dans `string` et peut inclure le code de presque n’importe quel caractère, y compris les chiffres.  
  
 Un point d’exclamation (`!`) au début de `charlist` signifie qu’une correspondance est établie si un caractère à l’exception des caractères de `charlist` se trouve dans `string`. Lorsqu’il est utilisé en dehors de crochets, le point d’exclamation correspond à lui-même.  
  
## <a name="special-characters"></a>Caractères spéciaux  
 Pour mettre en correspondance le crochet de caractères spéciaux (`[`), point d’interrogation (`?`), signe dièse (`#`) et l’astérisque (`*`), les mettre entre parenthèses. Le crochet droit (`]`) ne peut pas être utilisé dans un groupe pour correspondre à lui-même, mais il peut être utilisé en dehors d’un groupe de caractères.  
  
 La séquence de caractères `[]` est considérée comme une chaîne de longueur nulle (`""`). Toutefois, il ne peut pas faire partie d’une liste de caractères placés entourée crochets. Si vous souhaitez vérifier si une position dans `string` contient l’un d’un groupe de caractères ou aucun caractère, vous pouvez utiliser `Like` à deux reprises. Pour obtenir un exemple, consultez [Comment : faire correspondre une chaîne à un modèle](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Plages de caractères  
 À l’aide d’un trait d’union (`–`) pour séparer les limites inférieure et supérieure de la plage, `charlist` peut spécifier une plage de caractères. Par exemple, `[A–Z]` trouve une correspondance si la position de caractère correspondant dans `string` contient un caractère dans la plage `A`–`Z`, et `[!H–L]` trouve une correspondance si la position de caractère correspondant contient un caractère en dehors de la plage `H`–`L`.  
  
 Lorsque vous spécifiez une plage de caractères, ils doivent apparaître dans l’ordre croissant, autrement dit, du plus petit au plus grand. Par conséquent, `[A–Z]` est un modèle valide, mais `[Z–A]` n’est pas.  
  
### <a name="multiple-character-ranges"></a>Plusieurs plages de caractères  
 Pour spécifier plusieurs plages pour la même position de caractère, placez les crochets sans délimiteurs. Par exemple, `[A–CX–Z]` trouve une correspondance si la position de caractère correspondant dans `string` contient un caractère dans la plage de `A`–`C` ou la plage `X`–`Z`.  
  
### <a name="usage-of-the-hyphen"></a>Utilisation du trait d’union  
 Un trait d’union (`–`) peuvent apparaître au début (après un point d’exclamation, le cas échéant) ou à la fin de `charlist` pour correspondre à lui-même. Dans un autre emplacement, le trait d’union identifie une plage de caractères délimitée par les caractères de chaque côté du trait d’union.  
  
## <a name="collating-sequence"></a>Séquence de classement  
 La signification d’une plage spécifiée dépend de l’ordre au moment de l’exécution, comme déterminé par des caractères `Option``Compare` et les paramètres régionaux du système, le code s’exécute. Avec `Option``Compare``Binary`, la plage `[A–E]` correspond à `A`, `B`, `C`, `D`, et `E`. Avec `Option``Compare``Text`, `[A–E]` correspond à `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, et `e`. La plage ne correspond pas à `Ê` ou `ê` , car les caractères accentués sont des caractères non accentués dans l’ordre de tri.  
  
## <a name="digraph-characters"></a>Caractères digrammes  
 Dans certaines langues, il existe des caractères alphabétiques représentent deux caractères distincts. Par exemple, plusieurs langues utilisent le caractère `æ` pour représenter les caractères `a` et `e` lorsqu’ils apparaissent ensemble. Le `Like` opérateur reconnaît que le caractère digramme simple et deux caractères sont équivalents.  
  
 Lorsqu’une langue qui utilise un caractère digramme est spécifiée dans les paramètres régionaux du système, une occurrence du caractère digramme simple, que ce soit `pattern` ou `string` correspond à la séquence de deux caractères équivalente dans l’autre chaîne. De même, un caractère digramme dans `pattern` entre crochets (lui-même, dans une liste ou dans une plage) correspond à la séquence de deux caractères équivalente dans `string`.  
  
## <a name="overloading"></a>Surcharge  
 Le `Like` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le `Like` pour comparer des chaînes de plusieurs modèles. Les résultats se dirigent vers un `Boolean` variable qui indique si chaque chaîne satisfait le modèle.  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [Opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Option Compare (instruction)](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Guide pratique : faire correspondre une chaîne à un modèle](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
