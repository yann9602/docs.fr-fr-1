---
title: Enum, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
caps.latest.revision: "44"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a8244318e0be8e50f3384b56cf63e59182b6cda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="enum-statement-visual-basic"></a>Enum, instruction (Visual Basic)
Déclare une énumération et définit les valeurs de ses membres.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a>Composants  
  
-   `attributelist`  
  
     Facultatif. Liste des attributs qui s’appliquent à cette énumération. Vous devez placer le [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md) figurant entre crochets («`<`« et »`>`»).  
  
     Le <xref:System.FlagsAttribute> attribut indique que la valeur d’une instance de l’énumération peut inclure plusieurs membres de l’énumération, et que chaque membre représente un champ de bits dans la valeur d’énumération.  
  
-   `accessmodifier`  
  
     Facultatif. Spécifie le code pouvant accéder à cette énumération. Il peut s'agir d'une des valeurs suivantes :  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
     Vous pouvez spécifier `Protected``Friend` pour autoriser l’accès à partir du code au sein classe de l’énumération, une classe dérivée ou le même assembly.  
  
-   `Shadows`  
  
     Facultatif. Spécifie que cette énumération redéclare et masque un élément de programmation portant le même nom ou un ensemble d’éléments surchargés, dans une classe de base. Vous pouvez spécifier [ombres](../../../visual-basic/language-reference/modifiers/shadows.md) uniquement sur l’énumération elle-même, et non sur un de ses membres.  
  
