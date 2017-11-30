---
title: Instructions dans Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:) [Visual Basic]
- constants [Visual Basic], defining
- underlines
- constants [Visual Basic], statements
- blue underline [Visual Basic]
- procedures [Visual Basic], statements
- variables [Visual Basic], assigning
- line breaks [Visual Basic], in code
- executable statements [Visual Basic]
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 210637105e54244ba829dabd73feab0b43ec7c6c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="statements-in-visual-basic"></a>Instructions dans Visual Basic
Une instruction dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] est une instruction complète. Il peut contenir des mots clés, des opérateurs, des variables, des constantes et des expressions. Chaque instruction appartient à une des catégories suivantes :  
  
-   **Les instructions de déclaration**, qui nommer une variable, une constante ou une procédure et que vous pouvez également spécifier un type de données.  
  
-   **Instructions exécutables**, laquelle lancer des actions. Ces instructions peuvent appeler une méthode ou une fonction, et ils peuvent parcourir ou créer des branches de blocs de code. Les instructions exécutables contiennent **instructions d’assignation**, qui affectent une valeur ou une expression à une variable ou constante.  
  
 Cette rubrique décrit chaque catégorie. En outre, cette rubrique décrit comment combiner plusieurs instructions sur une seule ligne et comment continuer une instruction sur plusieurs lignes.  
  
