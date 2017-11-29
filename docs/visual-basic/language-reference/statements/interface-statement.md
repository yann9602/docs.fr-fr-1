---
title: Interface, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9418dc86ac6947ae951cb8fb757aed6e092a6668
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="interface-statement-visual-basic"></a>Interface, instruction (Visual Basic)
Déclare le nom d’une interface et introduit les définitions des membres qui se compose de l’interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] _  
Interface name [ ( Of typelist ) ]  
    [ Inherits interfacenames ]  
    [ [ modifiers ] Property membername ]  
    [ [ modifiers ] Function membername ]  
    [ [ modifiers ] Sub membername ]  
    [ [ modifiers ] Event membername ]  
    [ [ modifiers ] Interface membername ]  
    [ [ modifiers ] Class membername ]  
    [ [ modifiers ] Structure membername ]  
End Interface  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`attributelist`|Facultatif. Consultez [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Facultatif. Il peut s'agir d'une des valeurs suivantes :<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privé](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Facultatif. Consultez [ombres](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`name`|Obligatoire. Nom de cette interface. Consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Facultatif. Spécifie qu’il s’agit d’une interface générique.|  
|`typelist`|Requis si vous utilisez la [de](../../../visual-basic/language-reference/statements/of-clause.md) (mot clé). Liste des paramètres de type pour cette interface. Éventuellement, chaque paramètre de type peut être déclaré variant à l’aide de `In` et `Out` modificateurs génériques. Consultez [tapez liste](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Facultatif. Indique que cette interface hérite les attributs et les membres d’une autre interface ou les interfaces. Consultez [Inherits, instruction](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`interfacenames`|Requis si vous utilisez la `Inherits` instruction. Les noms des interfaces à partir duquel cette interface dérive.|  
|`modifiers`|Facultatif. Modificateurs appropriés pour le membre d’interface défini.|  
|`Property`|Facultatif. Définit une propriété qui est un membre de l’interface.|  
|`Function`|Facultatif. Définit un `Function` procédure qui est un membre de l’interface.|  
|`Sub`|Facultatif. Définit un `Sub` procédure qui est un membre de l’interface.|  
|`Event`|Facultatif. Définit un événement qui est un membre de l’interface.|  
|`Interface`|Facultatif. Définit une interface qui est imbriquée dans cette interface. La définition d’interface imbriquée doit se terminer par un `End Interface` instruction.|  
|`Class`|Facultatif. Définit une classe qui est un membre de l’interface. La définition de la classe membre doit se terminer par un `End Class` instruction.|  
|`Structure`|Facultatif. Définit une structure qui est un membre de l’interface. La définition de la structure membre doit se terminer par un `End Structure` instruction.|  
|`membername`|Obligatoire pour chaque propriété, procédure, événement, interface, classe ou structure définie en tant que membre de l’interface. Nom du membre.|  
|`End Interface`|Met fin à la `Interface` définition.|  
  
## <a name="remarks"></a>Remarques  
 Un *interface* définit un jeu de membres, tels que les propriétés et les procédures que les classes et les structures peuvent implémenter. L’interface définit uniquement les signatures des membres et pas leur fonctionnement interne.  
  
 Une classe ou structure implémente l’interface en fournissant un code pour chaque membre défini par l’interface. Enfin, lorsque l’application crée une instance de cette classe ou structure, un objet existe et s’exécute en mémoire. Pour plus d’informations, consultez [objets et Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) et [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Vous pouvez utiliser `Interface` uniquement au niveau de l’espace de noms ou module. Cela signifie que la *contexte de déclaration* pour une interface doit être un fichier source, espace de noms, classe, structure, module ou interface et ne peut pas être une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 La valeur par défaut pour les interfaces [Friend](../../../visual-basic/language-reference/modifiers/friend.md) accès. Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès. Pour plus d’informations, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Règles  
  
-   **Imbrication des Interfaces.** Vous pouvez définir une interface dans une autre. L’interface externe est appelée la *contenant l’interface*, et l’interface interne est appelée un *interface imbriquée*.  
  
-   **Déclaration de membre.** Lorsque vous déclarez une propriété ou une procédure en tant que membre d’une interface, vous définissez uniquement la *signature* de cette propriété ou procédure. Cela inclut le type d’élément (propriété ou procédure), ses paramètres et types de paramètre et son type de retour. Pour cette raison, la définition de membre utilise une seule ligne de code et de fin d’instructions telles que `End Function` ou `End Property` ne sont pas valides dans une interface.  
  
     En revanche, lorsque vous définissez une énumération ou de structure, ou une classe imbriquée ou une interface, il est nécessaire d’inclure leurs membres de données.  
  
-   **Modificateurs de membre.** Vous ne pouvez pas utiliser les modificateurs d’accès lors de la définition des membres de module, ni spécifier [Shared](../../../visual-basic/language-reference/modifiers/shared.md) ou un modificateur de procédure sauf [surcharges](../../../visual-basic/language-reference/modifiers/overloads.md). Vous pouvez déclarer un membre avec [ombres](../../../visual-basic/language-reference/modifiers/shadows.md), et vous pouvez utiliser [par défaut](../../../visual-basic/language-reference/modifiers/default.md) lors de la définition d’une propriété, ainsi que [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) ou [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
-   **Héritage.** Si l’interface utilise les [l’instruction Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md), vous pouvez spécifier une ou plusieurs interfaces de base. Vous pouvez hériter de deux interfaces même si chacune définit un membre portant le même nom. Si vous procédez ainsi, le code d’implémentation doit utiliser qualification de noms pour spécifier le membre qu’il implémente.  
  
     Une interface ne peut pas hériter d’une autre interface avec un niveau d’accès plus restrictif. Par exemple, un `Public` interface ne peut pas hériter d’un `Friend` interface.  
  
     Une interface ne peut pas hériter d’une interface imbriquée dans celui-ci.  
  
-   **Mise en œuvre.** Lorsqu’une classe utilise le [implémente](../../../visual-basic/language-reference/statements/implements-clause.md) instruction pour implémenter cette interface, elle doit implémenter chaque membre défini dans l’interface. En outre, chaque signature dans le code d’implémentation doit correspondre exactement à la signature correspondante définie dans cette interface. Toutefois, le nom du membre dans le code d’implémentation n’a pas correspondre au nom de membre, tel que défini dans l’interface.  
  
     Lorsqu’une classe implémente une procédure, il ne peut pas désigner la procédure en tant que `Shared`.  
  
-   **Propriété par défaut.** Une interface peut spécifier au plus une propriété en tant que son *propriété par défaut*, ce qui peut être référencé sans utiliser le nom de propriété. Vous spécifiez cette propriété en la déclarant avec le [par défaut](../../../visual-basic/language-reference/modifiers/default.md) modificateur.  
  
     Notez que cela signifie qu’une interface peut définir une propriété par défaut uniquement si elle hérite d’aucune.  
  
## <a name="behavior"></a>Comportement  
  
-   **Niveau d’accès.** Tous les membres d’interface possèdent implicitement [Public](../../../visual-basic/language-reference/modifiers/public.md) accès. Vous ne pouvez pas utiliser un modificateur d’accès lors de la définition d’un membre. Toutefois, une classe qui implémente l’interface peut déclarer un niveau d’accès pour chaque membre implémenté.  
  
     Si vous assignez une instance de classe à une variable, le niveau d’accès de ses membres peut varient selon que le type de données de la variable est l’interface sous-jacente ou la classe d’implémentation. L'exemple suivant illustre ce comportement.  
  
     [!code-vb[VbVbalrStatements#39](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_1.vb)]  
  
     Si vous accédez à des membres de classe par le biais `varAsInterface`, ils ont tous un accès public. Toutefois, si vous accédez aux membres via `varAsClass`, le `Sub` procédure `doSomething` possède un accès privé.  
  
-   **Étendue.** Une interface est dans la portée dans l’ensemble de son espace de noms, de classe, structure ou module.  
  
     L’étendue de chaque membre d’interface est l’ensemble de l’interface.  
  
-   **Durée de vie.** Une interface n’a pas une durée de vie, ni ses membres. Lorsqu’une classe implémente une interface et un objet est créé en tant qu’instance de que classe, l’objet a une durée de vie de l’application dans laquelle il est en cours d’exécution. Pour plus d’informations, consultez « Durée de vie » dans [Class, instruction](../../../visual-basic/language-reference/statements/class-statement.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `Interface` instruction afin de définir une interface nommée `thisInterface`, qui doit être implémenté avec un `Property` instruction et un `Function` instruction.  
  
 [!code-vb[VbVbalrStatements#40](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_2.vb)]  
  
 Notez que la `Property` et `Function` instructions n’introduisent pas de blocs se terminant par `End Property` et `End Function` dans l’interface. L’interface définit uniquement les signatures de ses membres. La version complète `Property` et `Function` blocs s’affichent dans une classe qui implémente `thisInterface`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Module (instruction)](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Types génériques en Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Variance dans les interfaces génériques](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
