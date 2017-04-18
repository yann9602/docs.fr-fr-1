---
title: Enum, instruction (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Enum
dev_langs:
- VB
helpviewer_keywords:
- enumerated constants
- Enum statement
- Private keyword, Enum statements
- Public keyword, in Enum statement
- variables [Visual Basic], enumeration
- constants, enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
caps.latest.revision: 44
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f9d3377300d30fd045c041367a528766fa9a8ed9
ms.lasthandoff: 03/13/2017

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
  
     Facultatif. Liste des attributs qui s’appliquent à cette énumération. Vous devez placer le [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md) dans des crochets pointus («`<`« et »`>`»).  
  
     Le <xref:System.FlagsAttribute>attribut indique que la valeur d’une instance de l’énumération peut inclure plusieurs membres d’énumération, et que chaque membre représente un champ de bits dans la valeur d’énumération.</xref:System.FlagsAttribute>  
  
-   `accessmodifier`  
  
     Facultatif. Spécifie le code pouvant accéder à cette énumération. Il peut s'agir d'une des valeurs suivantes :  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
     Vous pouvez spécifier `Protected``Friend` pour autoriser l’accès à partir de code dans la classe de l’énumération, une classe dérivée ou le même assembly.  
  
-   `Shadows`  
  
     Facultatif. Spécifie que cette énumération redéclare et masque un élément de programmation portant le même nom ou un ensemble d’éléments surchargés, dans une classe de base. Vous pouvez spécifier [ombres](../../../visual-basic/language-reference/modifiers/shadows.md) uniquement sur l’énumération elle-même, et non sur un de ses membres.  
  
-   `enumerationname`  
  
     Obligatoire. Nom de l’énumération. Pour plus d’informations sur les noms valides, consultez la page [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
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
  
## <a name="remarks"></a>Notes  
 Si vous avez un ensemble de valeurs immuables qui sont logiquement liés entre eux, vous pouvez les définir ensemble dans une énumération. Cela fournit des noms explicites pour l’énumération et ses membres, qui sont plus faciles à mémoriser que leurs valeurs. Vous pouvez ensuite utiliser les membres d’énumération dans de nombreux endroits dans votre code.  
  
 Les avantages de l’utilisation d’énumérations sont les suivantes :  
  
-   Réduit les erreurs dues à la transposition ou entrée incorrecte de nombres.  
  
-   Rend plus facile à modifier les valeurs dans le futur.  
  
-   Rend le code plus facile à lire, ce qui signifie qu’il est peu probable que les erreurs seront introduites.  
  
-   Garantit la compatibilité ascendante. Si vous utilisez des énumérations, votre code est moins susceptible d’échouer si l’avenir quelqu'un modifie les valeurs correspondant aux noms de membres.  
  
 Une énumération a un nom, un type de données sous-jacent et un jeu de membres. Chaque membre représente une constante.  
  
 Une énumération déclarée au niveau de la classe, structure, module ou niveau de l’interface, en dehors de toute procédure, est une *énumération membre*. Il est membre de la classe, une structure, un module ou une interface qui la déclare.  
  
 Les énumérations de membres sont accessibles à partir de n’importe où au sein de leur classe, une structure, un module ou une interface. Code à l’extérieur d’une classe, structure ou module doit qualifier le nom d’une énumération de membre avec le nom de cette classe, une structure ou un module. Vous pouvez éviter la nécessité d’utiliser des noms qualifiés complets en ajoutant une [importations](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instruction dans le fichier source.  
  
 Une énumération déclarée au niveau de l’espace de noms, en dehors de toute classe, une structure, un module ou une interface, est un membre de l’espace de noms dans lequel il apparaît.  
  
 Le *contexte de déclaration* pour une énumération doit être un fichier source, espace de noms, classe, structure, module ou interface et ne peut pas être une procédure. Pour plus d’informations, consultez [contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Vous pouvez appliquer des attributs à une énumération dans son ensemble, mais pas à ses membres individuellement. Un attribut fournit des informations aux métadonnées de l’assembly.  
  
## <a name="data-type"></a>Type de données  
 La `Enum` instruction peut déclarer le type de données d’une énumération. Chaque membre prend le type de données de l’énumération. You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.  
  
 Si vous ne spécifiez pas `datatype` pour l’énumération, chaque membre prend le type de données de ses `initializer`. Si vous spécifiez les deux `datatype` et `initializer`, type de données de `initializer` doit être convertible en `datatype`. Si ni `datatype` ni `initializer` est présent, le type de données par défaut, `Integer`.  
  
## <a name="initializing-members"></a>Initialisation des membres  
 Le `Enum` instruction peut initialiser le contenu de membres sélectionnés dans `memberlist`. Vous utilisez `initializer` pour fournir une expression à assigner au membre.  
  
 Si vous ne spécifiez pas `initializer` d’un membre, Visual Basic l’initialise soit à zéro (s’il s’agit de la première `member` dans `memberlist`), ou une valeur supérieure d’une unité à celle de la précédant `member`.  
  
 L’expression fournie dans chaque `initializer` peut être n’importe quelle combinaison de littéraux, d’autres constantes qui sont déjà définies et de membres de l’énumération qui sont déjà définies, y compris un membre précédent de cette énumération. Vous pouvez utiliser des opérateurs arithmétiques et logiques pour combiner ces éléments.  
  
 Vous ne pouvez pas utiliser de variables ni fonctions dans `initializer`. Toutefois, vous pouvez utiliser des mots clés de conversion tels que `CByte` et `CShort`. Vous pouvez également utiliser `AscW` si vous l’appelez avec une constante `String` ou `Char` argument, étant donné que qui peut être évaluée au moment de la compilation.  
  
 Les énumérations ne peut pas avoir de valeurs à virgule flottante. Si un membre est attribué une valeur à virgule flottante et `Option Strict` a la valeur on, une erreur de compilation se produit. Si `Option Strict` est désactivé, la valeur est automatiquement convertie en la `Enum` type.  
  
 Si la valeur d’un membre dépasse la plage autorisée pour le type de données sous-jacent, ou si vous initialisez un membre à la valeur maximale autorisée par le type de données sous-jacent, le compilateur signale une erreur.  
  
## <a name="modifiers"></a>Modificateurs  
 Classe, structure, module et interface membres énumérations par défaut d’un accès public. Vous pouvez régler leurs niveaux d’accès avec les modificateurs d’accès. Namespace membre énumérations par défaut d’un accès ami. Vous pouvez régler leurs niveaux d’accès public, mais pas en privé ou protégé. Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Tous les membres d’énumération ont un accès public, et vous ne pouvez pas utiliser les modificateurs d’accès sur ces derniers. Toutefois, si l’énumération proprement dite possède un niveau d’accès plus restreint, le niveau d’accès spécifié (énumération) est prioritaire.  
  
 Par défaut, toutes les énumérations sont des types et leurs champs sont des constantes. Par conséquent, le `Shared`, `Static`, et `ReadOnly` mots clés ne peuvent pas être utilisés lors de la déclaration d’une énumération ou ses membres.  
  
## <a name="assigning-multiple-values"></a>Attribution de plusieurs valeurs  
 Énumérations représentent généralement les valeurs qui s’excluent mutuellement. En incluant la <xref:System.FlagsAttribute>l’attribut dans le `Enum` déclaration, vous pouvez à la place attribuer plusieurs valeurs à une instance de l’énumération.</xref:System.FlagsAttribute> Le <xref:System.FlagsAttribute>attribut spécifie que l’énumération considérée comme un champ de bits, c'est-à-dire un ensemble d’indicateurs.</xref:System.FlagsAttribute> Il s’agit de *au niveau du bit* énumérations.  
  
 Lorsque vous déclarez une énumération à l’aide de la <xref:System.FlagsAttribute>attribut, nous vous recommandons d’utiliser les puissances de 2, qui est, 1, 2, 4, 8, 16 et ainsi de suite, pour les valeurs.</xref:System.FlagsAttribute> Nous vous recommandons également de « None » soit le nom d’un membre dont la valeur est 0. Pour obtenir des instructions supplémentaires, consultez la page <xref:System.FlagsAttribute>et <xref:System.Enum>.</xref:System.Enum> </xref:System.FlagsAttribute>  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la `Enum` instruction. Notez que le membre est appelé `EggSizeEnum.Medium`et non comme `Medium`.  
  
 [!code-vb[# VbEnumsTask&41;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a>Exemple  
 La méthode dans l’exemple suivant est en dehors de la `Egg` classe. Par conséquent, `EggSizeEnum` est le nom complet en tant que `Egg.EggSizeEnum`.  
  
 [!code-vb[VbEnumsTask&#42;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `Enum` instruction pour définir un ensemble des valeurs des constantes nommées. Dans ce cas, les valeurs sont des couleurs que vous pouvez choisir de concevoir des formulaires de saisie de données pour une base de données.  
  
 [!code-vb[30 VbEnumsTask](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre les valeurs qui incluent des nombres positifs et négatifs.  
  
 [!code-vb[VbEnumsTask&#31;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un `As` clause est utilisée pour spécifier le `datatype` d’une énumération.  
  
 [!code-vb[VbEnumsTask n °&6;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser une énumération au niveau du bit. Plusieurs valeurs peuvent être assignées à une instance d’une énumération au niveau du bit. Le `Enum` déclaration comprend le <xref:System.FlagsAttribute>attribut qui indique que l’énumération peut être traitée comme un ensemble d’indicateurs.</xref:System.FlagsAttribute>  
  
 [!code-vb[VbEnumsTask&#61;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant itère une énumération. Il utilise le <xref:System.Enum.GetNames%2A>méthode pour récupérer un tableau des noms de membres de l’énumération, et <xref:System.Enum.GetValues%2A>pour récupérer un tableau de valeurs de membre.</xref:System.Enum.GetValues%2A> </xref:System.Enum.GetNames%2A>  
  
 [!code-vb[VbEnumsTask&#51;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Enum></xref:System.Enum>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 [Const (instruction)](../../../visual-basic/language-reference/statements/const-statement.md)   
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Fonctions de Conversion de type](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Constantes et énumérations](../../../visual-basic/language-reference/constants-and-enumerations.md)
