---
title: Dim, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
caps.latest.revision: "72"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a428f8be7b62600ca8fffd3160039c1de911e34e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="dim-statement-visual-basic"></a>Dim, instruction (Visual Basic)
Déclare et alloue de l’espace de stockage pour une ou plusieurs variables.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a>Composants  
  
-   `attributelist`  
  
     Facultatif. Consultez [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
-   `accessmodifier`  
  
     Facultatif. Il peut s'agir d'une des valeurs suivantes :  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     Consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `Shared`  
  
     Facultatif. Consultez [partagé](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Facultatif. Consultez [ombres](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `Static`  
  
     Facultatif. Consultez [statique](../../../visual-basic/language-reference/modifiers/static.md).  
  
-   `ReadOnly`  
  
     Facultatif. Consultez [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
-   `WithEvents`  
  
     Facultatif. Spécifie qu’il s’agit des variables objets qui font référence aux instances d’une classe qui peut déclencher des événements. Consultez [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).  
  
-   `variablelist`  
  
     Obligatoire. Liste des variables déclarées dans cette instruction.  
  
     `variable [ , variable ... ]`  
  
     Chaque `variable` emploie la syntaxe et les éléments suivants :  
  
     `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`  
  
    |Élément|Description|  
    |---|---|  
    |`variablename`|Obligatoire. Nom de la variable. Consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
    |`boundslist`|Facultatif. Liste des limites de chaque dimension d’une variable tableau.|  
    |`New`|Facultatif. Crée une nouvelle instance de la classe lors de la `Dim` instruction s’exécute.|  
    |`datatype`|Facultatif. Type de données de la variable.|  
    |`With`|Facultatif. Présente la liste d’initialiseurs objet.|  
    |`propertyname`|Facultatif. Le nom d’une propriété dans la classe, vous effectuez une instance de.|  
    |`propinitializer`|Requis après `propertyname` =. L’expression qui est évaluée et assignée au nom de propriété.|  
    |`initializer`|Facultatif si `New` n’est pas spécifié. Expression qui est évaluée et assignée à la variable lors de sa création.|  
  
## <a name="remarks"></a>Remarques  
 Le compilateur Visual Basic utilise le `Dim` pour déterminer le type de données de la variable et d’autres informations, telles que le code peut accéder à la variable. L’exemple suivant déclare une variable qui doit contenir un `Integer` valeur.  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, structure, classe ou d’interface.  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 Pour un type référence, vous utilisez le `New` mot clé pour créer une nouvelle instance de la classe ou une structure qui est spécifié par le type de données. Si vous utilisez `New`, vous n’utilisez pas une expression d’initialiseur. Au lieu de cela, vous fournissez des arguments, s’ils sont requis, au constructeur de la classe à partir de laquelle vous créez la variable.  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 Vous pouvez déclarer une variable dans une procédure, un bloc, une classe, une structure ou un module. Vous ne pouvez pas déclarer une variable dans un fichier source, un espace de noms ou une interface. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Une variable qui est déclarée au niveau du module, en dehors de toute procédure, est une *variable membre* ou *champ*. Les variables membres sont dans la portée dans l’ensemble de leur classe, structure ou un module. Une variable déclarée au niveau de la procédure est un *variable locale*. Variables locales sont dans la portée uniquement au sein de leur procédure ou un bloc.  
  
 Les modificateurs d’accès suivants sont utilisés pour déclarer des variables en dehors d’une procédure : `Public`, `Protected`, `Friend`, `Protected Friend`, et `Private`. Pour plus d’informations, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Le `Dim` mot clé est facultatif et généralement omis si vous spécifiez un des modificateurs suivants : `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, ou `WithEvents`.  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 Si `Option Explicit` est activée (par défaut), le compilateur requiert une déclaration pour chaque variable que vous utilisez. Pour plus d’informations, consultez [Option Explicit, instruction](../../../visual-basic/language-reference/statements/option-explicit-statement.md).  
  
## <a name="specifying-an-initial-value"></a>Spécifier une valeur initiale  
 Vous pouvez affecter une valeur à une variable lors de sa création. Pour un type valeur, vous utilisez un *initialiseur* pour fournir une expression à affecter à la variable. L’expression doit correspondre à une constante qui peut être calculée au moment de la compilation.  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 Si un initialiseur est spécifié et un type de données n’est pas spécifié dans un `As` clause, *l’inférence de type* est utilisée pour déduire le type de données à partir de l’initialiseur. Dans l’exemple suivant, les deux `num1` et `num2` sont fortement typées en tant qu’entiers. Dans la seconde déclaration, l’inférence de type déduit le type de la valeur 3.  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 L’inférence de type s’applique au niveau de la procédure. Il ne s’applique pas à l’extérieur d’une procédure dans une classe, une structure, un module ou une interface. Pour plus d’informations sur l’inférence de type, consultez [Option Infer, instruction](../../../visual-basic/language-reference/statements/option-infer-statement.md) et [l’inférence de Type Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 Pour plus d’informations sur ce qui se passe quand un type de données ou un initialiseur n’est pas spécifié, consultez [par défaut des Types de données et les valeurs](../../../visual-basic/language-reference/statements/dim-statement.md#default) plus loin dans cette rubrique.  
  
 Vous pouvez utiliser un *initialiseur d’objet* pour déclarer des instances de types nommés et anonymes. Le code suivant crée une instance d’un `Student` de classe et utilise un initialiseur d’objet pour initialiser les propriétés.  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 Pour plus d’informations sur les initialiseurs d’objets, consultez [Comment : déclarer un objet à l’aide d’un initialiseur d’objet](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [initialiseurs d’objets : Types nommés et anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), et [les Types anonymes ](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="declaring-multiple-variables"></a>Déclaration de Variables multiples  
 Vous pouvez déclarer plusieurs variables dans la même instruction de déclaration, en spécifiant le nom de variable pour chacun d’eux et en suivant le nom de chaque tableau avec des parenthèses. Les variables multiples sont séparées par des virgules.  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 Si vous déclarez plusieurs variables avec une `As` clause, vous ne pouvez pas fournir un initialiseur pour ce groupe de variables.  
  
 Vous pouvez spécifier différents types de données pour différentes variables à l’aide de distinct `As` clause pour chaque variable que vous déclarez. Chaque variable prend le type de données spécifié dans la première `As` clause rencontrée après son `variablename` partie.  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a>Tableaux  
 Vous pouvez déclarer une variable qui doit contenir un *tableau*, qui peut contenir plusieurs valeurs. Pour spécifier qu’une variable contient un tableau, procédez comme son `variablename` immédiatement avec des parenthèses. Pour plus d’informations sur les tableaux, consultez [tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Vous pouvez spécifier la limite inférieure et supérieure de chaque dimension du tableau. Pour cela, incluez un `boundslist` à l’intérieur des parenthèses. Pour chaque dimension, le `boundslist` spécifie la limite supérieure et éventuellement la limite inférieure. La limite inférieure est toujours égal à zéro, si vous le spécifiez ou non. Chaque index peut varier de zéro à sa valeur de limite supérieure.  
  
 Les deux instructions suivantes sont équivalentes. Chaque instruction déclare un tableau de 21 `Integer` éléments. Lorsque vous accédez au tableau, l’index peut varier entre 0 et 20.  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 L’instruction suivante déclare un tableau à deux dimensions de type `Double`. Le tableau a 4 lignes (3 + 1) de 6 colonnes (5 + 1). Notez qu’une limite supérieure représente la valeur la plus élevée possible pour l’index, et non la longueur de la dimension. La longueur de la dimension est la limite supérieure plus un.  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 Un tableau peut avoir de 1 à 32 dimensions.  
  
 Vous pouvez laisser toutes les limites vides dans une déclaration de tableau. Si vous faites cela, le tableau dispose du nombre de dimensions que vous spécifiez, mais il n’est pas initialisé. Il a la valeur `Nothing` jusqu'à ce que vous initialisez au moins certains de ses éléments. La `Dim` instruction doit spécifier des limites pour toutes les dimensions ou aucune dimension.  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 Si le tableau a plusieurs dimensions, vous devez inclure des virgules entre parenthèses pour indiquer le nombre de dimensions.  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 Vous pouvez déclarer un *tableau de longueur zéro* en déclarant une des dimensions du tableau-1. Une variable qui contient un tableau de longueur zéro n’a pas la valeur `Nothing`. Les tableaux de longueur nulle sont requis par certaines fonctions du common language runtime. Si vous essayez d’accéder à ce type de tableau, une exception runtime se produit. Pour plus d’informations, consultez [tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Vous pouvez initialiser les valeurs d’un tableau à l’aide d’un littéral de tableau. Pour ce faire, mettez les valeurs d’initialisation entre accolades (`{}`).  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 Pour les tableaux multidimensionnels, l’initialisation de chaque dimension séparée est entourée d’accolades dans la dimension externe. Les éléments sont spécifiés dans l’ordre ligne-champ.  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 Pour plus d’informations sur les littéraux de tableau, consultez [tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
##  <a name="default"></a>Types de données par défaut et valeurs  
 Le tableau suivant décrit les résultats des diverses combinaisons de spécification du type de données et d'un initialiseur dans une instruction `Dim`.  
  
|Type de données spécifié ?|Initialiseur spécifié ?|Exemple|Résultat|  
|---|---|---|---|  
|Non|Non|`Dim qty`|Si [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) est désactivé (par défaut), la variable est définie sur `Nothing`.<br /><br /> Si `Option Strict` est activé, une erreur se produit au moment de la compilation.|  
|Non|Oui|`Dim qty = 5`|Si [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) est activée (par défaut), la variable prend les données de type de l’initialiseur. Consultez [l’inférence de Type Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est désactivé, la variable prend le type de données de `Object`.<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est activé, une erreur se produit au moment de la compilation.|  
|Oui|Non|`Dim qty As Integer`|La variable est initialisée avec la valeur par défaut du type de données. Consultez le tableau plus loin dans cette section.|  
|Oui|Oui|`Dim qty  As Integer = 5`|Si le type de données de l’initialiseur ne peut pas être converti dans le type de données spécifié, une erreur se produit au moment de la compilation.|  
  
 Si vous spécifiez un type de données mais que vous ne spécifiez pas un initialiseur, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] initialise la variable à la valeur par défaut pour son type de données. Le tableau suivant présente la valeur par défaut des valeurs d’initialisation.  
  
|Type de données|Valeur par défaut|  
|---|---|  
|Tous les types numériques (y compris `Byte` et `SByte`)|0|  
|`Char`|0 (binaire)|  
|Tous les types référence (y compris `Object`, `String`et tous les tableaux)|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|12 h 00 le 1er janvier de l’année 1 (01/01/0001 12:00:00 AM)|  
  
 Chaque élément d’une structure est initialisé comme s’il s’agissait d’une variable distincte. Si vous déclarez la longueur d’un tableau, mais ne pas initialisez ses éléments, chaque élément est initialisé comme s’il s’agissait d’une variable distincte.  
  
## <a name="static-local-variable-lifetime"></a>Durée de vie Variable locale statique  
 A `Static` variable locale a une durée de vie plus longue que celle de la procédure dans laquelle elle est déclarée. Les limites de durée de vie de la variable dépendent où la procédure est déclarée et qu’il soit `Shared`.  
  
|Déclaration de procédure|Variable initialisée|Variable n’existe plus.|  
|---|---|---|  
|Dans un module|La première fois que la procédure est appelée.|Lorsque votre programme s’arrête l’exécution|  
|Dans une classe ou une structure, la procédure est`Shared`|La première fois que la procédure est appelée sur une instance spécifique ou sur la classe ou la structure elle-même|Lorsque votre programme s’arrête l’exécution|  
|Dans une classe ou une structure, la procédure n’est pas`Shared`|La première fois que la procédure est appelée sur une instance spécifique|Lorsque l’instance est libérée pour le garbage collection (GC)|  
  
## <a name="attributes-and-modifiers"></a>Attributs et les modificateurs  
 Vous pouvez appliquer des attributs qu’aux variables membres, pas aux variables locales. Un attribut fournit des informations aux métadonnées de l’assembly, qui n’est pas significatif pour le stockage temporaire, tels que des variables locales.  
  
 Au niveau du module, vous ne pouvez pas utiliser le `Static` modificateur pour déclarer des variables de membre. Au niveau de la procédure, vous ne pouvez pas utiliser `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, ou un modificateur d’accès pour déclarer des variables locales.  
  
 Vous pouvez spécifier le code peut accéder à une variable en fournissant un `accessmodifier`. Classe et le module membre variables (en dehors de toute procédure) par défaut d’un accès privé et structure membre variables par défaut d’un accès public. Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès. Vous ne pouvez pas utiliser les modificateurs d’accès sur les variables locales (à l’intérieur d’une procédure).  
  
 Vous pouvez spécifier `WithEvents` uniquement sur les variables membres, et non sur les variables locales à l’intérieur d’une procédure. Si vous spécifiez `WithEvents`, le type de données de la variable doit être un type class spécifique, pas `Object`. Vous ne pouvez pas déclarer un tableau avec `WithEvents`. Pour plus d’informations sur les événements, consultez [événements](../../../visual-basic/programming-guide/language-features/events/index.md).  
  
> [!NOTE]
>  Code en dehors d’une classe, structure ou module doit qualifier le nom d’une variable membre avec le nom de cette classe, une structure ou un module. Code en dehors de qu'une procédure ou un bloc ne peut pas faire référence à des variables locales de cette procédure ou un bloc.  
  
## <a name="releasing-managed-resources"></a>Libération des ressources managées  
 Le garbage collector .NET Framework libère des ressources managées sans codage supplémentaire de votre part. Toutefois, vous pouvez forcer la suppression d’une ressource managée au lieu d’attendre le garbage collector.  
  
 Si une classe maintient une ressource particulièrement précieuse et rare (par exemple, un handle de connexion ou un fichier de base de données), vous pouvez attendre jusqu’au garbage collection suivant pour nettoyer une instance de classe qui n’est plus en cours d’utilisation. Une classe peut implémenter la <xref:System.IDisposable> interface afin de fournir un moyen pour libérer des ressources avant un garbage collection. Une classe qui implémente cette interface expose un `Dispose` méthode qui peut être appelé pour le forcer à libérer immédiatement des ressources précieuses.  
  
 La `Using` instruction automatise le processus de l’acquisition d’une ressource, l’exécution d’un ensemble d’instructions, puis suppression de la ressource. Toutefois, la ressource doit implémenter la <xref:System.IDisposable> interface. Pour plus d’informations, consultez [using, instruction](../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant déclare les variables à l’aide de la `Dim` instruction avec différentes options.  
  
 [!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant répertorie les nombres premiers entre 1 et 30. La portée des variables locales est décrite dans les commentaires de code.  
  
 [!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la `speedValue` variable est déclarée au niveau de la classe. Le `Private` est utilisé pour déclarer la variable. La variable est accessible par n’importe quelle procédure la `Car` classe.  
  
 [!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Const (instruction)](../../../visual-basic/language-reference/statements/const-statement.md)  
 [ReDim (instruction)](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Option Explicit (instruction)](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Option Infer (instruction)](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Page Compiler, Concepteur de projet (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [Déclaration de variable](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Initialiseurs d’objets : types nommés et anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Initialiseurs d’objets : types nommés et anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Guide pratique : déclarer un objet à l’aide d’un initialiseur d’objet](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)  
 [Inférence de type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
