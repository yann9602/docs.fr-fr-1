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
ms.openlocfilehash: 6d4b6e74ef3dfab3a7174da07cff7100fa4b2a2f
ms.lasthandoff: 03/13/2017

---
# <a name="special-characters-in-code-visual-basic"></a>Caractères spéciaux dans le code (Visual Basic)
Parfois, vous devez utiliser des caractères spéciaux dans votre code, autrement dit, les caractères qui ne sont pas alphabétiques ou numériques. Les signes de ponctuation et caractères spéciaux dans le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] jeu de caractères ont plusieurs utilisations, de l’organisation du texte de programme à la définition des tâches effectuées par le compilateur ou le programme compilé. Ils ne spécifient pas d'opération à effectuer.  
  
## <a name="parentheses"></a>Entre parenthèses  
 Utilisez des parenthèses lorsque vous définissez une procédure, comme un `Sub` ou `Function`. Vous devez placer toutes les listes d’arguments de procédure entre parenthèses. Vous également utiliser des parenthèses pour insérer des variables ou arguments en groupes logiques, en particulier pour substituer l’ordre de priorité des opérateurs dans une expression complexe par défaut. L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbcnConventions&#11;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 Après l’exécution du code précédent, la valeur de `d` est 8.225 et la valeur de `e` est 3. Le calcul de `d` utilise la priorité par défaut de `/` sur `+` et équivaut à `d = b + (c / a)`. Les parenthèses dans le calcul de `e` la priorité par défaut.  
  
## <a name="separators"></a>Séparateurs  
 Séparateurs de faire ce que leur nom suggère : séparent les différentes sections de code. Dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], le caractère de séparation est le signe deux-points (`:`). Utilisez des séparateurs lorsque vous voulez inclure plusieurs instructions sur une seule ligne au lieu de lignes distinctes. Cela économise de l’espace et améliore la lisibilité de votre code. L’exemple suivant montre les trois instructions sont séparées par un signe deux-points.  
  
 [!code-vb[VbVbcnConventions&#12;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 Pour plus d’informations, consultez [Comment : interrompre et combiner des instructions dans le Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
 Le signe deux-points (`:`) caractères sont également utilisé pour identifier une étiquette d’instruction. Pour plus d’informations, consultez [Comment : Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## <a name="concatenation"></a>Concaténation  
 Utilisez le `&` opérateur pour *concaténation*, ou lier plusieurs chaînes. Ne confondez pas avec le `+` opérateur, qui additionne les valeurs numériques. Si vous utilisez le `+` pour concaténer lorsque vous utilisez des valeurs numériques, vous pouvez obtenir des résultats incorrects. Cela est illustré par l'exemple suivant.  
  
 [!code-vb[VbVbcnConventions&#13;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 Après l’exécution du code précédent, la valeur de `resultA` est 21.01 et la valeur de `resultB` est « 10.0111 ».  
  
## <a name="member-access-operators"></a>Opérateurs d’accès au membre  
 Pour accéder à un membre d’un type, utilisez le point (`.`) ou un point d’exclamation (`!`) opérateur entre le nom de type et le nom du membre.  
  
### <a name="dot--operator"></a>Point (.) Opérateur  
 Utilisez le `.` opérateur sur une classe, une structure, une interface ou une énumération comme un opérateur d’accès au membre. Le membre peut être un champ, une propriété, un événement ou une méthode. L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbcnConventions&#14;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### <a name="exclamation-point--operator"></a>Point d’exclamation ( !) Opérateur  
 Utilisez le `!` opérateur uniquement sur une classe ou une interface comme un opérateur d’accès au dictionnaire. La classe ou interface doit avoir une propriété par défaut qui accepte un seul `String` argument. L’identificateur qui suit immédiatement la `!` devient la valeur de l’argument passée à la propriété par défaut sous forme de chaîne. Cela est illustré par l'exemple suivant.  
  
 [!code-vb[VbVbcnConventions&#15;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 Les trois lignes de sortie de `MsgBox` tous affichent la valeur `32856`. La première ligne utilise l’accès traditionnel à la propriété `index`, la seconde utilise le fait que `index` est la propriété par défaut de la classe `hasDefault`, et la troisième utilise l’accès au dictionnaire à la classe.  
  
 Notez que le deuxième opérande de le `!` opérateur doit être un identificateur Visual Basic valide ne pas entouré de guillemets doubles (`" "`). En d’autres termes, vous ne pouvez pas utiliser un littéral de chaîne ou une variable de chaîne. La modification ci-dessous à la dernière ligne de la `MsgBox` appel génère une erreur car `"X"` est une chaîne entre parenthèses littéral.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  Références aux collections par défaut doivent être explicites. En particulier, vous ne pouvez pas utiliser le `!` opérateur sur une variable à liaison tardive.  
  
 Le `!` caractère est également utilisé comme le `Single` caractère de type.  
  
## <a name="see-also"></a>Voir aussi  
 [Structure de programme et Conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Caractères de type](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
