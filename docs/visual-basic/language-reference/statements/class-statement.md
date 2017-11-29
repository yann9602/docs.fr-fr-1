---
title: Class, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Class
helpviewer_keywords:
- class modules
- Class statement [Visual Basic]
- classes [Visual Basic], fields
- fields [Visual Basic], of classes
- class types [Visual Basic], class statements
- classes [Visual Basic], creating
- classes [Visual Basic], data members
- data members [Visual Basic], of classes
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df86ef0eec67d96f2f997dc5dac7ee2357c6362b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="class-statement-visual-basic"></a>Class, instruction (Visual Basic)
Déclare le nom d’une classe et introduit la définition des variables, propriétés, événements et procédures contenus dans la classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`attributelist`|Facultatif. Consultez [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Facultatif. Il peut s'agir d'une des valeurs suivantes :<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privé](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Facultatif. Consultez [ombres](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Facultatif. Consultez [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Facultatif. Consultez [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|Facultatif. Indique une définition partielle de la classe. Consultez [partielle](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Obligatoire. Nom de cette classe. Consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Facultatif. Spécifie qu’il s’agit d’une classe générique.|  
|`typelist`|Requis si vous utilisez la [de](../../../visual-basic/language-reference/statements/of-clause.md) (mot clé). Liste des paramètres de type pour cette classe. Consultez [tapez liste](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Facultatif. Indique que cette classe hérite des membres d’une autre classe. Consultez [Inherits, instruction](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Requis si vous utilisez la `Inherits` instruction. Le nom de la classe à partir de laquelle cette classe dérive.|  
|`Implements`|Facultatif. Indique que cette classe implémente les membres d’une ou plusieurs interfaces. Consultez [implémente l’instruction](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Requis si vous utilisez la `Implements` instruction. Les noms des interfaces implémentées par cette classe.|  
|`statements`|Facultatif. Instructions qui définissent les membres de cette classe.|  
|`End Class`|Obligatoire. Met fin à la `Class` définition.|  
  
## <a name="remarks"></a>Remarques  
 A `Class` instruction définit un type de données. A *classe* est un bloc de construction fondamental de la programmation orientée objet (OOP). Pour plus d’informations, consultez [objets et Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 Vous pouvez utiliser `Class` uniquement au niveau de l’espace de noms ou module. Cela signifie que la *contexte de déclaration* pour une classe doit être un fichier source, espace de noms, classe, structure, module ou interface et ne peut pas être une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Chaque instance d’une classe a une durée de vie indépendante de toutes les autres instances. Cette durée de vie commence lorsqu’elle est créée par un [nouvel opérateur](../../../visual-basic/language-reference/operators/new-operator.md) clause ou par une fonction telle que <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>. Il se termine lorsque toutes les variables pointant vers l’instance ont été définies [rien](../../../visual-basic/language-reference/nothing.md) ou les instances d’autres classes.  
  
 La valeur par défaut pour des classes [Friend](../../../visual-basic/language-reference/modifiers/friend.md) accès. Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès. Pour plus d’informations, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Règles  
  
-   **Imbrication.** Vous pouvez définir une classe dans une autre. La classe externe est appelée la *contenant la classe*, et la classe interne est appelée un *classe imbriquée*.  
  
-   **Héritage.** Si la classe utilise le [l’instruction Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md), vous pouvez spécifier qu’une seule classe de base ou interface. Une classe ne peut pas hériter de plusieurs éléments.  
  
     Une classe ne peut pas hériter d’une autre classe avec un niveau d’accès plus restrictif. Par exemple, un `Public` classe ne peut pas hériter d’un `Friend` classe.  
  
     Une classe ne peut pas hériter d’une classe imbriquée.  
  
-   **Mise en œuvre.** Si la classe utilise le [Implements, instruction](../../../visual-basic/language-reference/statements/implements-statement.md), vous devez implémenter chaque membre défini par chaque interface que vous spécifiez dans `interfacenames`. Une exception à cette règle est la nouvelle implémentation d’un membre de classe de base. Pour plus d’informations, consultez « Nouvelle implémentation » dans [implémente](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
-   **Propriété par défaut.** Une classe peut spécifier qu’une propriété en tant que son *propriété par défaut*. Pour plus d’informations, consultez [par défaut](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Comportement  
  
-   **Niveau d’accès.** Dans une classe, vous pouvez déclarer chaque membre avec son propre niveau d’accès. Membres de classe par défaut [Public](../../../visual-basic/language-reference/modifiers/public.md) accéder, à l’exception des variables et des constantes, qui par défaut à [privé](../../../visual-basic/language-reference/modifiers/private.md) accès. Lorsqu’une classe a plus restreint l’accès à un de ses membres, le niveau d’accès de la classe est prioritaire.  
  
-   **Étendue.** Une classe est dans la portée dans l’ensemble de son espace de noms, classe, structure ou module conteneur.  
  
     L’étendue de chaque membre de classe est la classe entière.  
  
     **Durée de vie.** Visual Basic ne prend pas en charge les classes static. L’équivalent d’une classe statique est fourni par un module. Pour plus d’informations, consultez [Module, instruction](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Membres de classe ont des durées de vie selon où et comment ils sont déclarés. Pour plus d’informations, consultez [durée de vie dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   **Qualification.** Le code en dehors d’une classe doit qualifier le nom d’un membre avec le nom de cette classe.  
  
     Si le code à l’intérieur d’une classe imbriquée établit une référence non qualifiée à un élément de programmation, Visual Basic recherche l’élément tout d’abord dans la classe imbriquée, puis dans sa classe conteneur, et ainsi de suite pour l’élément conteneur le plus externe.  
  
## <a name="classes-and-modules"></a>Classes et les Modules  
 Ces éléments ont de nombreuses similitudes, mais il existe certaines différences importantes ainsi.  
  
-   **Terminologie.** Les versions précédentes de Visual Basic reconnaissent deux types de modules : *modules de classe* (fichiers .cls) et *modules standard* (fichiers .bas). La version actuelle appelle ces *classes* et *modules*, respectivement.  
  
-   **Membres partagés.** Vous pouvez contrôler si un membre d’une classe est une connexion partagée ou un membre d’instance.  
  
-   **Orientation de l’objet.** Les classes sont orientés objet, mais les modules ne sont pas. Vous pouvez créer une ou plusieurs instances d’une classe. Pour plus d’informations, consultez [objets et Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un `Class` instruction afin de définir une classe et plusieurs membres.  
  
 [!code-vb[VbVbalrStatements#62](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/class-statement_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Structures et classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Module (instruction)](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Durée de vie d’un objet : création et destruction des objets](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Types génériques en Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Guide pratique : utiliser une classe générique](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
