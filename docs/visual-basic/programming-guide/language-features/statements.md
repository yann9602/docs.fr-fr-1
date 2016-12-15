---
title: "Statements in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], declaring"
  - "colons (:)"
  - "constants, defining"
  - "underlines"
  - "constants, statements"
  - "blue underline"
  - "procedures, statements"
  - "variables [Visual Basic], assigning"
  - "line breaks, in code"
  - "executable statements"
  - "variables [Visual Basic], defining"
  - "statements [Visual Basic], about statements"
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Statements in Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

En [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], une instruction est une entité complète.  Elle contient des mots clés, des opérateurs, des variables, des constantes et des expressions.  Chaque instruction appartient à l'une des catégories suivantes :  
  
-   **instructions de déclaration** qui nomment une variable, une constante ou une procédure et qui peuvent également spécifier un type de données ;  
  
-   **instructions exécutables** qui initient des actions.  Ces instructions peuvent appeler une méthode ou une fonction, et peuvent parcourir ou créer des branches de blocs de code.  Les instructions exécutables contiennent des **instructions d'assignation**, qui assignent une valeur ou une expression à une variable ou à une constante.  
  
 Cette rubrique décrit chaque catégorie.  Elle montre également comment combiner plusieurs instructions sur une ligne et comment continuer une instruction sur plusieurs lignes.  
  
