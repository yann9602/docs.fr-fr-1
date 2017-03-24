---
title: Instructions dans Visual Basic | Documents Microsoft
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
- variables [Visual Basic], declaring
- colons (:)
- constants, defining
- underlines
- constants, statements
- blue underline
- procedures, statements
- variables [Visual Basic], assigning
- line breaks, in code
- executable statements
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
caps.latest.revision: 30
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
ms.openlocfilehash: 001ea1cb5e651b95f808eefd47fd468f556550a1
ms.lasthandoff: 03/13/2017

---
# <a name="statements-in-visual-basic"></a>Instructions dans Visual Basic
Une instruction [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] est une instruction complète. Il peut contenir des mots clés, des opérateurs, des variables, des constantes et des expressions. Chaque instruction appartient à une des catégories suivantes :  
  
-   **Instructions de déclaration**, nommer une variable, une constante ou une procédure et qui peuvent également spécifier un type de données.  
  
-   **Instructions exécutables**, laquelle lancer des actions. Ces instructions peuvent appeler une méthode ou une fonction, et peuvent parcourir ou créer des branches de blocs de code. Les instructions exécutables contiennent **instructions d’assignation**, qui affectent une valeur ou une expression à une variable ou constante.  
  
 Cette rubrique décrit chaque catégorie. En outre, cette rubrique décrit comment combiner plusieurs instructions sur une seule ligne et comment continuer une instruction sur plusieurs lignes.  
  
