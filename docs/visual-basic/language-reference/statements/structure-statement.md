---
title: Structure, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Structure
- Structure
helpviewer_keywords:
- user-defined types [Visual Basic], Structure statement
- compound data types [Visual Basic]
- Structure keyword [Visual Basic]
- Structure statement [Visual Basic]
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 43211bb10793acf3bfe0c1d7a35791114170ee7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="structure-statement"></a>Structure, instruction
Déclare le nom d’une structure et introduit la définition des variables, propriétés, événements et procédures contenus dans la structure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _  
Structure name [ ( Of typelist ) ]  
    [ Implements interfacenames ]  
    [ datamemberdeclarations ]  
    [ methodmemberdeclarations ]  
End Structure  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`attributelist`|Facultatif. Consultez [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Facultatif. Il peut s'agir d'une des valeurs suivantes :<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privé](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Facultatif. Consultez [ombres](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`Partial`|Facultatif. Indique une définition partielle de la structure. Consultez [partielle](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Obligatoire. Nom de cette structure. Consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Facultatif. Spécifie qu’il s’agit d’une structure générique.|  
|`typelist`|Requis si vous utilisez la [de](../../../visual-basic/language-reference/statements/of-clause.md) (mot clé). Liste de paramètres de type pour cette structure. Consultez [tapez liste](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Implements`|Facultatif. Indique que cette structure implémente les membres d’une ou plusieurs interfaces. Consultez [implémente l’instruction](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Requis si vous utilisez la `Implements` instruction. Les noms des interfaces implémentées par cette structure.|  
|`datamemberdeclarations`|Obligatoire. Zéro ou plusieurs `Const`, `Dim`, `Enum`, ou `Event` instructions déclaration *membres de données* de la structure.|  
|`methodmemberdeclarations`|Facultatif. Zéro ou plusieurs déclarations de `Function`, `Operator`, `Property`, ou `Sub` procédures, qui servent de *membres de la méthode* de la structure.|  
|`End Structure`|Obligatoire. Met fin à la `Structure` définition.|  
  
## <a name="remarks"></a>Remarques  
 La `Structure` instruction définit un type valeur composite que vous pouvez personnaliser. A *structure* est une généralisation du type défini par l’utilisateur (UDT) des versions précédentes de Visual Basic. Pour plus d’informations, consultez [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md).  
  
 Structures prennent en charge un grand nombre de ces fonctionnalités en tant que classes. Par exemple, les structures peuvent avoir des propriétés et des procédures, peuvent implémenter des interfaces et ont des constructeurs paramétrés. Toutefois, il existe des différences significatives entre les classes et structures dans des zones telles que l’héritage, les déclarations et d’utilisation. En outre, les classes sont des types référence et les structures sont des types valeur. Pour plus d’informations, consultez [Structures et Classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Vous pouvez utiliser `Structure` uniquement au niveau de l’espace de noms ou module. Cela signifie que la *contexte de déclaration* pour une structure doit être un fichier source, espace de noms, classe, structure, module ou interface et ne peut pas être une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Structures de valeur par défaut [Friend](../../../visual-basic/language-reference/modifiers/friend.md) accès. Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès. Pour plus d’informations, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Règles  
  
-   **Imbrication.** Vous pouvez définir une structure dans une autre. La structure externe est appelée la *contenant une structure*, et la structure interne est appelée un *imbriquée de structure*. Toutefois, vous ne pouvez pas accéder les membres d’une structure imbriquée via la structure contenante. Au lieu de cela, vous devez déclarer une variable de type de données de la structure imbriquée.  
  
-   **Déclaration de membre.** Vous devez déclarer chaque membre d’une structure. Un membre de structure ne peut pas être [protégé](../../../visual-basic/language-reference/modifiers/protected.md) ou `Protected Friend` , car rien ne peut hériter que d’une structure. La structure elle-même, toutefois, peut être `Protected` ou `Protected Friend`.  
  
     Vous pouvez déclarer zéro ou plusieurs variables non partagées ou des événements non personnalisés non partagées dans une structure. Vous ne pouvez avoir uniquement des constantes, des propriétés et des procédures, même si certains d'entre eux sont non partagées.  
  
-   **Initialisation.** Impossible d’initialiser la valeur d’un membre de données non partagée d’une structure dans le cadre de sa déclaration. Vous devez initialiser le membre de données au moyen d’un constructeur paramétrable sur la structure, ou attribuer une valeur au membre après avoir créé une instance de la structure.  
  
-   **Héritage.** Une structure ne peut pas hériter d’un type autre que <xref:System.ValueType>, à partir de laquelle toutes les structures héritent. En particulier, une structure ne peut pas hériter d’une autre.  
  
     Vous ne pouvez pas utiliser le [l’instruction Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md) dans une définition de structure, même pour spécifier <xref:System.ValueType>.  
  
-   **Mise en œuvre.** Si la structure de la [Implements, instruction](../../../visual-basic/language-reference/statements/implements-statement.md), vous devez implémenter chaque membre défini par chaque interface que vous spécifiez dans `interfacenames`.  
  
-   **Propriété par défaut.** Une structure peut spécifier au plus une propriété en tant que son *propriété par défaut*, à l’aide du [par défaut](../../../visual-basic/language-reference/modifiers/default.md) modificateur. Pour plus d’informations, consultez [par défaut](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Comportement  
  
-   **Niveau d’accès.** Dans une structure, vous pouvez déclarer chaque membre avec son propre niveau d’accès. Tous les membres de structure par défaut [Public](../../../visual-basic/language-reference/modifiers/public.md) accès. Notez que si la structure elle-même a un niveau d’accès plus restreint, cela restreint automatiquement l’accès à ses membres, même si vous modifiez leurs niveaux d’accès avec les modificateurs d’accès.  
  
-   **Étendue.** Une structure est dans la portée dans l’ensemble de son espace de noms, classe, structure ou module conteneur.  
  
     La portée de chaque membre de structure est la structure entière.  
  
-   **Durée de vie.** Une structure ne pas lui-même a une durée de vie. Au lieu de cela, chaque instance de cette structure a une durée de vie indépendante de toutes les autres instances.  
  
     La durée de vie d’une instance commence lorsqu’elle est créée par un [nouvel opérateur](../../../visual-basic/language-reference/operators/new-operator.md) clause. Il se termine lorsque la durée de vie de la variable qui contient cette section se termine.  
  
     Vous ne pouvez pas étendre la durée de vie d’une instance de la structure. Une approximation des fonctionnalités de structure statiques est fournie par un module. Pour plus d’informations, consultez [Module, instruction](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Les membres de structure ont des durées de vie selon où et comment ils sont déclarés. Pour plus d’informations, consultez « Durée de vie » dans [Class, instruction](../../../visual-basic/language-reference/statements/class-statement.md).  
  
-   **Qualification.** Le code en dehors d’une structure doit qualifier le nom d’un membre avec le nom de cette structure.  
  
     Si le code à l’intérieur d’une structure imbriquée établit une référence non qualifiée à un élément de programmation, Visual Basic recherche l’élément tout d’abord dans la structure imbriquée, puis dans sa structure conteneur, et ainsi de suite pour l’élément conteneur le plus externe. Pour plus d’informations, consultez [références aux éléments de déclaré](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
-   **Consommation de mémoire.** Comme avec tous les types de données composites, vous ne peut pas calculer en toute sécurité la consommation totale de la mémoire d’une structure en additionnant les allocations de stockage nominal de ses membres. En outre, vous ne pouvez pas supposer que l’ordre de stockage en mémoire est le même que l’ordre de déclaration. Si vous avez besoin contrôler la disposition de stockage d’une structure, vous pouvez appliquer la <xref:System.Runtime.InteropServices.StructLayoutAttribute> d’attribut à la `Structure` instruction.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `Structure` instruction afin de définir un jeu de données associées pour un employé. Il illustre l’utilisation de `Public`, `Friend`, et `Private` membres pour refléter la sensibilité des éléments de données. Il montre également les membres de la procédure, propriété et événement.  
  
 [!code-vb[VbVbalrStatements#57](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/structure-statement_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Module (instruction)](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Const (instruction)](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Enum (instruction)](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Structures et classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