## Instructions de déclaration  
 Les instructions de déclaration permettent de nommer et de définir des procédures, des variables, des propriétés, des tableaux et des constantes.  Lorsque vous déclarez un élément de programmation, vous pouvez également définir son type de données, son niveau d'accès et sa portée.  Pour plus d'informations, consultez [Declared Element Characteristics](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
 L'exemple suivant contient trois déclarations.  
  
 [!code-vb[VbVbalrStatements#80](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_1.vb)]  
  
 La première déclaration est l'instruction `Sub`.  Associée à son instruction `End Sub` correspondante, elle déclare une procédure nommée `applyFormat`.  Elle spécifie également que `applyFormat` a la valeur `Public`, ce qui signifie qu'un code qui peut y faire référence peut l'appeler.  
  
 La deuxième déclaration est l'instruction `Const` qui déclare la constante `limit`, en spécifiant le type de données `Integer` et la valeur 33.  
  
 La troisième déclaration est l'instruction `Dim`, qui déclare la variable `thisWidget`.  Le type de données est un objet spécifique, à savoir un objet créé à partir de la classe `Widget`.  Vous pouvez déclarer une variable comme étant d'un type de données élémentaire ou d'un type d'objet exposé dans l'application utilisée.  
  
### Valeurs initiales  
 Lorsque le code contenant une instruction de déclaration s'exécute, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] réserve la mémoire requise pour l'élément déclaré.  Si l'élément contient une valeur, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] l'initialise à la valeur par défaut de son type de données.  Pour plus d'informations, consultez « Comportement » dans [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
 Vous pouvez assigner une valeur initiale à une variable dans le cadre de sa déclaration, comme l'exemple suivant l'illustre.  
  
 [!code-vb[VbVbalrStatements#81](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_2.vb)]  
  
 Si votre variable est une variable objet, vous pouvez explicitement créer une instance de sa classe lorsque vous la déclarez à l'aide du mot clé [New Operator](../../../visual-basic/language-reference/operators/new-operator.md), comme indiqué dans l'exemple suivant  
  
 [!code-vb[VbVbalrStatements#82](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_3.vb)]  
  
 Notez que la valeur initiale que vous spécifiez dans une instruction de déclaration n'est pas assignée à une variable tant que l'exécution n'atteint pas son instruction de déclaration.  Jusqu'à ce moment, la variable contient la valeur par défaut de son type de données.  
  
## Instructions exécutables  
 Une instruction exécutable effectue une action.  Elle peut appeler une procédure, effectuer un branchement vers un autre emplacement du code, parcourir plusieurs instructions ou évaluer une expression.  Une instruction d'assignation est un cas spécial d'une instruction exécutable.  
  
 L'exemple suivant utilise une structure de contrôle `If...Then...Else` pour exécuter divers blocs de code selon la valeur d'une variable.  Une boucle `For...Next` s'exécute un certain nombre de fois dans chaque bloc de code.  
  
 [!code-vb[VbVbalrStatements#83](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_4.vb)]  
  
 L'instruction `If`de l'exemple précédent vérifie la valeur du paramètre `clockwise`.  Si la valeur est `True`, elle appelle la méthode `spinClockwise` de `aWidget`.  Si la valeur est `False`, elle appelle la méthode `spinCounterClockwise` de `aWidget`.  La structure de contrôle `If...Then...Else` se termine par `End If`.  
  
 La boucle `For...Next` à l'intérieur de chaque bloc appelle la méthode appropriée autant de fois que la valeur du paramètre `revolutions`.  
  
## Instructions d'assignation  
 Les instructions d'assignation exécutent des opérations d'assignation qui consistent à prendre la valeur située à droite de l'opérateur d'assignation \(`=`\) et à la stocker dans l'élément situé à gauche, comme dans l'exemple suivant.  
  
 [!code-vb[VbVbalrStatements#73](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_5.vb)]  
  
 Dans l'exemple précédent, l'instruction d'assignation stocke la valeur littérale 42 dans la variable `v`.  
  
### Éléments de programmation admissibles  
 L'élément de programmation situé à gauche de l'opérateur d'assignation doit être en mesure d'accepter et de stocker une valeur.  En d'autres termes, il doit être une variable ou une propriété qui n'est pas [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), ou encore il doit être un élément de tableau.  Dans le contexte d'une instruction d'assignation, un tel élément est parfois appelé *lvalue*, pour « valeur de gauche ».  
  
 La valeur située à droite de l'opérateur d'assignation est générée par une expression qui peut être composée de n'importe quelle combinaison de littéraux, de constantes, de variables, de propriétés, d'éléments de tableau, d'autres expressions ou d'appels de fonctions.  L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrStatements#74](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_6.vb)]  
  
 L'exemple précédent ajoute la valeur contenue dans la variable `y` à celle qui est contenue dans la variable `z`variable, puis ajoute la valeur retournée par l'appel à la fonction `findResult`.  La valeur totale de cette expression est ensuite stockée dans la variable `x`.  
  
### Types de données dans les instructions d'assignation  
 Outre les valeurs numériques, l'opérateur d'assignation peut également assigner des valeurs `String`, comme le montre l'exemple suivant.  
  
 [!code-vb[VbVbalrStatements#75](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_7.vb)]  
  
 Vous pouvez également assigner des valeurs `Boolean` à l'aide d'un littéral `Boolean` ou d'une expression `Boolean`, comme le montre l'exemple suivant.  
  
 [!code-vb[VbVbalrStatements#76](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_8.vb)]  
  
 De même, vous pouvez assigner des valeurs appropriées aux éléments de programmation du type de données `Char`, `Date` ou `Object`.  Vous pouvez également assigner une instance d'objet à un élément a déclaré pour faire partie de la classe dans laquelle cette instance est créée.  
  
### Instructions d'assignation composée  
 Les *instructions d'assignation composée* exécutent en premier lieu une opération sur une expression avant de l'assigner à un élément de programmation.  L'exemple suivant illustre l'un de ces opérateurs, `+=`, qui incrémente la valeur de la variable située à gauche de l'opérateur par la valeur de l'expression de droite.  
  
 [!code-vb[VbVbalrStatements#77](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_9.vb)]  
  
 L'exemple précédent ajoute 1 à la valeur de `n`, puis stocke cette nouvelle valeur dans `n`.  C'est l'équivalent abrégé de l'instruction suivante :  
  
 [!code-vb[VbVbalrStatements#78](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_10.vb)]  
  
 Les opérateurs de ce type permettent d'effectuer de nombreuses opérations d'assignation composées.  Pour obtenir la liste de ces opérateurs et en savoir davantage sur eux, consultez [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md).  
  
 Enfin, l'opérateur d'assignation de concaténation \(`&=`\) est utile pour ajouter une chaîne à la fin de chaînes déjà existantes, comme le montre l'exemple suivant :  
  
 [!code-vb[VbVbalrStatements#79](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_11.vb)]  
  
### Conversions de types dans les instructions d'assignation  
 La valeur que vous assignez à une variable, une propriété ou un élément de tableau doit être un type de données approprié pour cet élément de destination.  En général, vous devez essayer de générer une valeur du même type de données que celui de l'élément de destination.  Toutefois, certains types peuvent être convertis en d'autres types au cours de l'assignation.  
  
 Pour plus d'informations sur la conversion entre types de données, consultez [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md).  En résumé, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] convertit automatiquement une valeur d'un type donné en un autre type auquel elle s'étend.  Une *conversion étendue* réussit toujours au moment de l'exécution et ne perd pas de données.  Par exemple, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] convertit une valeur `Integer` en `Double`, le cas échéant, car `Integer` s'étend à `Double`.  Pour plus d'informations, consultez [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Les *conversions restrictives* \(celles qui ne sont pas étendues\) courent un risque d'échec au moment de l'exécution, ou de perte de données.  Vous pouvez effectuer explicitement une conversion restrictive en utilisant une fonction de conversion de type, ou encore demander au compilateur d'effectuer implicitement toutes les conversions en définissant `Option Strict Off`.  Pour plus d'informations, consultez [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## Placement de plusieurs instructions sur une seule ligne  
 Plusieurs instructions peuvent figurer sur une seule ligne, séparées par le signe deux\-points \(`:`\).  L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrStatements#70](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_12.vb)]  
  
 Ce type de syntaxe rend souvent la lecture et la gestion du code difficiles.  Il est donc recommandé de conserver une instruction sur une ligne.  
  
## Suite d'une instruction sur plusieurs lignes  
 Une instruction figure généralement dans une seule ligne, mais lorsqu'elle est trop longue, vous pouvez la poursuivre sur la ligne suivante en utilisant une séquence de continuation de ligne, composée respectivement d'un espace, d'un trait de soulignement \(`_`\) et d'un retour chariot.  Dans l'exemple suivant, l'instruction exécutable `MsgBox` se poursuit sur deux lignes.  
  
 [!code-vb[VbVbalrStatements#71](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_13.vb)]  
  
### Continuation de ligne implicite  
 Dans de nombreux cas, vous pouvez continuer une instruction sur la ligne consécutive suivante sans utiliser le trait de soulignement \(\_\).  Le tableau suivant répertorie les éléments de syntaxe qui continuent implicitement l'instruction sur la ligne de code suivante.  
  
|||  
|-|-|  
|Élément de syntaxe|Exemple|  
|Après une virgule \(`,`\).|[!code-vb[VbVbalrLineContinuation#1](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_14.vb)]|  
|Après une parenthèse ouvrante \(`(`\) ou avant une parenthèse fermante \(`)`\).|[!code-vb[VbVbalrLineContinuation#2](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_15.vb)]|  
|Après une accolade ouvrante \(`{`\) ou avant une accolade fermante \(`}`\).|[!code-vb[VbVbalrLineContinuation#3](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_16.vb)]<br /><br /> Pour plus d'informations, consultez [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) ou [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
|Après une expression incorporée ouvrante \(`<%=`\) ou avant une expression incorporée fermante \(`%>`\) dans un littéral XML.|[!code-vb[VbVbalrLineContinuation#4](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_17.vb)]<br /><br /> Pour plus d'informations, consultez [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
|Après l'opérateur de concaténation \(`&`\).|[!code-vb[VbVbcnConventions#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_18.vb)]<br /><br /> Pour plus d'informations, consultez [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Après les opérateurs d'assignation \(`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`\).|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br /><br /> Pour plus d'informations, consultez [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Après les opérateurs binaires \(`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`\) dans une expression.|[!code-vb[VbVbalrLineContinuation#7](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_20.vb)]<br /><br /> Pour plus d'informations, consultez [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Après les opérateurs `Is` et `IsNot`.|[!code-vb[VbVbalrLineContinuation#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_21.vb)]<br /><br /> Pour plus d'informations, consultez [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Après un caractère de qualificateur de membre \(`.`\) et avant le nom de membre.  Toutefois, vous devez inclure un caractère de continuation de ligne \(\_\) après un caractère de qualificateur de membre lorsque vous utilisez l'instruction `With` ou que vous indiquez des valeurs dans la liste d'initialisation d'un type.  Arrêtez la ligne après l'opérateur d'assignation \(par exemple, `=`\) lorsque vous utilisez des instructions `With` ou des listes d'initialisation d'objets.|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br />[!code-vb[VbVbalrLineContinuation#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_22.vb)]<br /><br /> Pour plus d'informations, consultez [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md) ou [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).|  
|Après un qualificateur de propriété d'axe XML \(`.` ou `.@` ou `...`\).  Toutefois, vous devez inclure un caractère de continuation de ligne \(\_\) lorsque vous spécifiez un qualificateur de membre, si vous utilisez le mot clé `With`.|[!code-vb[VbVbalrLineContinuation#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_23.vb)]<br /><br /> Pour plus d'informations, consultez [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).|  
|Après un signe inférieur à \(\<\) ou avant un signe supérieur à \(`>`\) lorsque vous spécifiez un attribut.  Également après un signe supérieur à \(`>`\) lorsque vous spécifiez un attribut.  Toutefois, vous devez inclure un caractère de continuation de ligne \(\_\) lorsque vous spécifiez des attributs au niveau de l'assembly ou du module.|[!code-vb[VbVbalrLineContinuation#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_24.vb)]<br /><br /> Pour plus d'informations, consultez [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md).|  
|Avant et après les opérateurs de requête \(`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending` et `Descending`\).  Vous ne pouvez pas interrompre une ligne entre les mots clés des opérateurs de requête qui sont composés de plusieurs mots clés \(`Order By`, `Group Join`, `Take While` et `Skip While`\).|[!code-vb[VbVbalrLineContinuation#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_25.vb)]<br /><br /> Pour plus d'informations, consultez [Queries](../../../visual-basic/language-reference/queries/queries.md).|  
|Après le mot clé `In` dans une instruction `For Each`.|[!code-vb[VbVbalrLineContinuation#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_26.vb)]<br /><br /> Pour plus d'informations, consultez [For Each...Next, instruction](../../../visual-basic/language-reference/statements/for-each-next-statement.md).|  
|Après le mot clé `From` dans un initialiseur de collection.|[!code-vb[VbVbalrLineContinuation#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_27.vb)]<br /><br /> Pour plus d'informations, consultez [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
  
## Ajout de commentaires  
 Le code source n'est pas toujours explicatif, même pour le programmeur qui l'a écrit.  Pour simplifier la documentation de leur code, la majorité des programmeurs utilisent donc de nombreux commentaires incorporés.  Les commentaires présents dans le code peuvent expliquer une procédure ou une instruction particulière à n'importe quelle personne qui la lit ou l'utilise ultérieurement.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ignore les commentaires pendant la compilation de telle sorte qu'ils n'affectent pas le code compilé.  
  
 Les lignes des commentaires commencent par une apostrophe \(`'`\) ou par `REM` suivi d'un espace.  Ils peuvent être ajoutés n'importe où dans le code, sauf dans une chaîne.  Pour ajouter un commentaire à une instruction, insérez une apostrophe ou `REM` après l'instruction, suivie du commentaire.  Les commentaires peuvent également figurer sur leur propre ligne distincte.  L'exemple de code suivant illustre ces possibilités.  
  
 [!code-vb[VbVbalrStatements#72](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_28.vb)]  
  
## Vérification des erreurs de compilation  
 Si après avoir tapé une ligne de code, la ligne est affichée avec un soulignement ondulant \(un message d'erreur peut également être affiché\), l'instruction comporte une erreur de syntaxe.  Vous devez localiser le problème de l'instruction \(en recherchant dans la liste des tâches ou en plaçant le pointeur de la souris sur l'erreur pour lire le message d'erreur\) et le corriger.  Votre programme ne sera pas correctement compilé si vous ne corrigez pas toutes les erreurs de syntaxe dans votre code.  
  
## Rubriques connexes  
  
|||  
|-|-|  
|Terme|Définition|  
|[Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)|Fournit des liens vers des pages de référence du langage qui décrivent les opérateurs d'assignation, tels que `=`, `*=` et `&=`.|  
|[Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)|Explique comment combiner des éléments avec des opérateurs pour retourner de nouvelles valeurs.|  
|[Procédure : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Indique comment répartir une instruction unique sur plusieurs lignes et comment placer plusieurs instructions sur une même ligne.|  
|[How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Montre comment étiqueter une ligne de code.|