## <a name="declaration-statements"></a>Instructions de déclaration  
 Instructions de déclaration vous permet de nommer et de définir des procédures, des variables, des propriétés, des tableaux et des constantes. Lorsque vous déclarez un élément de programmation, vous pouvez également définir son type de données, le niveau d’accès et la portée. Pour plus d’informations, consultez [caractéristiques d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
 L’exemple suivant contient trois déclarations.  
  
 [!code-vb[VbVbalrStatements&#80;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_1.vb)]  
  
 La première déclaration est la `Sub` instruction. Avec sa mise en correspondance `End Sub` instruction, elle déclare une procédure nommée `applyFormat`. Il spécifie également que `applyFormat` est `Public`, ce qui signifie que tout code qui peut faire peut appeler.  
  
 La deuxième déclaration est la `Const` instruction qui déclare la constante `limit`, en spécifiant le `Integer` type de données et une valeur 33.  
  
 La troisième déclaration est la `Dim` instruction qui déclare la variable `thisWidget`. Le type de données est un objet spécifique, à savoir un objet créé à partir de la `Widget` classe. Vous pouvez déclarer une variable de n’importe quel type de données élémentaire ou de tout type d’objet qui est exposé dans l’application que vous utilisez.  
  
### <a name="initial-values"></a>Valeurs initiales  
 Lorsque le code contenant une instruction de déclaration s’exécute, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] réserve la mémoire requise pour l’élément déclaré. Si l’élément contient une valeur, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] initialise à la valeur par défaut pour son type de données. Pour plus d’informations, consultez « Comportement » dans [une instruction Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
 Vous pouvez affecter une valeur initiale à une variable dans le cadre de sa déclaration, comme l’illustre l’exemple suivant.  
  
 [!code-vb[VbVbalrStatements&#81;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_2.vb)]  
  
 Si une variable est une variable objet, vous pouvez créer explicitement une instance de sa classe lorsque vous la déclarez à l’aide de la [nouveau opérateur](../../../visual-basic/language-reference/operators/new-operator.md) (mot clé), comme l’exemple suivant illustre.  
  
 [!code-vb[VbVbalrStatements&#82;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_3.vb)]  
  
 Notez que la valeur initiale que vous spécifiez dans une instruction de déclaration n'est pas affectée à une variable jusqu'à ce que l’exécution atteint son instruction de déclaration. En attendant, la variable contient la valeur par défaut pour son type de données.  
  
## <a name="executable-statements"></a>Instructions exécutables  
 Une instruction exécutable effectue une action. Elle peut appeler une procédure, la branche à un autre emplacement dans le code, parcourir plusieurs instructions, ou évaluer une expression. Une instruction d’assignation est un cas spécial d’une instruction exécutable.  
  
 L’exemple suivant utilise un `If...Then...Else` structure pour exécuter différents blocs de code selon la valeur d’une variable de contrôle. Dans chaque bloc de code, un `For...Next` boucle s’exécute un nombre de fois spécifié.  
  
 [!code-vb[83 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_4.vb)]  
  
 Le `If` instruction dans l’exemple précédent vérifie la valeur du paramètre `clockwise`. Si la valeur est `True`, il appelle le `spinClockwise` méthode `aWidget`. Si la valeur est `False`, il appelle le `spinCounterClockwise` méthode `aWidget`. Le `If...Then...Else` structure de contrôle se termine par `End If`.  
  
 Le `For...Next` boucle à l’intérieur de chaque bloc appelle la méthode appropriée un nombre de fois égal à la valeur de le `revolutions` paramètre.  
  
## <a name="assignment-statements"></a>Instructions d’assignation  
 Instructions d’assignation effectuent des opérations d’assignation qui consistent à prendre la valeur située à droite de l’opérateur d’assignation (`=`) et en les stockant dans l’élément sur la gauche, comme dans l’exemple suivant.  
  
 [!code-vb[VbVbalrStatements&#73;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_5.vb)]  
  
 Dans l’exemple précédent, l’instruction d’assignation stocke la valeur littérale 42 dans la variable `v`.  
  
### <a name="eligible-programming-elements"></a>Éléments de programmation disponibles  
 L’élément de programmation sur le côté gauche de l’opérateur d’assignation doit être en mesure d’accepter et de stocker une valeur. Cela signifie qu’il doit être une variable ou une propriété qui n’est pas [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), ou il doit être un élément de tableau. Dans le contexte d’une instruction d’assignation, un tel élément est parfois appelé un *lvalue*, pour « valeur de gauche ».  
  
 La valeur située à droite de l’opérateur d’assignation est générée par une expression qui peut être composé de n’importe quelle combinaison de littéraux, constantes, variables, propriétés, éléments de tableau, les expressions ou les appels de fonction. L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrStatements&#74;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_6.vb)]  
  
 L’exemple précédent ajoute la valeur contenue dans la variable `y` à la valeur contenue dans la variable `z`, puis ajoute la valeur retournée par l’appel de fonction `findResult`. La valeur totale de cette expression est ensuite stockée dans la variable `x`.  
  
### <a name="data-types-in-assignment-statements"></a>Types de données dans les instructions d’assignation  
 En plus des valeurs numériques, l’opérateur d’assignation peut également assigner `String` valeurs, comme l’illustre l’exemple suivant.  
  
 [!code-vb[VbVbalrStatements&#75;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_7.vb)]  
  
 Vous pouvez également affecter `Boolean` à l’aide d’une des valeurs un `Boolean` littéral ou un `Boolean` expression, comme l’exemple suivant illustre.  
  
 [!code-vb[VbVbalrStatements&#76;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_8.vb)]  
  
 De même, vous pouvez assigner des valeurs appropriées aux éléments de programmation de la `Char`, `Date`, ou `Object` type de données. Vous pouvez également attribuer une instance d’objet à un élément déclaré comme étant de la classe à partir de laquelle cette instance est créée.  
  
### <a name="compound-assignment-statements"></a>Instructions d’assignation composée  
 *Instructions d’assignation composée* tout d’abord effectuer une opération sur une expression avant de l’assigner à un élément de programmation. L’exemple suivant illustre l’un de ces opérateurs, `+=`, qui incrémente la valeur de la variable sur le côté gauche de l’opérateur par la valeur de l’expression de droite.  
  
 [!code-vb[VbVbalrStatements&#77;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_9.vb)]  
  
 L’exemple précédent ajoute 1 à la valeur de `n`, puis stocke cette nouvelle valeur dans `n`. Il est un raccourci équivalente de l’instruction suivante :  
  
 [!code-vb[VbVbalrStatements&#78;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_10.vb)]  
  
 Un ensemble d’opérations d’assignation composée peut être effectué à l’aide d’opérateurs de ce type. Pour obtenir la liste de ces opérateurs et plus d’informations à leur sujet, consultez [opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md).  
  
 L’opérateur d’assignation de concaténation (`&=`) est utile pour ajouter une chaîne à la fin d’existants des chaînes, comme l’illustre l’exemple suivant.  
  
 [!code-vb[VbVbalrStatements&#79;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_11.vb)]  
  
### <a name="type-conversions-in-assignment-statements"></a>Conversions de type dans les instructions d’assignation  
 La valeur que vous assignez à une variable, une propriété ou un élément de tableau doit être un type de données approprié pour cet élément de destination. En général, vous devez tenter de générer une valeur du même type de données que celui de l’élément de destination. Toutefois, certains types peuvent être convertis en d’autres types lors de l’attribution.  
  
 Pour plus d’informations sur la conversion entre types de données, consultez [en Visual Basic, les Conversions de Type](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md). En bref, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] convertit automatiquement une valeur d’un type donné en un autre type auquel elle s’étend. A *conversion étendue* est une qui réussit au moment de l’exécution toujours et que vous ne perdez pas de données. Par exemple, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] convertit un `Integer` valeur `Double` le cas échéant, car `Integer` s’étend à `Double`. Pour plus d’informations, consultez [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 *Les conversions restrictives* (ceux qui ne sont pas étendues) comportent un risque de défaillance au moment de l’exécution, ou de perte de données. Vous pouvez effectuer explicitement une conversion restrictive en utilisant une fonction de conversion de type, ou vous pouvez demander au compilateur d’effectuer implicitement de toutes les conversions en définissant `Option Strict Off`. Pour plus d’informations, consultez [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## <a name="putting-multiple-statements-on-one-line"></a>Placement de plusieurs instructions sur une seule ligne  
 Vous pouvez avoir plusieurs instructions sur une seule ligne, séparés par le signe deux-points (`:`) caractères. L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrStatements&#70;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_12.vb)]  
  
 Souvent, ce type de syntaxe rend votre code difficile à lire et à gérer. Par conséquent, il est recommandé de conserver une instruction sur une ligne.  
  
## <a name="continuing-a-statement-over-multiple-lines"></a>Continuer une instruction sur plusieurs lignes  
 Une instruction tienne généralement sur une ligne, mais lorsqu’il est trop long, vous pouvez la continuer sur la ligne suivante à l’aide d’une séquence de continuation de ligne, qui se compose d’un espace suivi par un caractère de soulignement (`_`) suivie d’un retour chariot. Dans l’exemple suivant, la `MsgBox` instruction exécutable se poursuit sur deux lignes.  
  
 [!code-vb[VbVbalrStatements&#71;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_13.vb)]  
  
### <a name="implicit-line-continuation"></a>Continuation de ligne implicite  
 Dans de nombreux cas, vous pouvez continuer une instruction sur la ligne consécutive suivante sans utiliser le caractère de soulignement (_). Le tableau suivant répertorie les éléments de syntaxe qui continuent implicitement l’instruction sur la ligne de code suivante.  
  
|Élément de syntaxe|Exemple|  
|---|---|  
|Après une virgule (`,`).|[!code-vb[VbVbalrLineContinuation n °&1;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_14.vb)]|  
|Après une parenthèse ouvrante (`(`) ou avant une parenthèse fermante (`)`).|[!code-vb[VbVbalrLineContinuation n °&2;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_15.vb)]|  
|Après une accolade ouvrante (`{`) ou avant une accolade fermante (`}`).|[!code-vb[VbVbalrLineContinuation n °&3;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_16.vb)]<br /><br /> Pour plus d’informations, consultez [initialiseurs d’objets : Types nommés et anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) ou [initialiseurs de Collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
|Après avoir ouvert d’expression incorporée (`<%=`) ou avant la fermeture d’une expression incorporée (`%>`) dans un littéral XML.|[!code-vb[VbVbalrLineContinuation n °&4;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_17.vb)]<br /><br /> Pour plus d’informations, consultez [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
|Après l’opérateur de concaténation (`&`).|[!code-vb[VbVbcnConventions&#9;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_18.vb)]<br /><br /> Pour plus d’informations, consultez [opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|After assignment operators (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`).|[!code-vb[VbVbalrLineContinuation n °&5;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br /><br /> Pour plus d’informations, consultez [opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|After binary operators (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) within an expression.|[!code-vb[VbVbalrLineContinuation&#7;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_20.vb)]<br /><br /> Pour plus d’informations, consultez [opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Après le `Is` et `IsNot` opérateurs.|[!code-vb[VbVbalrLineContinuation n °&8;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_21.vb)]<br /><br /> Pour plus d’informations, consultez [opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Après un caractère de qualificateur de membre (`.`) et avant le nom du membre. Toutefois, vous devez inclure un caractère de continuation de ligne (_) après un caractère de qualificateur de membre lorsque vous utilisez la `With` instruction ou indiquez des valeurs dans la liste d’initialisation pour un type. Arrêtez la ligne après l’opérateur d’assignation (par exemple, `=`) lorsque vous utilisez `With` instructions ou des listes d’initialisation d’objets.|[!code-vb[VbVbalrLineContinuation n °&5;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br />[!code-vb[VbVbalrLineContinuation&#14;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_22.vb)]<br /><br /> Pour plus d’informations, consultez [avec... End With, instruction](../../../visual-basic/language-reference/statements/with-end-with-statement.md) ou [initialiseurs d’objets : Types nommés et anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).|  
|Après un qualificateur de propriété d’axe XML (`.` ou `.@` ou `...`). Toutefois, vous devez inclure un caractère de continuation de ligne (_) lorsque vous spécifiez un qualificateur de membre lorsque vous utilisez la `With` (mot clé).|[!code-vb[VbVbalrLineContinuation&#9;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_23.vb)]<br /><br /> Pour plus d’informations, consultez [propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).|  
|Après un inférieur-signe (<) or="" before="" a="" greater-than="" sign=""></)>`>`) lorsque vous spécifiez un attribut. Également après un signe supérieur-signe (`>`) lorsque vous spécifiez un attribut. Toutefois, vous devez inclure un caractère de continuation de ligne (_) lorsque vous spécifiez des attributs de niveau assembly ou au niveau du module.|[!code-vb[VbVbalrLineContinuation&#10;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_24.vb)]<br /><br /> Pour plus d’informations, consultez [vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md).|  
|Before and after query operators (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, and `Descending`). Vous ne pouvez pas interrompre une ligne entre les mots clés des opérateurs de requête qui sont composés de plusieurs mots clés (`Order By`, `Group Join`, `Take While`, et `Skip While`).|[!code-vb[VbVbalrLineContinuation&#11;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_25.vb)]<br /><br /> Pour plus d’informations, consultez [requêtes](../../../visual-basic/language-reference/queries/queries.md).|  
|Après le `In` mot clé dans un `For Each` instruction.|[!code-vb[VbVbalrLineContinuation&#12;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_26.vb)]<br /><br /> Pour plus d’informations, consultez [For Each... L’instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md).|  
|Après le `From` mot clé dans un initialiseur de collection.|[!code-vb[VbVbalrLineContinuation&#13;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_27.vb)]<br /><br /> Pour plus d’informations, consultez [initialiseurs de Collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
  
## <a name="adding-comments"></a>Ajout de commentaires  
 Code source n’est pas toujours explicatif, même pour le programmeur qui l’a écrit. Pour vous aider à documenter leur code, la plupart des programmeurs donc l’utilisation répandue des commentaires incorporés. Les commentaires dans le code peuvent expliquer une procédure ou une instruction particulière à toute lecture ou de son utilisation ultérieure. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ignore les commentaires pendant la compilation, et elles n’affectent pas le code compilé.  
  
 Les lignes de commentaire commencent par une apostrophe (`'`) ou `REM` suivi d’un espace. Ils peuvent être ajoutés n’importe où dans le code, sauf dans une chaîne. Pour ajouter un commentaire à une instruction, insérez une apostrophe ou `REM` après l’instruction, suivie du commentaire. Les commentaires peuvent également figurer sur leur propre ligne distincte. L’exemple suivant illustre ces possibilités.  
  
 [!code-vb[VbVbalrStatements&#72;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_28.vb)]  
  
## <a name="checking-compilation-errors"></a>Vérification des erreurs de Compilation  
 Si, après avoir tapé une ligne de code, la ligne est affichée par un soulignement ondulé bleu (un message d’erreur peut être également), il existe une erreur de syntaxe dans l’instruction. Vous devez savoir quel est le problème avec l’instruction (en recherchant dans la liste des tâches, ou pointant sur l’erreur avec le pointeur de la souris et lire le message d’erreur) et le corriger. Jusqu'à ce que vous avez résolu toutes les erreurs de syntaxe dans votre code, votre programme échouera se compile correctement.  
  
## <a name="related-sections"></a>Rubriques connexes  
  
|Terme|Définition|  
|---|---|  
|[Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md)|Fournit des liens vers les pages de référence du langage couvrant les opérateurs d’assignation comme `=`, `*=`, et `&=`.|  
|[Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)|Montre comment combiner des éléments avec des opérateurs pour retourner de nouvelles valeurs.|  
|[Guide pratique : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Montre comment diviser une instruction unique en plusieurs lignes et comment placer plusieurs instructions sur la même ligne.|  
|[Guide pratique : étiqueter des instructions](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Montre comment étiqueter une ligne de code.|
