---
title: Const, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Const
helpviewer_keywords: Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 720a465f1459b663a1fca2a48856f51762328459
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="const-statement-visual-basic"></a>Const, instruction (Visual Basic)
Déclare et définit une ou plusieurs constantes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## <a name="parts"></a>Composants  
 `attributelist`  
 Facultatif. Liste des attributs qui s’appliquent à toutes les constantes déclarées dans cette instruction. Consultez [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md) figurant entre crochets («`<`« et »`>`»).  
  
 `accessmodifier`  
 Facultatif. Permet de spécifier le code peut accéder à ces constantes. Peut être [Public](../../../visual-basic/language-reference/modifiers/public.md), [protégé](../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, ou [privé](../../../visual-basic/language-reference/modifiers/private.md).  
  
 `Shadows`  
 Facultatif. Utilisez-le pour redéclarer et masquer un élément de programmation dans une classe de base. Consultez [ombres](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `constantlist`  
 Obligatoire. Liste des constantes qui sont déclarées dans cette instruction.  
  
 `constant` `[ ,` `constant` `... ]`  
  
 Chaque `constant` emploie la syntaxe et les éléments suivants :  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|Élément|Description|  
|----------|-----------------|  
|`constantname`|Obligatoire. Nom de la constante. Consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`datatype`|Obligatoire si `Option Strict` est `On`. Type de données de la constante.|  
|`initializer`|Obligatoire. Expression qui est évaluée au moment de la compilation et assignée à la constante.|  
  
## <a name="remarks"></a>Remarques  
 Si vous avez une valeur qui ne change jamais dans votre application, vous pouvez définir une constante nommée et l’utiliser à la place d’une valeur littérale. Un nom est plus facile à mémoriser à une valeur. Vous pouvez définir la constante une seule fois et l’utiliser dans de nombreux endroits dans votre code. Si dans une version ultérieure, vous devez redéfinir la valeur, la `Const` instruction est le seul endroit où vous souhaitez apporter une modification.  
  
 Vous pouvez utiliser `Const` uniquement au niveau du module ou de la procédure. Cela signifie que la *contexte de déclaration* pour une variable doit être une classe, structure, module, procédure ou un bloc et qu’il ne peut pas être un fichier source, un espace de noms ou une interface. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Par défaut les constantes locales (à l’intérieur d’une procédure) à l’accès public et que vous ne pouvez pas utiliser des modificateurs d’accès sur ces derniers. Classe et le module membre constantes (en dehors de toute procédure) par défaut d’un accès privé et structure membre constantes par défaut d’un accès public. Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès.  
  
## <a name="rules"></a>Règles  
  
-   **Contexte de déclaration.** Une constante déclarée au niveau du module, en dehors de toute procédure, est une *constante membre*; il est membre de la classe, structure, ou le module qui la déclare.  
  
     Une constante déclarée au niveau de la procédure est un *constante locale*; elle est locale à la procédure ou du bloc qui le déclare.  
  
-   **Attributs.** Vous pouvez appliquer des attributs qu’aux constantes membres, pas aux constantes locales. Un attribut fournit des informations aux métadonnées de l’assembly, qui n’est pas significatif pour le stockage temporaire, tels que les constantes locales.  
  
-   **Modificateurs.** Par défaut, toutes les constantes sont `Shared`, `Static`, et `ReadOnly`. Vous ne pouvez pas utiliser un de ces mots clés lors de la déclaration d’une constante.  
  
     Au niveau de la procédure, vous ne pouvez pas utiliser `Shadows` ou un modificateur d’accès pour déclarer des constantes locales.  
  
-   **Plusieurs constantes.** Vous pouvez déclarer plusieurs constantes dans la même instruction de déclaration, en spécifiant le `constantname` partie pour chacun d’eux. Constantes multiples sont séparées par des virgules.  
  
## <a name="data-type-rules"></a>Règles de Type de données  
  
-   **Types de données.** La `Const` instruction peut déclarer le type de données d’une variable. Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération.  
  
-   **Type de valeur par défaut.** Si vous ne spécifiez pas `datatype`, la constante prend le type de données `initializer`. Si vous spécifiez à la fois `datatype` et `initializer`, type de données de `initializer` doit être convertible en `datatype`. Si ni `datatype` ni `initializer` est présent, le type de données par défaut, `Object`.  
  
-   **Différents Types.** Vous pouvez spécifier différents types de données pour les constantes à l’aide de distinct `As` clause pour chaque variable que vous déclarez. Toutefois, vous ne pouvez pas déclarer plusieurs constantes comme étant du même type à l’aide d’un commun `As` clause.  
  
-   **Initialisation.** Vous devez initialiser la valeur de chaque constante dans `constantlist`. Vous utilisez `initializer` pour fournir une expression à assigner à la constante. L’expression peut être n’importe quelle combinaison de littéraux, d’autres constantes qui sont déjà définies et de membres de l’énumération qui sont déjà définis. Vous pouvez utiliser des opérateurs arithmétiques et logiques pour combiner ces éléments.  
  
     Vous ne pouvez pas utiliser des variables ou des fonctions dans `initializer`. Toutefois, vous pouvez utiliser des mots clés de conversion tels que `CByte` et `CShort`. Vous pouvez également utiliser `AscW` si vous l’appelez avec une constante `String` ou `Char` argument, étant donné que qui peut être évaluée au moment de la compilation.  
  
## <a name="behavior"></a>Comportement  
  
-   **Étendue.** Les constantes locales sont accessibles uniquement à partir de leur procédure ou un bloc. Constantes de membres sont accessibles à partir de n’importe où leur classe, structure ou un module.  
  
-   **Qualification.** Code en dehors d’une classe, structure ou module doit qualifier le nom d’une constante membre avec le nom de cette classe, une structure ou un module. Code en dehors de qu'une procédure ou un bloc ne peut pas faire référence aux constantes locales de cette procédure ou un bloc.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `Const` instruction pour déclarer des constantes à utiliser à la place de valeurs littérales.  
  
 [!code-vb[VbVbalrStatements#13](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_1.vb)]  
  
## <a name="example"></a>Exemple  
 Si vous définissez une constante avec le type de données `Object`, le compilateur Visual Basic lui donne le type de `initializer`, au lieu de `Object`. Dans l’exemple suivant, la constante `naturalLogBase` a le type au moment de l’exécution `Decimal`.  
  
 [!code-vb[VbVbalrStatements#87](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_2.vb)]  
  
 L’exemple précédent utilise la <xref:System.Type.ToString%2A> méthode sur le <xref:System.Type> objet retourné par la [opérateur GetType](../../../visual-basic/language-reference/operators/gettype-operator.md), car <xref:System.Type> ne peut pas être converti en `String` à l’aide de `CStr`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [Enum (instruction)](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [#Const (directive)](../../../visual-basic/language-reference/directives/const-directive.md)  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim (instruction)](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Constantes et énumérations](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [Constantes et énumérations](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
