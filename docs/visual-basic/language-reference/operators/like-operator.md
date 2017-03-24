---
title: "Like Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "Like"
  - "vb.Like"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "similar to"
  - "pattern matching"
  - "Like operator [Visual Basic]"
  - "? symbol, wildcard character"
  - "string comparison [Visual Basic], Like operator"
  - "strings [Visual Basic], comparing"
  - "comparison operators"
  - "symbols, wildcard"
  - "wildcards, Like operator"
  - "strings [Visual Basic], matching"
  - "string comparison [Visual Basic], sorting data"
  - "data [Visual Basic], sorting"
  - "text [Visual Basic], comparing"
  - "operators [Visual Basic], pattern-matching"
  - "data [Visual Basic], string comparisons"
  - "string comparison [Visual Basic], Like operators"
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Like Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Compare une chaîne à un modèle.  
  
## Syntaxe  
  
```  
  
result = string Like pattern  
```  
  
## Composants  
 `result`  
 Obligatoire.  Toute variable `Boolean`.  Le résultat est une valeur `Boolean` indiquant si `string` satisfait `pattern`.  
  
 `string`  
 Obligatoire.  Toute expression `String`.  
  
 `pattern`  
 Obligatoire.  Toute expression `String` se conformant aux critères spéciaux décrits dans les « Notes ».  
  
## Notes  
 Si la valeur de `string` satisfait le modèle contenu dans `pattern`, `result` a la valeur `True`.  Si la chaîne ne satisfait pas le modèle, `result` a la valeur `False`.  Si `string` et `pattern` sont des chaînes vides, le résultat est `True`.  
  
## Méthode de comparaison  
 Le comportement de l'opérateur `Like` dépend de l'[Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).  La méthode de comparaison de chaînes par défaut pour chaque fichier source est `Option Compare Binary`.  
  
## Options de modèle  
 La correspondance de modèles intégrée fournit un outil polyvalent pour les comparaisons de chaînes.  Les fonctionnalités se conformant aux critères spéciaux vous permettent de faire correspondre chaque caractère d'une `string` à un caractère spécifique, un caractère générique, une liste de caractères ou une plage de caractères.  Le tableau suivant illustre les caractères autorisés dans `pattern` et ce à quoi ils correspondent :  
  
|Caractères contenus dans `pattern`|Correspond dans `string` à|  
|----------------------------------------|--------------------------------|  
|`?`|Tout caractère unique|  
|`*`|Zéro ou plusieurs caractères|  
|`#`|Tout chiffre \(0\-9\)|  
|`[` `charlist` `]`|Tout caractère présent dans `charlist`|  
|`[!` `charlist` `]`|Tout caractère absent de `charlist`|  
  
## Listes de caractères  
 Un ou plusieurs caractères \(`charlist`\) placés entre crochets \(`[ ]`\) peuvent être utilisés pour faire correspondre tout caractère unique de `string` et peut comprendre presque tous les codes de caractères, y compris les chiffres.  
  
 Un point d'exclamation \(`!`\) au début de `charlist` signifie que la correspondance est trouvée si tous les caractères excepté ceux de `charlist` se trouvent dans `string`.  Lorsqu'il est utilisé à l'extérieur de crochets, le point d'exclamation correspond à lui\-même.  
  
## Caractères spéciaux  
 Pour faire correspondre les caractères spéciaux comme le crochet ouvrant \(`[`\), le point d'interrogation \(`?`\), le signe dièse \(`#`\) et l'astérisque \(`*`\), vous devez les mettre entre crochets.  Le crochet fermant \(`]`\) ne peut pas être utilisé dans un groupe pour se représenter lui\-même, mais il peut être employé comme un caractère spécifique à l'extérieur d'un groupe.  
  
 La séquence de caractères `[]` est considérée comme une chaîne de longueur nulle \(`""`\).  Toutefois, elle ne peut pas faire partie d'une liste de caractères entre crochets.  Si vous souhaitez vérifier si une position dans la `string` contient un caractère ou pas, vous pouvez utiliser `Like` deux fois.  Pour obtenir un exemple, consultez [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## Plage de caractères  
 Si vous utilisez un trait d'union \(`–`\) pour séparer les limites inférieure et supérieure de la plage, `charlist` peut spécifier une plage de caractères.  Par exemple, `[A–Z]` trouve une correspondance si la position du caractère correspondante dans `string` contient un caractère dans la plage `A`–`Z`, et `[!H–L]` trouve une correspondance si la position de caractère correspondante contient un caractère à l'extérieur de la plage `H`–`L`.  
  
 Lorsque vous spécifiez une plage de caractères, ceux\-ci doivent apparaître dans l'ordre de tri croissant \(c'est\-à\-dire du premier au dernier\).  Ainsi, `[A–Z]` est un modèle valide, mais `[Z–A]` n'en est pas un.  
  
### Plage de caractères multiples  
 Pour spécifier plusieurs plages pour la même position, mettez les caractères entre crochets sans délimiteur.  Par exemple, `[A–CX–Z]` trouve une correspondance si la position du caractère correspondante dans la `string` contient les caractères compris dans la plage `A`–`C` ou `X`–`Z`.  
  
### Utilisation du trait d'union  
 Un trait d'union \(`–) peut apparaître soit au début (après un point d'exclamation, le cas échéant), soit à la fin de` `charlist` pour correspondre à lui\-même.  À tout autre endroit, le trait d'union identifie une plage de caractères délimitée par les caractères de part et d'autre du trait d'union.  
  
## Table de classement  
 La signification d'une plage spécifiée dépend de l'ordre des caractères au moment de l'exécution \(comme défini par `Option` `Compare` et les paramètres régionaux du système sur lequel s'exécute le code\).  Avec `Option` `Compare` `Binary`, la plage `[A–E]` correspond à `A`, `B`, `C`, `D`, et `E`.  Avec `Option` `Compare` `Text`, `[A–E]` correspond à `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E` et `e`.  La plage ne correspond pas `Ê` ou `ê` parce que les caractères accentués sont classés après les caractères inaccentués dans l'ordre de tri.  
  
## Caractères digrammes  
 Dans certaines langues, certains caractères alphabétiques représentent deux caractères séparés.  Par exemple, plusieurs langues utilisent le caractère `æ` pour représenter le caractère `a` et le caractère `e` lorsqu'ils apparaissent ensemble.  L'opérateur `Like` reconnaît l'équivalence du caractère digramme simple et des deux caractères individuels.  
  
 Lorsqu'une langue qui utilise un caractère digramme est spécifiée dans les paramètres régionaux du système, une occurrence du caractère digramme simple dans `pattern` ou `string` correspond à la séquence équivalente de deux caractères dans l'autre chaîne.  De même, un caractère digramme dans `pattern` placé entre crochets \(tout seul, dans une liste ou dans une plage\) correspond à la séquence équivalente de deux caractères dans `string`.  
  
## Surcharge  
 L'opérateur `Like` peut être *surchargé*, ce qui signifie qu'une classe ou une structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou de cette structure.  Si votre code utilise cet opérateur sur une telle classe ou structure, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 Cet exemple utilise l'opérateur `Like` pour comparer des chaînes de plusieurs modèles.  Les résultats se dirigent vers une variable `Boolean` qui indique si chaque chaîne satisfait le modèle.  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>   
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>   
 [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)