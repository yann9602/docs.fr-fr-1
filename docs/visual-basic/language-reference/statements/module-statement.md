---
title: Module, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 92cdcd1919f21243118108da3bc382ea5d954130
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="module-statement"></a>Module, instruction
Déclare le nom d’un module et introduit la définition des variables, propriétés, événements et procédures contenus dans le module.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a>Composants  
 `attributelist`  
 Facultatif. Consultez [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Facultatif. Il peut s'agir d'une des valeurs suivantes :  
  
-   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 Consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `name`  
 Obligatoire. Nom de ce module. Consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `statements`  
 Facultatif. Instructions qui définissent des variables, des propriétés, des événements, des procédures et des types imbriqués de ce module.  
  
 `End Module`  
 Met fin à la `Module` définition.  
  
## <a name="remarks"></a>Remarques  
 A `Module` instruction définit un type de référence disponible tout au long de son espace de noms. A *module* (parfois appelé un *module standard*) est semblable à une classe, mais avec certaines des différences importantes. Chaque module a exactement une seule instance et ne doit-elle pas être créé ou assigné à une variable. Les modules ne prennent en charge l’héritage ou implémenter des interfaces. Notez qu’un module n’est pas un *type* dans le sens où une classe ou une structure, vous ne pouvez pas déclarer un élément de programmation comme ayant le type de données d’un module.  
  
 Vous pouvez utiliser `Module` uniquement au niveau de l’espace de noms. Cela signifie que la *contexte de déclaration* pour un module doit être un fichier source ou un espace de noms et qu’il ne peut pas être une classe, structure, module, interface, procédure ou bloc. Vous ne pouvez pas imbriquer un module dans un autre module, ou dans n’importe quel type. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Un module a la même durée de vie que votre programme. Étant donné que ses membres sont tous les `Shared`, ils ont également des durées de vie égales à celle du programme.  
  
 Par défaut des modules à [Friend](../../../visual-basic/language-reference/modifiers/friend.md) accès. Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès. Pour plus d’informations, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Tous les membres d’un module sont implicitement `Shared`.  
  
## <a name="classes-and-modules"></a>Classes et les Modules  
 Ces éléments ont de nombreuses similitudes, mais il existe certaines différences importantes ainsi.  
  
-   **Terminologie.** Les versions précédentes de Visual Basic reconnaissent deux types de modules : *modules de classe* (fichiers .cls) et *modules standard* (fichiers .bas). La version actuelle appelle ces *classes* et *modules*, respectivement.  
  
-   **Membres partagés.** Vous pouvez contrôler si un membre d’une classe est une connexion partagée ou un membre d’instance.  
  
-   **Orientation de l’objet.** Les classes sont orientés objet, mais les modules ne sont pas. Par conséquent, seules les classes peuvent être instanciés en tant qu’objets. Pour plus d’informations, consultez [objets et Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="rules"></a>Règles  
  
-   **Modificateurs.** Tous les membres de module sont implicitement [partagé](../../../visual-basic/language-reference/modifiers/shared.md). Vous ne pouvez pas utiliser le `Shared` mot clé lors de la déclaration d’un membre et vous ne pouvez pas modifier l’état partagé d’un membre.  
  
-   **Héritage.** Un module ne peut pas hériter d’un type autre que <xref:System.Object>, à partir de quels tous les modules hériter. En particulier, un module ne peut pas hériter d’une autre.  
  
     Vous ne pouvez pas utiliser le [l’instruction Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md) dans une définition de module, même pour spécifier <xref:System.Object>.  
  
-   **Propriété par défaut.** Vous ne pouvez pas définir les propriétés par défaut dans un module. Pour plus d’informations, consultez [par défaut](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Comportement  
  
-   **Niveau d’accès.** Dans un module, vous pouvez déclarer chaque membre avec son propre niveau d’accès. Membres de module par défaut [Public](../../../visual-basic/language-reference/modifiers/public.md) accéder, à l’exception des variables et des constantes, qui par défaut à [privé](../../../visual-basic/language-reference/modifiers/private.md) accès. Lorsqu’un module a plus restreint l’accès à un de ses membres, le niveau d’accès de module spécifié est prioritaire.  
  
-   **Étendue.** Un module est dans la portée dans l’ensemble de son espace de noms.  
  
     La portée de chaque membre de module est l’ensemble du module. Notez que tous les membres subissent *promotion de type*, ce qui entraîne leur étendue de promotion à l’espace de noms contenant le module. Pour plus d’informations, consultez [Promotion de Type](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
-   **Qualification.** Vous pouvez avoir plusieurs modules dans un projet, et vous pouvez déclarer des membres portant le même nom dans deux ou plusieurs modules. Toutefois, vous devez qualifier toute référence à ce membre avec le nom de module approprié si la référence est en dehors du module. Pour plus d’informations, consultez [références aux éléments de déclaré](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Namespace (instruction)](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Promotion de type](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
