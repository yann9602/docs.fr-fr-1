---
title: "Comment : faire correspondre une chaîne à un modèle (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83433bdb41df0ce40d0979f3f44603f10ba1c7d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>Comment : faire correspondre une chaîne à un modèle (Visual Basic)
Si vous souhaitez savoir si une expression de la [Type de données String](../../../../visual-basic/language-reference/data-types/string-data-type.md) répond à un modèle, vous pouvez ensuite utiliser le [opérateur Like](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
 `Like`utilise deux opérandes. L’opérande gauche est une expression de chaîne, et l’opérande de droite est une chaîne qui contient le modèle à utiliser pour la correspondance. `Like`Retourne un `Boolean` valeur qui indique si l’expression de chaîne est conforme au modèle.  
  
 Vous pouvez faire correspondre chaque caractère de l’expression de chaîne avec un caractère spécifique, un caractère générique, une liste de caractères ou une plage de caractères. Les positions des spécifications dans la chaîne de masque correspondent aux positions des caractères de correspondance dans l’expression de chaîne.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>Pour mettre en correspondance un caractère de l’expression de chaîne avec un caractère spécifique  
  
-   Placez le caractère spécifique directement dans la chaîne de modèle. Certains caractères spéciaux doivent être entourés de crochets (`[ ]`). Pour plus d’informations, consultez [opérateur Like](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
     L’exemple suivant teste si `myString` se compose exactement du caractère `H`.  
  
     [!code-vb[VbVbalrOperators#70](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>Pour mettre en correspondance un caractère de l’expression de chaîne avec un caractère générique  
  
-   Placez un point d’interrogation (`?`) dans la chaîne de modèle. N’importe quel caractère valide dans cette position rend une correspondance.  
  
     L’exemple suivant teste si `myString` se compose d’un caractère unique `W` suivi exactement deux caractères de toutes les valeurs.  
  
     [!code-vb[VbVbalrOperators#71](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>Pour mettre en correspondance un caractère dans l’expression de chaîne par rapport à une liste de caractères  
  
-   Mettez des crochets (`[ ]`) dans la chaîne de modèle et à l’intérieur de crochets, mettez la liste des caractères. Ne séparez pas les caractères par des virgules ou tout autre séparateur. Tout caractère unique dans la liste effectue une correspondance.  
  
     L’exemple suivant teste si `myString` se compose d’un caractère valide, suivi par une seule des caractères `A`, `C`, ou `E`.  
  
     [!code-vb[VbVbalrOperators#72](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]  
  
     Notez que cette correspondance respecte la casse.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>Pour mettre en correspondance un caractère de l’expression de chaîne avec une plage de caractères  
  
-   Mettez des crochets (`[ ]`) dans la chaîne de modèle et à l’intérieur de crochets, mettez les caractères les plus élevés dans la plage, séparés par un trait d’union (`–`). N’importe quel caractère unique dans la plage effectue une correspondance.  
  
     L’exemple suivant teste si `myString` se compose de caractères `num` suivi par une seule des caractères `i`, `j`, `k`, `l`, `m`, ou `n`.  
  
     [!code-vb[VbVbalrOperators#73](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]  
  
     Notez que cette correspondance respecte la casse.  
  
## <a name="matching-empty-strings"></a>Correspondance des chaînes vides  
 `Like`traite la séquence `[]` comme une chaîne de longueur nulle (`""`). Vous pouvez utiliser `[]` pour tester si l’expression d’ensemble de la chaîne est vide, mais vous ne pouvez pas l’utiliser pour tester si une position donnée dans l’expression de chaîne est vide. Si une position vide est une des options que vous devez tester, vous pouvez utiliser `Like` plusieurs fois.  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>Pour mettre en correspondance un caractère dans l’expression de chaîne par rapport à une liste de caractères ou aucun caractère  
  
1.  Appeler le `Like` opérateur deux fois sur la même expression de chaîne et connectez les deux appels avec les [ou opérateur](../../../../visual-basic/language-reference/operators/or-operator.md) ou [opérateur OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
2.  Dans la chaîne de modèle pour la première `Like` clause, inclure la liste de caractères placés entourée crochets (`[ ]`).  
  
3.  Dans la chaîne de modèle pour la deuxième `Like` clause, ne placez pas n’importe quel caractère à la position en question.  
  
     L’exemple suivant teste le numéro de téléphone de sept chiffres `phoneNum` pour exactement trois chiffres, suivi d’un espace, un trait d’union (`–`), une période (`.`), ou aucun caractère, ne suivi par exactement quatre chiffres.  
  
     [!code-vb[VbVbalrOperators#74](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs de comparaison](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Opérateurs et expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Like (opérateur)](../../../../visual-basic/language-reference/operators/like-operator.md)  
 [String (type de données)](../../../../visual-basic/language-reference/data-types/string-data-type.md)