## <a name="declaration-statements"></a>Instructions de déclaration  
 Les instructions de déclaration vous permet de nommer et de définir des procédures, des variables, des propriétés, des tableaux et des constantes. Lorsque vous déclarez un élément de programmation, vous pouvez également définir son type de données, le niveau d’accès et la portée. Pour plus d’informations, consultez [caractéristiques de l’élément déclaré](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
 L’exemple suivant contient trois déclarations.  
  
 [!code-vb[VbVbalrStatements#80](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_1.vb)]  
  
 La première déclaration est la `Sub` instruction. Ainsi que sa mise en correspondance `End Sub` instruction, elle déclare une procédure nommée `applyFormat`. Il spécifie également que `applyFormat` est `Public`, ce qui signifie que tout code qui peut faire référence à ce dernier peut appeler.  
  
 La seconde déclaration est la `Const` instruction qui déclare la constante `limit`, en spécifiant le `Integer` type de données et la valeur 33.  
  
 La troisième déclaration est la `Dim` instruction qui déclare la variable `thisWidget`. Le type de données est un objet spécifique, à savoir un objet créé à partir de la `Widget` classe. Vous pouvez déclarer une variable qui doit être de n’importe quel type de données élémentaire ou de tout type d’objet qui est exposé dans l’application que vous utilisez.  
  
### <a name="initial-values"></a>Valeurs initiales  
 Lorsque le code contenant une instruction de déclaration s’exécute, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] réserve la mémoire requise pour l’élément déclaré. Si l’élément contient une valeur, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] initialise à la valeur par défaut pour son type de données. Pour plus d’informations, consultez « Comportement » dans [instruction Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
 Vous pouvez affecter une valeur initiale à une variable dans le cadre de sa déclaration, comme l’illustre l’exemple suivant.  
  
 [!code-vb[VbVbalrStatements#81](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_2.vb)]  
  
 Si une variable est une variable objet, vous pouvez créer explicitement une instance de la classe lorsque vous la déclarez à l’aide de la [nouvel opérateur](../../../visual-basic/language-reference/operators/new-operator.md) (mot clé), comme l’exemple suivant illustre.  
  
 [!code-vb[VbVbalrStatements#82](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_3.vb)]  
  
 Notez que la valeur initiale que vous spécifiez dans une instruction de déclaration n’est pas attribuée à une variable jusqu'à ce que l’exécution atteint son instruction de déclaration. En attendant, la variable contient la valeur par défaut pour son type de données.  
  
## <a name="executable-statements"></a>Instructions exécutables  
 Une instruction exécutable effectue une action. Il peut appeler une procédure, une branche vers un autre emplacement dans le code, parcourir plusieurs instructions, ou évaluer une expression. Une instruction d’assignation est un cas spécial d’une instruction exécutable.  
  
 L’exemple suivant utilise une `If...Then...Else` structure pour exécuter différents blocs de code en fonction de la valeur d’une variable de contrôle. Dans chaque bloc de code, un `For...Next` boucle s’exécute un nombre spécifié de fois.  
  
 [!code-vb[VbVbalrStatements#83](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_4.vb)]  
  
 Le `If` instruction dans l’exemple précédent vérifie la valeur du paramètre `clockwise`. Si la valeur est `True`, il appelle la `spinClockwise` méthode `aWidget`. Si la valeur est `False`, il appelle la `spinCounterClockwise` méthode `aWidget`. Le `If...Then...Else` structure de contrôle se termine par `End If`.  
  
 Le `For...Next` boucle à l’intérieur de chaque bloc appelle la méthode appropriée un nombre de fois égal à la valeur de le `revolutions` paramètre.  
  
## <a name="assignment-statements"></a>Instructions d’assignation  
 Instructions d’assignation exécutent des opérations d’assignation qui consistent à prendre la valeur située à droite de l’opérateur d’assignation (`=`) et son stockage dans l’élément sur la gauche, comme dans l’exemple suivant.  
  
 [!code-vb[VbVbalrStatements#73](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_5.vb)]  
  
 Dans l’exemple précédent, l’instruction d’assignation stocke la valeur littérale 42 dans la variable `v`.  
  
### <a name="eligible-programming-elements"></a>Éléments de programmation disponibles  
 L’élément de programmation sur le côté gauche de l’opérateur d’assignation doit être en mesure d’accepter et de stocker une valeur. Cela signifie qu’il doit être une variable ou une propriété qui n’est pas [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), ou il doit être un élément de tableau. Dans le contexte d’une instruction d’assignation, un tel élément est parfois appelé un *lvalue*, pour « left value ».  
  
 La valeur située à droite de l’opérateur d’assignation est générée par une expression qui peut être constitué de n’importe quelle combinaison de littéraux, de constantes, variables, propriétés, éléments de tableau, autres expressions ou les appels de fonction. L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrStatements#74](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_6.vb)]  
  
 L’exemple précédent ajoute la valeur contenue dans la variable `y` à la valeur contenue dans la variable `z`, puis ajoute la valeur retournée par l’appel de fonction `findResult`. La valeur totale de cette expression est ensuite stockée dans la variable `x`.  
  
### <a name="data-types-in-assignment-statements"></a>Types de données dans les instructions d’assignation  
 Outre les valeurs numériques, l’opérateur d’assignation peut également affecter `String` des valeurs, comme l’illustre l’exemple suivant.  
  
 [!code-vb[VbVbalrStatements#75](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_7.vb)]  
  
 Vous pouvez également affecter `Boolean` des valeurs, en utilisant soit un `Boolean` littéral ou un `Boolean` expression, comme l’exemple suivant illustre.  
  
 [!code-vb[VbVbalrStatements#76](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_8.vb)]  
  
 De même, vous pouvez assigner des valeurs appropriées aux éléments de programmation le `Char`, `Date`, ou `Object` type de données. Vous pouvez également affecter une instance d’objet à un élément déclaré comme étant de la classe à partir de laquelle cette instance est créée.  
  
### <a name="compound-assignment-statements"></a>Instructions d’assignation composée  
 *Instructions d’assignation composée* tout d’abord effectuer une opération sur une expression avant de l’assigner à un élément de programmation. L’exemple suivant illustre l’un de ces opérateurs, `+=`, qui incrémente la valeur de la variable sur le côté gauche de l’opérateur par la valeur de l’expression de droite.  
  
 [!code-vb[VbVbalrStatements#77](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_9.vb)]  
  
 L’exemple précédent ajoute 1 à la valeur de `n`, puis stocke cette nouvelle valeur dans `n`. Il s’agit d’une propriété raccourcie équivalent de l’instruction suivante :  
  
 [!code-vb[VbVbalrStatements#78](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_10.vb)]  
  
 Un ensemble d’opérations d’assignation composée peut être effectué à l’aide des opérateurs de ce type. Pour obtenir la liste de ces opérateurs et plus d’informations à leur sujet, consultez [opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md).  
  
 L’opérateur d’assignation de concaténation (`&=`) est utile pour ajouter une chaîne à la fin d’existe déjà des chaînes, comme l’illustre l’exemple suivant.  
  
 [!code-vb[VbVbalrStatements#79](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_11.vb)]  
  
### <a name="type-conversions-in-assignment-statements"></a>Conversions de type dans les instructions d’assignation  
 La valeur que vous assignez à une variable, une propriété ou un élément de tableau doit être un type de données approprié pour cet élément de destination. En règle générale, vous devez tenter de générer une valeur du même type de données que celui de l’élément de destination. Toutefois, certains types peuvent être convertis en d’autres types lors de l’attribution.  
  
 Pour plus d’informations sur la conversion entre types de données, consultez [en Visual Basic, les Conversions de Type](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md). En bref, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] convertit automatiquement une valeur d’un type donné en un autre type auquel elle s’étend. A *conversion étendue* est un qui réussit au moment de l’exécution toujours et que vous ne perdez pas de données. Par exemple, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] convertit un `Integer` valeur `Double` quand cela est approprié, car `Integer` s’étend à `Double`. Pour plus d’informations, consultez [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 *Les conversions restrictives* (celles qui ne sont pas étendues) comportent un risque de défaillance au moment de l’exécution, ou de perte de données. Vous pouvez effectuer une conversion restrictive explicitement à l’aide d’une fonction de conversion de type, ou vous pouvez demander au compilateur d’effectuer toutes les conversions implicitement en définissant `Option Strict Off`. Pour plus d’informations, consultez [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## <a name="putting-multiple-statements-on-one-line"></a>Placement de plusieurs instructions sur une seule ligne  
 Vous pouvez avoir plusieurs instructions sur une seule ligne, séparées par le signe deux-points (`:`) caractères. L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrStatements#70](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_12.vb)]  
  
 Souvent, ce type de syntaxe rend votre code difficile à lire et à gérer. Par conséquent, il est recommandé de conserver une seule instruction sur une ligne.  
  
## <a name="continuing-a-statement-over-multiple-lines"></a>Suite d’une instruction sur plusieurs lignes  
 Une instruction tient généralement sur une seule ligne, mais lorsqu’il est trop long, vous pouvez la continuer sur la ligne suivante à l’aide d’une séquence de continuation de ligne, qui se compose d’un espace suivi par un caractère de soulignement (`_`) suivi d’un retour chariot. Dans l’exemple suivant, la `MsgBox` instruction exécutable se poursuit sur deux lignes.  
  
 [!code-vb[VbVbalrStatements#71](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_13.vb)]  
  
### <a name="implicit-line-continuation"></a>Continuation de ligne implicite  
 Dans de nombreux cas, vous pouvez continuer une instruction sur la ligne consécutive suivante sans utiliser le caractère de soulignement (_). Le tableau suivant répertorie les éléments de syntaxe qui continuent implicitement l’instruction sur la ligne de code suivante.  
  
|Élément de syntaxe|Exemple|  
|---|---|  
|Après une virgule (`,`).|[!code-vb[VbVbalrLineContinuation#1](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_14.vb)]|  
|Après une parenthèse ouvrante (`(`) ou avant une parenthèse fermante (`)`).|[!code-vb[VbVbalrLineContinuation#2](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_15.vb)]|  
|Après une accolade ouvrante (`{`) ou avant une accolade fermante (`}`).|[!code-vb[VbVbalrLineContinuation#3](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_16.vb)]<br /><br /> Pour plus d’informations, consultez [initialiseurs d’objets : Types nommés et anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) ou [initialiseurs de Collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
|Après avoir ouvert expression incorporée (`<%=`) ou avant la fermeture d’une expression incorporée (`%>`) dans un littéral XML.|[!code-vb[VbVbalrLineContinuation#4](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_17.vb)]<br /><br /> Pour plus d’informations, consultez [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
|Après l’opérateur de concaténation (`&`).|[!code-vb[VbVbcnConventions#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_18.vb)]<br /><br /> Pour plus d’informations, consultez [opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Après les opérateurs d’assignation (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`).|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br /><br /> Pour plus d’informations, consultez [opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Après les opérateurs binaires (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) dans une expression.|[!code-vb[VbVbalrLineContinuation#7](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_20.vb)]<br /><br /> Pour plus d’informations, consultez [opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Après le `Is` et `IsNot` opérateurs.|[!code-vb[VbVbalrLineContinuation#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_21.vb)]<br /><br /> Pour plus d’informations, consultez [opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Après un caractère d’identificateur de membre (`.`) et avant le nom du membre. Toutefois, vous devez inclure un caractère de continuation de ligne (_) après un caractère de qualificateur de membre lorsque vous utilisez la `With` instruction ou indiquez des valeurs dans la liste d’initialisation d’un type. Arrêtez la ligne après l’opérateur d’assignation (par exemple, `=`) lorsque vous utilisez `With` instructions ou des listes d’initialisation d’objets.|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br />[!code-vb[VbVbalrLineContinuation#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_22.vb)]<br /><br /> Pour plus d’informations, consultez [avec... End With, instruction](../../../visual-basic/language-reference/statements/with-end-with-statement.md) ou [initialiseurs d’objets : Types nommés et anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).|  
|Après un qualificateur de propriété d’axe XML (`.` ou `.@` ou `...`). Toutefois, vous devez inclure un caractère de continuation de ligne (_) lorsque vous spécifiez un qualificateur de membre lorsque vous utilisez la `With` (mot clé).|[!code-vb[VbVbalrLineContinuation#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_23.vb)]<br /><br /> Pour plus d’informations, consultez [propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).|  
|Après un inférieur-signe < (inférieur à) ou avant une meilleure-signe (`>`) lorsque vous spécifiez un attribut. Également après un supérieur-signe (`>`) lorsque vous spécifiez un attribut. Toutefois, vous devez inclure un caractère de continuation de ligne (_) lorsque vous spécifiez les attributs de niveau assembly ou au niveau du module.|[!code-vb[VbVbalrLineContinuation#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_24.vb)]<br /><br /> Pour plus d’informations, consultez [vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md).|  
|Avant et après les opérateurs de requête (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, et `Descending`). Vous ne pouvez pas de saut de ligne entre les mots clés des opérateurs de requête qui sont composés de plusieurs mots clés (`Order By`, `Group Join`, `Take While`, et `Skip While`).|[!code-vb[VbVbalrLineContinuation#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_25.vb)]<br /><br /> Pour plus d’informations, consultez [requêtes](../../../visual-basic/language-reference/queries/queries.md).|  
|Après le `In` mot clé dans un `For Each` instruction.|[!code-vb[VbVbalrLineContinuation#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_26.vb)]<br /><br /> Pour plus d’informations, consultez [For Each... L’instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md).|  
|Après le `From` mot clé dans un initialiseur de collection.|[!code-vb[VbVbalrLineContinuation#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_27.vb)]<br /><br /> Pour plus d’informations, consultez [Initialiseurs de collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
  
## <a name="adding-comments"></a>L’ajout de commentaires  
 Code source n’est pas toujours évident, même pour le programmeur qui l’a écrit. Pour vous aider à documenter leur code, la plupart des programmeurs donc l’utilisation répandue des commentaires incorporés. Commentaires dans le code peuvent expliquer une procédure ou une instruction particulière à toute personne lors de la lecture ou de son utilisation ultérieure. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]ignore les commentaires pendant la compilation, et ils n’affectent pas le code compilé.  
  
 Les lignes de commentaire commencent par une apostrophe (`'`) ou `REM` suivi d’un espace. Ils peuvent être ajoutés n’importe où dans le code, sauf dans une chaîne. Pour ajouter un commentaire à une instruction, insérez une apostrophe ou `REM` après l’instruction, suivie du commentaire. Commentaires peuvent également passer sur leur propre ligne distincte. L’exemple suivant illustre ces possibilités.  
  
 [!code-vb[VbVbalrStatements#72](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_28.vb)]  
  
## <a name="checking-compilation-errors"></a>Vérification des erreurs de Compilation  
 Si, après avoir tapé une ligne de code, la ligne est affichée par un soulignement ondulé bleu (un message d’erreur peut également apparaître), il existe une erreur de syntaxe dans l’instruction. Vous devez savoir quel est le problème avec l’instruction (en recherchant dans la liste des tâches, ou vous pointez sur l’erreur avec le pointeur de la souris et le message d’erreur lors de la lecture) et corrigez-le. Jusqu'à ce que vous avez résolu toutes les erreurs de syntaxe dans votre code, votre programme échoue pour une compilation correcte.  
  
## <a name="related-sections"></a>Rubriques connexes  
  
|Terme|Définition|  
|---|---|  
|[Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md)|Fournit des liens vers les pages de référence du langage couvrant tels que les opérateurs d’assignation `=`, `*=`, et `&=`.|  
|[Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)|Montre comment combiner des éléments avec des opérateurs pour retourner de nouvelles valeurs.|  
|[Guide pratique : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Montre comment arrêter une instruction unique en plusieurs lignes et comment placer plusieurs instructions sur la même ligne.|  
|[Guide pratique : étiqueter des instructions](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Montre comment étiqueter une ligne de code.|