-   `enumerationname`  
  
     Obligatoire. Nom de l’énumération. Pour plus d’informations sur les noms valides, consultez [noms d’élément déclaré](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `datatype`  
  
     Facultatif. Type de données de l’énumération et tous ses membres.  
  
-   `memberlist`  
  
     Obligatoire. Liste des constantes membres déclarées dans cette instruction. Plusieurs membres apparaissent sur les lignes de code source individuel.  
  
     Chaque `member` possède la syntaxe et les éléments suivants :`[<attribute list>] member name [ = initializer ]`  
  
    |Élément|Description|  
    |---|---|  
    |`membername`|Obligatoire. Nom de ce membre.|  
    |`initializer`|Facultatif. Expression qui est évaluée au moment de la compilation et assignée à ce membre.|  
  
-   `End` `Enum`  
  
     Met fin au bloc `Enum`.  
  
## <a name="remarks"></a>Remarques  
 Si vous avez un ensemble de valeurs qui ne changent pas logiquement liées entre elles, vous pouvez les définir ensemble dans une énumération. Cela fournit des noms explicites pour l’énumération et ses membres, qui sont plus faciles à mémoriser que leurs valeurs. Vous pouvez ensuite utiliser les membres d’énumération dans de nombreux endroits dans votre code.  
  
 Les avantages de l’utilisation des énumérations sont les suivantes :  
  
-   Réduit les erreurs provoquées par transposer ou numéros d’erreur de frappe.  
  
-   Rend faciles à modifier les valeurs dans le futur.  
  
-   Rend le code plus facile à lire, ce qui signifie qu’il est peu probable que les erreurs seront introduites.  
  
-   Garantit la compatibilité ascendante. Si vous utilisez des énumérations, votre code est moins susceptible d’échouer si à l’avenir une personne modifie les valeurs correspondant aux noms de membre.  
  
 Une énumération a un nom, un type de données sous-jacent et un jeu de membres. Chaque membre représente une constante.  
  
 Une énumération déclarée au niveau de la classe, structure, un module ou niveau de l’interface, en dehors de toute procédure, est une *énumération membre*. Il est membre de la classe, une structure, un module ou une interface qui le déclare.  
  
 Les énumérations de membres sont accessibles à partir de n’importe où au sein de leur classe, une structure, un module ou une interface. Code en dehors d’une classe, structure ou module doit qualifier le nom d’une énumération de membre avec le nom de cette classe, une structure ou un module. Vous pouvez éviter la nécessité d’utiliser des noms qualifiés complets en ajoutant un [importations](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instruction dans le fichier source.  
  
 Une énumération déclarée au niveau de l’espace de noms, en dehors de toute classe, une structure, un module ou une interface, est un membre de l’espace de noms dans lequel elle apparaît.  
  
 Le *contexte de déclaration* pour une énumération doit être un fichier source, espace de noms, classe, structure, module ou interface et qu’il ne peut pas être une procédure. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Vous pouvez appliquer des attributs à une énumération dans son ensemble, mais pas à ses membres individuellement. Un attribut fournit des informations aux métadonnées de l’assembly.  
  
## <a name="data-type"></a>Type de données  
 La `Enum` instruction peut déclarer le type de données d’une énumération. Chaque membre prend le type de données de l’énumération. Vous pouvez spécifier `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, ou `UShort`.  
  
 Si vous ne spécifiez pas `datatype` pour l’énumération, chaque membre prend le type de données de son `initializer`. Si vous spécifiez à la fois `datatype` et `initializer`, type de données de `initializer` doit être convertible en `datatype`. Si ni `datatype` ni `initializer` est présent, le type de données par défaut, `Integer`.  
  
## <a name="initializing-members"></a>L’initialisation des membres  
 Le `Enum` instruction peut initialiser le contenu de membres sélectionnés dans `memberlist`. Vous utilisez `initializer` pour fournir une expression à affecter au membre.  
  
 Si vous ne spécifiez pas `initializer` pour un membre, Visual Basic l’initialise soit à zéro (s’il s’agit de la première `member` dans `memberlist`), ou une valeur supérieure d’une unité à celle de qui précède immédiatement `member`.  
  
 L’expression fournie dans chaque `initializer` peut être n’importe quelle combinaison de littéraux, d’autres constantes qui sont déjà définies et de membres de l’énumération qui sont déjà définis, y compris un membre précédent de cette énumération. Vous pouvez utiliser des opérateurs arithmétiques et logiques pour combiner ces éléments.  
  
 Vous ne pouvez pas utiliser des variables ou des fonctions dans `initializer`. Toutefois, vous pouvez utiliser des mots clés de conversion tels que `CByte` et `CShort`. Vous pouvez également utiliser `AscW` si vous l’appelez avec une constante `String` ou `Char` argument, étant donné que qui peut être évaluée au moment de la compilation.  
  
 Les énumérations ne peut pas avoir de valeurs à virgule flottante. Si un membre est assigné une valeur à virgule flottante et `Option Strict` a la valeur on, une erreur de compilation se produit. Si `Option Strict` est désactivée, la valeur est automatiquement convertie en la `Enum` type.  
  
 Si la valeur d’un membre dépasse la plage autorisée pour le type de données sous-jacente, ou si vous initialisez un membre à la valeur maximale autorisée par le type de données sous-jacent, le compilateur signale une erreur.  
  
## <a name="modifiers"></a>Modificateurs  
 Classe, structure, module et interface membres énumérations par défaut d’un accès public. Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès. Namespace membre énumérations par défaut d’un accès ami. Vous pouvez ajuster leurs niveaux d’accès public, mais pas pour privé ou protégé. Pour plus d’informations, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Tous les membres d’énumération ont un accès public, et vous ne pouvez pas utiliser les modificateurs d’accès sur ces derniers. Toutefois, si l’énumération elle-même a un niveau d’accès plus restreint, le niveau d’accès de l’énumération spécifiée est prioritaire.  
  
 Par défaut, toutes les énumérations sont des types et leurs champs sont des constantes. Par conséquent la `Shared`, `Static`, et `ReadOnly` mots clés ne peut pas être utilisés pour déclarer une énumération ou ses membres.  
  
## <a name="assigning-multiple-values"></a>Affectation de valeurs multiples  
 Énumérations représentent généralement les valeurs s’excluent mutuellement. En incluant la <xref:System.FlagsAttribute> d’attribut dans le `Enum` déclaration, vous pouvez affecter à la place plusieurs valeurs à une instance de l’énumération. Le <xref:System.FlagsAttribute> attribut spécifie que l’énumération être traitée comme un champ de bits, c'est-à-dire un ensemble d’indicateurs. Ils sont appelés *au niveau du bit* énumérations.  
  
 Lorsque vous déclarez une énumération à l’aide de la <xref:System.FlagsAttribute> attribut, nous vous recommandons d’utiliser puissances de 2, qui est, 1, 2, 4, 8, 16 et ainsi de suite, pour les valeurs. Nous vous recommandons également de « None » soit le nom d’un membre dont la valeur est 0. Pour des instructions supplémentaires, consultez <xref:System.FlagsAttribute> et <xref:System.Enum>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la `Enum` instruction. Notez que le membre est appelé `EggSizeEnum.Medium`et non comme `Medium`.  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a>Exemple  
 La méthode dans l’exemple suivant est en dehors de la `Egg` classe. Par conséquent, `EggSizeEnum` est qualifié en tant que `Egg.EggSizeEnum`.  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `Enum` instruction afin de définir un ensemble des valeurs des constantes nommées. Dans ce cas, les valeurs sont des couleurs, que vous pouvez choisir de concevoir les formulaires de saisie de données pour une base de données.  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre les valeurs qui comportent des nombres positifs et négatifs.  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un `As` clause est utilisée pour spécifier le `datatype` d’une énumération.  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser une énumération au niveau du bit. Plusieurs valeurs peuvent être attribués à une instance d’une énumération au niveau du bit. Le `Enum` déclaration inclut le <xref:System.FlagsAttribute> attribut, ce qui indique que l’énumération peut être traitée comme un ensemble d’indicateurs.  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant effectue une itération dans une énumération. Elle utilise le <xref:System.Enum.GetNames%2A> méthode pour récupérer un tableau des noms de membres de l’énumération, et <xref:System.Enum.GetValues%2A> pour récupérer un tableau de valeurs de membre.  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Enum>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [Const (instruction)](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Constantes et énumérations](../../../visual-basic/language-reference/constants-and-enumerations.md)
